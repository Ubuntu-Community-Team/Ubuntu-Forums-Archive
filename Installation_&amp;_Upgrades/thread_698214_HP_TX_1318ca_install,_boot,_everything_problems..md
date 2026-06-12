---
title: "HP TX 1318ca install, boot, everything problems."
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by GhostCyber on 2008-02-16
I just got this new laptop...
I love it...Normaly i would have bought a sony, but i am glad this time i bought an hp...

My History,
I am familur with linux, but this is my first ubuntu install. I untill now, have been with SuSe. I want to be Ubuntu, hopefully this will work out.

My problems, :confused:
It took me quite a bit of time, trying differant install cd's and finally i got ubunto 7.10 installed, Type x64 ... using the Ubuntu DVD.

It now wont go past either boot option, this first... (i don't know how to do a verbose with ubuntu) goes to the 4th box, and stops...

the second boot option, (Wich is verbose) goes to Loading hardware drivers..

they then both freeze.

i got it to boot once, out of fluke i guess, tried to update, hoping that would solve the problem, rebooted, then same thing.

Boot options are:

root (hd0,2)
kernal /boot/vmlinuz-2.6.22-14-generic root=UUID=e027439a-fef0-4bf0-9146-233c4aeff8ac ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

root (hd0,2)
kernal /boot/vmlinuz-2.6.22-14-generic root=UUID=e027439a-fef0-4bf0-9146-233c4aeff8ac ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet


hardware of the laptop is :
AMD Turian 64x2
Nvidia 6150
2gigs ram.

If any further info is needed, let me know...
I have spent hours at this problem...Really hope someone can help.

---

### Post by GhostCyber on 2008-02-16
k, so, upon further review, i fixed it.
'doscsi noapic nopcmcia' 
goes in the first statement...

root (hd0,2)
kernal /boot/vmlinuz-2.6.22-14-generic root=UUID=e027439a-fef0-4bf0-9146-233c4aeff8ac ro doscsi noapic nopcmcia quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

it now works, ty fer all yer help... now on to getting the touch pscreen working.

---

