# 2024-04-01: CVE-2024-0204 in Fortra's GoAnywhere MFT

Unpacking in more detail: see pdf

CVE-2024-0204 is like a key under the mat that has not been authenticated and wants to create its own administrator user. This vulnerability can be exploited remotely and is a classic example of CWE-425: "Forced access when a web application is simply too polite to provide proper authorization." Vulnerable versions 6.x starting from 6.0.1 and version 7.x up to 7.4.1, in which they decided to hang a lock on the door. If you're feeling DIY, the advisory suggests a workaround: delete the endpoint /InitialAccountSetup.xhtml and restart the service. For those fancy container-deployed instances, just replace the file with an empty one and give it a good ol' reboot.

Now, let's talk about GoAnywhere MFT itself. It's a secure software solution that's supposed to streamline data exchange and improve security, which is kind of hilarious given the circumstances. It's like having a state-of-the-art vault with the door wide open. It can be deployed on-premises, in the cloud, or in hybrid environments and supports a plethora of operating systems and protocols.

CVE-2024-0204, a vulnerability in Fortra's GoAnywhere MFT, is practically a VIP pass for unauthenticated attackers. Why bother with the hassle of hacking when you can just create your own admin account, right? It's like the system is saying, "Please, come in, make yourself at home, and while you're at it, feel free to take control of everything." 

The impacts of this vulnerability are like a greatest hits album of cybersecurity nightmares:
 * **Creation of Unauthorized Admin Users**: Because why wouldn't we want random strangers to have the keys to the kingdom?
 * **Potential for Data Breach**: It's like leaving your diary open in a crowded cafe and being surprised when someone reads it.
 * **Malware Deployment**: Who needs traditional malware distribution methods when you can just drop your ransomware directly into the system like it's hot?
 * **Complete System Takeover**: It's not just a visit; it's a full-blown takeover. Why rent when you can own?
 * **Risk of Extortion**: With access this easy, why not throw in a little blackmail? It's the cherry on top of the cybersecurity disaster sundae.
 * **Operational Disruption**: Because who doesn't love a little chaos in their day-to-day operations?
 * **Compliance and Legal Issues**: Nothing spices up the boardroom like a good old-fashioned compliance scandal and the potential for legal drama.

The bar for "attack complexity" is set so low, even a toddler could trip over it. We're talking about the kind of simplicity that makes you wonder if "security" is just a fancy word they throw around to sound important.

Attack Flow
So, here's the blockbuster attack flow for this authentication bypass extravaganza:
 * **Initial Access**: Our intrepid attacker, armed with the digital equivalent of a plastic spork, strolls into the GoAnywhere MFT administration portal without so much as a by-your-leave. Thanks to the path traversal issue, it's less "breaking and entering" and more "please enter and make yourself at home."
 * **Exploitation**: Next, our villain exploits the path traversal issue, which is basically like finding a secret passage in a Scooby-Doo episode, leading straight to the /InitialAccountSetup.xhtml endpoint. No meddling kids in sight to stop them, unfortunately.
 * **Creation of Admin User**: Once they've tiptoed through the secret passage, they can create an admin user. This isn't just any user, mind you; it's the kind with all the bells and whistles—read, write, command execution. It's like giving a burglar the keys to the safe, the alarm codes, and a nice cup of tea.
 * **Potential Further Exploitation**: With the keys to the kingdom, our attacker can now do all the fun stuff: access sensitive data, deploy malware, or just take complete control because, why not? It's a free-for-all!

In short, CVE-2024-0204 is the gift that keeps on giving—if you're an attacker, that is. For the rest of us, it's a facepalm-worthy reminder that maybe, just maybe, we should take this whole "security" thing a bit more seriously.
