---
title: "Windows 7 install disk"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by jackheart on 2010-08-04
Sorry if this is not the right place for this. This is more of a windows 7 question, but I want to do dual boot W7 and Ubuntu Studio. Just got my brand new laptop and they dont come with a manufacture disk anymore. There was a pop up telling me how to make a manufacture default disk (or something of that flavor), but I dont see it anymore and I dont know how to get to it. I did make a repair disk, and I can make a backup....but that is just a copy of my files right? How do I make a Windows 7 64 bit disk that I can reinstall after I make my partitions with Gparted. Or do I have to use partition magic and create partitions with W7 still on it? Again, sorry this is not a ubuntu Question, but I would love to do dual boot. Thanks!

PS, I know it seems silly that I cant figure out a seemingly simple thing in Windows, and I want to use Ubuntu, but I do have some experience. I recently put purdyne on an old thinkpad so I definitely have some experience with Linux and its quarks.

---

### Post by brokenromeo on 2010-08-04
When you make a system restore disk from windows on your laptop, that typically is the option to recreate your laptop as it shipped from the factory...make those and those also contain your OS. Boot into windows and go to the disk manager, and there you can shrink your windows partition, reboot after that just to make sure you are ok. Then you can boot from the Ubuntu install disk or usb drive and install using the dual boot option, your computer will then boot to the grub menu where you can select which OS you want to boot into.

---

### Post by jackheart on 2010-08-04
is a system repair disk (the one I made) the same as system restore? I am still a little confused Sorry.

---

### Post by brokenromeo on 2010-08-04
It should be if you made it correctly...you could try booting from it...

---

### Post by jackheart on 2010-08-04
Well I finally found it actually. I knew something was not right because the repair disk was only 1gig on the DVD, that is why I was apprehensive. The repair disk has the drivers and other system files, but not Win7 or the full Acer (my comp) suite. There was a program called Acer eRecovery that lets you make a factory default disk. It took 3 DVD's thanks for the help though.

---

