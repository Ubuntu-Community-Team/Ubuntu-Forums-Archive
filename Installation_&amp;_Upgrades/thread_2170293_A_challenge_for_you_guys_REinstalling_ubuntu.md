---
title: "A challenge for you guys RE:installing ubuntu"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by mrgreaper on 2013-08-25
ok so here i sit at work with a laptop that has windows 8 pre-installed and is stuttering a lot more then it should. i can do the reinstall windows with the restore and i lose all my files and installed programs...so i was thinking hmmm ubuntu is free and can install alongside windows..ah ha!

so i downloaded it 13.04-desktop.iso, mounted it and ran wubi ....it told me to leave the cd in the drive and reboot...ah hmmm thats a bit of a problem...
so thinking on my feet i looked at my andriod phone and thought oooo lets use that as a flash drive...only it seems my phone only has two usb modes..camera (ptp) and media (mtp)

so heres the challenge i have 3 and a half hours till i go home, at home i will be just as worse off (no flash drives no blank cds) and i want to try and get ubuntu installed alongside windows 8 before then, any ideas how we can do it

Resources available:
laptop with 1tb hd
samsung galaxy s4 rooted and on andriod 4.3
ubuntu iso 13.04 64bit
internet with slow speed (took an hour to get the unbuntu disc) but unlimited data (thank you one plan!) 

queue mission impossible music

---

### Post by qamelian on 2013-08-25
I'm afraid you're out of luck, if you want to use WUBI. WUBI doesn't work with that release of Ubuntu, plus it doesn't work with Windows 8.
[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

---

### Post by Boab1993 on 2013-08-25
Hi MrGreaper,

As for WUBI, @qamelian is right, WUBI is being discontinued due to the  exact reason you cant use it UEFI. So it is being phased out.
Just  for trivia, this is not strictly true for no UEFI systems e.g. Xp/Win7  you can still use WUBI to install an older version of Ubuntu and upgrade  with the update manager.

For installation along side windows 8, you need disable fastboot and possibley secure boot.
You do this your BIOS system in windows 8, its accessed via an '[a key] for BIOS' at your splash screen at the begining of your startup.
There is official ubuntu documentation on this but since you dont want links, i will not give you them.

Secondly you need to shrink your current partition. Im rusty on windows tools and i have never used windows 8 (i dislike it alot) but this is done under adminstation tools, in there, there will be an option to manage disks or similar, there should be two items, one a list of your current drives, two a graphical representation of your disk space and partitions on it. Right click the windows 8 partition on the graph and go down to shrink partition. You will be prompted to select a size to shrink to. If you cant shrink the partition, defragment your disk and try again, you cannot shrink any part of disk with data on it, thus making the data contigious allows for a larger area to be shrunk.

As for what to use to install ubuntu, it is not advisable to use your phone as your live CD installer. Generally you need to reformat any device before using it as a USB installer, im pretty sure you cant do that with android, and if you can, you'd be without a phone. Could be wrong.

---

### Post by ian-weisser on 2013-08-25
> **mrgreaper said:**
> ok so here i sit at work with a laptop that has windows 8 pre-installed and is stuttering a lot more then it should. [...]

Stuttering? Do you mean the hard drive is making noise?
Ubuntu will not fix a dying hard drive or other hardware problems.

---

### Post by Bucky Ball on 2013-08-26
*Thread moved to **Installation & Upgrades**.*

Unsure as to why this was posted in ABS. Severly limits your chances of getting help with this. Please post in appropriate sub-forum. You will increase your chances of assistance.

---

### Post by coldraven on 2013-08-26
Installing an second OS, although it has become easy, is not a trivial matter. Things can go wrong and you could lose your data.
So before doing anything you should always **backup your files**.

---

