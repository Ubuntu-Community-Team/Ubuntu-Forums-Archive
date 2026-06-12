---
title: "Grub was installed to wrong hard drive"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Jordanwb on 2008-05-01
In my computer I have three hard drives with the following partitions:

320 GB SATA Hard Drive (referred to as sdb)
---> ~20 GB Partion NTFS For Windows XP
---> ~275GB For Ubuntu 8.04
---> ~4 GB for Linux Swap
250 GB PATA Hard drive (referred to as hd0)
---> 232 GB NTFS for archiving
160 GB SATA Hard Drive (referred to as sda)
---> 150 GB NTFS for Gaming in XP

Now in the Ubuntu Alternate installer it installed Grub to hd0 instead of sdb. The problem is that my computer looks to the SATA hard drive before the PATA (which hd0 is). I have Super Grub Disk but as Adam Savage once said "I don't know what to do."

How do I install grub to the correct drive and remove the one on hd0? I have access to a knoppix boot disk as well if needed.

[Edit] I selected "SGB with Help" or something like that and now I can't boot into Windows XP or Ubuntu, so is the "Fail Boat" picture required or did I screw up? The later is more likely. I made a backup before I installed Ubuntu, so I'm restoring that then I'm going to reinstall Ubuntu. Then I'll be in the same boat (hopefully not the fail boat).

---

### Post by El King on 2008-05-01
you can recover ur MBR to access XP by using a bootable XP cd and getting into the recovery console, then typing **fixboot** and **fixmbr**

if u wanted to restore GRUB u can use this helpful guide
**[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)**

---

### Post by Jordanwb on 2008-05-01
Well as I said I made a backup of XP (a clean installation of XP) with Acronus so it made a backup of the MBR has well(which it restored). I'm currently at the stage of installing Ubuntu, I haven't gotten to grub yet.

[Edit][Restarts Laptop after Firefox completely crashes Ubuntu]So instead of Ubuntu installing grub I would use those commands instead?

[Edit #2]I think I messed up Ubuntu. Let's try again. <_<

---

### Post by Jordanwb on 2008-05-01
I followed the instructions in that thread but now I can't boot into Windows or Ubuntu. I'm going to do a full format, restore the Windows and the MBR, disconnect the other two drives and try that.

[Edit] So far so good. I can boot into Ubuntu. Wow it boots so much faster than XP or Vista (IMHO Vista sucks). And I can boot into XP. Now I'm aware I need to mount the other two hard drives. I found a page on that. The only thing that went wrong was that I accidentally formatted my gaming drive instead of my main one. No biggy.

[Edit #2] Ooh Ubuntu automounted my drives for me.

---

### Post by ubnoobie on 2008-05-01
i remember filing a bug @ debian waaaay back in '04 on a similar problem: sata boot drive (sda) w/ winxp on sda1 installing pre-release sarge to ide drive (hda) where /boot is hda1 and / is hda3. grub installed to the ide instead of the sata. had to force d-i to put grub on the sata and then had to manually edit grub's menu.

there are numerous similar bugs at debian, and you'll find a few in launchpad [_here_]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=grub-install"), too.

---

