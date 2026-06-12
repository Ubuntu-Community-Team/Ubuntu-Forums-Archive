---
title: "Complicated Upgrade Question: Ubuntu Quantal from Debian Squeeze"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by moore.bryan on 2012-09-01
Hey gang... Debian stable is great on my old G4 FlowerPot iMac, but I run into some issues when having to install newer programs--you know, of the "unmet dependencies" variety--and, as such, I live in an almost constant almost-broken-system world. Basically, I'd like to give Quantal a test-drive on this old machine, since it's great on my Asus netbook. Now, here are the catches: there's no way to make a boot usb for this Mac, I've tried. A million times. Well, maybe not *literally* one million, but you catch my drift. Also, the disc reader in it is shot, so... 

Can I just alter the sources.list to reflect Ubuntu and dist-upgrade?

After some reading, I found many sites answering my question "no" and suggesting a hard disk install. I read up on that and decided it was the way to go. The official Ubuntu installation documentation had me put files on the HFS+ partition and install through OpenFirmware. I did that, rebooted into OF, and ran the associated commands; I received the dreaded "Can't read Elf e_ident/e_type/e_machine info" error, which was supposedly solved after Hoary. No sweat, I thought, I'll just reboot back into my Debian install and set things straight. Funny thing, the computer now boots directly into the installation bootable drive and won't let me boot into my install. Halp?

---

