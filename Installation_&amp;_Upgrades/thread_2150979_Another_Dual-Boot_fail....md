---
title: "Another Dual-Boot fail..."
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by jonathonemilio on 2013-06-03
I'm running on an HP Envy 4t-1100 touchsmart with an Intel i5 and on Windows 8 64bit. So I'm new to this forums site, and am, for the most part, new to Ubuntu (have played around with it in the past) but recently realized the convenience of using Linux for what I have to do for school. As such, I downloaded Ubuntu 12.04, loaded it as a live USB, tried it out, liked it, and tried dual booting to my laptop. Well, that didn't fare too well for me... when I finished installing Ubuntu, I realized that I was able to load Windows, but when I tried to run Ubuntu, it would tell me that I didn't have it installed in the hard drive. 

So I checked around, and after a bit, found that Boot-Repair in Ubuntu (run off the live USB) would fix the problem. When I tried that, it disabled (or overwrote) the normal Windows bootloader and replaced it with Grub, and I couldn't load Windows. Let me make note that I can't run Windows AT ALL... Command Line, safe mode, nothing. I can install Ubuntu and have it run, and while installing Ubuntu, it sees Windows 8, but Windows will not run on the machine. Right before dual booting, I did a backup of Windows, and tried to run the backup to recover Windows, not really caring for Ubuntu, but it didn't work. 

So I used the manufacturer's USB Factory Recover disk to completely recover the machine and automatically repartition the hard drive to what it wants, and that wouldn't work. I've tried using GParted to repartition the hard drive manually, re-running Boot-Repair to fix the Windows boot, recovering Windows and running GParted to change the flags around, and even cloning my hard drive to another and running repairs. 

Nothing seems to work for me! Any help would be HIGHLY appreciated at this point... I also took the liberty of doing a boot summary of my machine, found at [http://paste.ubuntu.com/5728155/](http://paste.ubuntu.com/5728155/) if that helps any... I would like to have Windows 8 and Ubuntu run together, but at this point, all I really want back is Windows 8...

---

### Post by jonathonemilio on 2013-06-03
Let me also point out that my original hard drive was a 500gig hybrid drive, and the one I'm on now is a terabyte hybrid drive...

---

### Post by Bucky Ball on 2013-06-03
*Thread moved to **Installation & Upgrades**.*

Welcome to the forum. I have edited your post to include paragraphs and increase your chances of getting help. Please refrain from the 'black blob' post as they will decrease your chances of getting help. ;)

Hmm. Quite a mess. I think the problem occurred when you installed Ubuntu and got the message it wasn't installed. At that point, neither was grub and your machine was as was, still booting Windows fine. Then you installed grub with Boot Repair without a Ubuntu install actually on the machine, in effect changing the boot from the Win loader to Grub. My advice:

Boot from the LiveCD, open Gparted. What is the current condition of your drive? Partitions, is Win still there (NTFS partition), is Ubuntu there (EXT* partition)?

Report back. If Win is still there, start hunting for how to restore its bootloader (you can do that with the options on the Win disk, repair install, but you'll need to research that) and delete grub. 

If Win not there, boot from the LiveCD, open Gparted. What is the current condition of your drive? What partitions are on there? Nothing you want to save delete all partitions leaving free space. Close and reboot to your regular Win recovery disk, create partition and install Win leaving the rest free space.

If Win is not there and neither is Ubuntu you may get more joy on a Windows forum figuring how to get it back on.

... but by the sounds Win could still be there so all is not lost. Just remember, doesn't sound like you have an install of Ubuntu, that failed, but you have installed grub with Boot Repair so that would appear to be your issue. Win should still be there and nothing has changed except the boot sector.

---

### Post by ubfan1 on 2013-06-03
Maybe running boot-repair and restoring the backup files would do it.  Normally, the regular Windows bootloaders get renamed with a "bkp" in the name, and replaced with a copy of shim -- all to get to grub.  But that leaves only oddly named Windows bootloaders around, so even the efi menu probably points to the original name, which is now a copy of shim.

---

