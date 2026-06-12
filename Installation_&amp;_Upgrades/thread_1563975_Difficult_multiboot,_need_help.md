---
title: "Difficult multiboot, need help"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by bacterialbag on 2010-08-29
Dear Ubuntu users,

I need help setting up my lenovo Y460 in multiboot. I've tried several times myself, but I cant seem to install the 4 OS's that i want. I keep failing and failing. That's why i came here, because you guys have helped me very good before!!


This is my setup;

Lenovo Y460 (Intel I5, 4gb, 1gb Video ram. 500gb HDD and 120 gb SSD )

What I want:

Quad boot; Xp, 7(64bit), Backtrack 4 (based on ubuntu8. ), KUbuntu 10.10 (64bit)

I want the windows 7 to be installed on the SSD, (for maximum speed in windows, it will be my primary OS.

I want Xp, BT4 and Ubuntu installed on the HDD,

and I want to be able to choose between the 4 OS's, using my bootloader.

Dos anyone has experience with this kind of multibooting? is it possible to boot from multiple HDD's?

if so;
How should I partition my drives? which one should be logical, primary etc?
In what order should I install the Os's? 
Where should I install the bootsectors?

Please inform me with your relevant information about multiboot, I'm eager to learn!

Thanks!

Bacterialbag
( P.s. sorry for the bad English, third language )

---

### Post by bacterialbag on 2010-08-30
My strategy was first installing XP to the HDD, then Windows 7 64 to the SSD, after that I would install Backtrack 4 (ubuntu 8 based) on my HDD, and then install Ubuntu 10.10. 
 
Do you guys think this will work? Is there something i forgot? 
 
Also, what drive should be the primary and what drive should be the logical drive in this scenario?
 
Any relevant info or links to this subject are welcome!
 
Thanks
 
Bacterialbag
 
P.s. (Is it possible to also install Snow Leopard with this setup? or will that task be too much frustration, to be worth the try?
 
sorry for the bad English, third language.

---

### Post by oldfred on 2010-08-30
Windows has issues with two installs. It will want to combine the boots so it can boot either one, but in doing so it moves the boot files from the second install to the first. You need to insure they are separate if you want to directly boot from grub2.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

If backtrack is Ubuntu 8.04 it uses old grub 0.97. You can install that version of grub to the partition boot sector (PBR) and chainload to it, just like grub chainloads to the windows boot sectors.

Some software in win7 causes boot issues with grub2. With multiple drives I normally suggest windows boot on one drive and grub2 on the other (with Ubuntu) and boot the grub/Ubuntu drive. With your SSD you may want to review what software has caused issues (Dell, HP tools and some adobe). I would still keep grub2 installed to the MBR of the 500GB drive, but not sure how much boot time you lose booting that and then choosing windows vs. having grub2 in the SSD and booting from it. You can easily install/reinstall boot loaders to test.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

With multiple operating systems you should keep system partitons small (with windows it is more difficult) and keep separate /home and/or /data partition(s). I have both a shared NTFS partition for any data I may want in my XP but now use XP so little that most of my data is in a /data partition that is ext3 but windows cannot see it. I like having the same firefox profiles in all my systems. Since I have all data elsewhere my Ubuntu partitions are all 20-25GB with only about 6GB used.

---

