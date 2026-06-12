---
title: "Boot Repair not loading GRUB"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by chumyash92 on 2015-05-25
Hi, recently I installed windows 7 and when I reboot I no longer see GRUB and it boots directly into windows.
Initially I had Windows 8.1 and Ubuntu installed side by side, I decided to downgrade to windows 7, hence the above problem.
Here is the report of Boot Repair: [http://paste2.org/zV9BhyFp](http://paste2.org/zV9BhyFp)

---

### Post by yancek on 2015-05-25
During your installation of windows 7, you have overwritten your Ubuntu install.  I hope you had backups of whatever you had on the Ubuntu partition(s) as the only sign of a Linux system on your drive is the old swap partition.  If you want to continue using Ubuntu you will need to reinstall.

---

### Post by chumyash92 on 2015-05-25
Really, I've to reinstall? I still see the partition I allocated for Ubuntu beside the swap, but it is marked as unallocated :/ Is there no way to restore Ubuntu apart from reinstalling?

---

### Post by oldfred on 2015-05-25
Yes you can restore it and in many cases it just works again.

Windows does not see Linux partitions, not sure why it then sees swap. But it rewrites partition table on its install and leaves out the Linux partition in the extended partition.

Many use testdisk and just restore missing partition, you have to keep all the other partitions also and keep primary as primary and logical as logical.

Testdisk is in repository so you can download directly into live installer you used to run Boot-Repair.
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You may be able to use parted rescue since you have a good idea of start & end sectors.

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by chumyash92 on 2015-05-25
I managed to find the partition containing my data with TestDisk, but I'm stuck at this stage:
[IMG]http://i61.tinypic.com/5dmfdk.png[/IMG]What should I do next to make it bootable?
Edit: I chose the option <write> and when I rebooted it gave me an error: OS not found, now it won't boot into windows either :(

---

### Post by oldfred on 2015-05-25
You have to first restore partition then restore a grub2 boot loader to MBR.

Did you restore partition, then Boot-Repair or manual reinstall of grub to MBR should work.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by chumyash92 on 2015-05-29
Hi, sorry for the late reply, had exams.
I've tired every link above, each yields some errors, can you help me with a noob friendly guide on how to restore grub?

---

### Post by oldfred on 2015-05-29
Did you restore partition. If you changed partitions a lot testdisk may find all the old versions. You have to select the one correct set of partitions.

Or what errors are you getting?

Once the Ubuntu partition is restored, Boot-Repair should be able to just restore grub to MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by chumyash92 on 2015-05-29
yes I've restored the partitions wit testdisk, I've selected the ext4 partition and chose "write". Then i installed boot-repair and it says the following: "GPT detected. Please create a BIOS-Boot partition (>1MB, unformated filesystem, bios_grub flag)..... Then try again"

---

### Post by chumyash92 on 2015-05-29
Here is the report: [http://paste.ubuntu.com/11435219/](http://paste.ubuntu.com/11435219/)

---

### Post by oldfred on 2015-05-29
It looks like you have Windows in BIOS with MBR partitioning.
Was your Windows 8 UEFI with gpt partitioning?
 
Windows 7 can be installed in either UEFI or BIOS modes, but defaults to BIOS. You have to copy to flash drive and move some efi boot files around so it can boot in UEFI mode.
If you install Windows in BIOS/MBR mode to a gpt disk it converts drive to MBR, but does it incorrectly. It is a Windows error, but can be fixed with fixparts.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by chumyash92 on 2015-05-29
I get an error from fixParts: " This Disk appears ti be a GPT disk. Use GNU parted or GPT fdisk on it!"

---

### Post by oldfred on 2015-05-29
Then somehow you converted to gpt. You can just do a convert to MBR(msdos).
Or reinstall Windows in UEFI boot mode, but that probably will erase everything all over again.

Follow the parts of the instructions on gpt to MBR.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by chumyash92 on 2015-05-29
I've managed to convert the disk to MBR, what partition should I make primary and/or logical?

---

### Post by oldfred on 2015-05-29
Probably best to see what partitions you now have.
Windows only boots from primary NTFS partitions, its standard install uses two of the 4 primary. 
Linux almost always creates swap as logical inside an extended and depending on what available partitions you have may have / (root) as primary or logical. 
Post this:
sudo parted -l

---

### Post by chumyash92 on 2015-05-29
[IMG]http://oi60.tinypic.com/2m3l4xe.jpg[/IMG]

---

### Post by oldfred on 2015-05-30
Please post text output as copy & paste. If longer be sure to use code tags which are the # in the advanced editor. And if a screen shot from a gui app, then attach not post in line. You use paperclip in advanced editor to add screen shots.

It says msdos and shows partitions. Does Boot-Repair install grub to MBR?

---

### Post by chumyash92 on 2015-05-30
It worked :D Both Ubuntu and windows boots perfectly! Thank you so so much, you helped a lot, I wanna hug you dude :p

---

### Post by oldfred on 2015-05-30
Glad it worked.
Please change to solved.

---

