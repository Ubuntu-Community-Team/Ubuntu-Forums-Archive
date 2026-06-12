---
title: "cannot boot windows XP"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by jensvanhoof on 2008-10-20
Hi Everybody,

I realize that this question comes up a lot, however, even after reading multiple threads I still cannot figure out my problem.

I'll start with the beginning:

I bought a new Fujitsu-Siemens laptop a few months ago. It came with Windows Vista installed. I descided I didn't want to use vista, so I downgraded the system to windows XP. All this worked fine. I should also mention that there are 2 hard disks in the laptop, who work together in a RAID configuration. When I was still using windows XP there where 3 partitions: SYSTEM, DATA and SYSTEM_DATA.

Last week I wanted to try Ubuntu 8.04. I downloaded the .ISO file, put it on a CD and installed it on my computer. I don't know exactly on what partition it was installed, but I think that I installed it correctly, next to windows XP. Unbuntu boots great, and in it's file explorer, I can still see all my windows files, so I'm prety sure that everything's still there.

Now, when I boot my computer, and want to load XP again (for some essential programs I need), this seems impossible. The ubuntu bootloader (GRUB, I think..) pops up and I can choose for Ubuntu, and under 'Other Operating Systems' I see 2 times 'Windows Vista Recovery', and nothing about Windows XP. When I try to boot the vista recovery, a recovery program from Fujitsu-Siemens loads, like it still thinks that Vista was the Microsoft OS that I was using.

When I take a look at the original boot.ini file it displays this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.0
[Operating System]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.0="Microsoft Windows XP Home Edition"

When I do sudo gedit/boot/grub/menu.lst it displays this:

#This is a divider, added to separate the menu itmes below from the Debian
#ones
title         Other Operating systems:
root

#This entry automatically added by the Debian installer for a non-Linux OS
#on /dev/sda1
title        Windows Vista/Longhorn (loader)
root         (hd0,0)
savedefault
makeactive
chainloader   +1

Similar like in boot.ini where 'partition' was set to 2, I changed in menu.lost root to (hd0,2).

When I do this and try to boot, it displays 'BOOTMGR is missing', which seems to be a VISTA file (again). The file is however present in the system directory which also contains boot.ini

When you pay close attention to boot.ini, you see that it points to another folder, called windows.0, which does not have the file BOOTMGR, I tried to copy it and change menu.lst to:

#This entry automatically added by the Debian installer for a non-Linux OS
#on /dev/sda1
title        Windows Vista/Longhorn (loader)
root         (hd0,0)/WINDOWS.0
savedefault
makeactive
chainloader   +1

but also this didn't work. I'm running out of options. Any help is greatly appreciated.

Thanks!!
Jens

---

### Post by caljohnsmith on 2008-10-20
How about first posting:
```
sudo fdisk -lu
```
So we can get a better idea of your setup. :)

---

### Post by jensvanhoof on 2008-10-23
For now, I just installed windows XP back on top. Seems I've got 2 windows XP's now.. sigh. I backupped all my files now, going to play with fdisk or something now. I'll keep you updated. Thanks for the interest though!

thx!
jens

---

