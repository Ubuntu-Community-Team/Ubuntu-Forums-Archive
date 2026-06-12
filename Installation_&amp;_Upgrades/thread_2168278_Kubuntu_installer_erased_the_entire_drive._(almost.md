---
title: "Kubuntu installer erased the entire drive. (almost) no question asked."
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by r.darwish on 2013-08-17
After several years with other Linux distributions I decided to re-try Kubuntu and install it on my laptop.
The laptop had a Gentoo system on LVM and Windows install. I was planning to switch the Gentoo with Ubuntu but wanted to keep my home directory.
When I got to the partition manager in the installer I first choose "manual", but the installer didn't seem to recognize my LVM volume group (It just showed the physical volume).
The three remaining options were:
Guided - Use the entire disk
Guided - Use the entire disk (LVM)
Guided - Use the entire disk (LVM + Encryption)

Usually Linux installers suggest a "Delete all Linux partitions" so they at least keep the Windows installation, but there was no such option.
"Use the entire disk" didn't seem like the right option but since it's supposed to be "Guided" I thought I'll get the chance to review the changes that are to be made, and even if I won't, I'll at least see a confirmation message that says "I'm about to erase your entire disk", as most Linux installers have.

No, there wasn't... The next click started the installation immediately without any questions asked. There goes off my Windows installation... There goes off my previous home directory... not a single "Are you sure?" question was asked.

This is a very bad first impression...

Of course I'm not looking for any solution since I probably just lost everything that was on my laptop. What I'm asking is what is the reason behind this? I really don't think removing the dual support from the distribution will make it more popular, and I don't think that an installer that asks almost no question before erasing your entire machine is more user friendly.

---

