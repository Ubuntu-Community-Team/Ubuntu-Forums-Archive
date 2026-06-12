---
title: "Grub error when there is only one partition of vista on the computer."
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by MightyRushpal on 2011-01-16
Okay i am going to try and explain this problem as best as i can. I am about to throw my computer out the window and never use it again. 

I am running vista 64x and i partitioned unbuntu 10.10 on my computer.

I deleted the ubuntu partitioned from my computer through Vista and made it all one drive. SO now all my computer has i the recovery partition which is 9.61GB and the main Vista partition that is 287.65GB. That is ALL.

I restarted my computer and it gives me the following error:

[I]error: no such partition
grub rescue>[/I]

I know you have answered millions of questions about that error, however the problem i have i cant find a solution for anywhere. 

Now, i have a GParted disk to manage my paritions because i have had this problem before. However when i put it in the computer it only shows my 2 partitions. (The recovery one and the vista one) Both of them are "unmounted"

How do i disable grub from loading through something like GParted that is boot loaded off a disk at system startup? I only have vista on this computer, but i cant get to it because GRUB is in the way. (I do not know if its grub1 or grub 2, but its ubuntu 10.10)

I DO NOT have a recovery disk for my vista computer, ive lost it, however i have the Windows 7 Upgrade disk, but that will not load from the disk when i turn on the computer.

I have absolutely NO IDEA how to fix this problem!

---

### Post by wilee-nilee on 2011-01-16
So you will have to be able to boot a recovery disc the W7 one will work, but here is the vista one.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Then follow this set of instructions. Notice the W7 forums link for a visual of the instructions.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If you can boot a Ubuntu disc, and the hd is sda you can load lilo with these two commands. If your HD is sdb or something else look in gparted to tell change the sda to the correct one.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

So it may be that you can't boot the windows disc, because you need to use a per-session keyprompt at powering on to get to the out of the bios boot from menu.

---

