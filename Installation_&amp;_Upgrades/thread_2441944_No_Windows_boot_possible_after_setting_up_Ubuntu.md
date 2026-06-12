---
title: "No Windows boot possible after setting up Ubuntu"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by hansefricke on 2020-04-28
Hey guys, 
I'm a complete newbie to Ubuntu and installed it on a computer with already Win7 and Win10 on it for University purposes.
The computer has three hard drives and was set up like this:

-120GB mSATA SSD with Win7
              ------100MB System-reserved NTFS
              ------119.9GB NTFS
-500GB HDD NTFS
-223GB SATA SSD with Win10 NTFS

during the setup of Ubuntu 18.04 I resized the Win10 Partition to 195GB to make space for this third OS in three Partitions as recommended.
Now Ubuntu is running fine, but GRUB only shows the options for Ubuntu and Win10. If i choose Win10 i get a plain purple screen and can't go further, so effectively I don't have access to both Win OS. I think the mistake was to resize the Win10-partition with Ubuntu and not a Windows-Tool.
I already tried Boot-Repair as recommended [here]("https://help.ubuntu.com/community/Boot-Repair") but it didn't bring me further.
Has someone any thoughts on how to proceed? This is the [report]("http://paste.ubuntu.com/p/C2YgZ3Gszt/") from the boot-repair tool.

Thanks!

edit: As seen in the report, the HDD without an OS doesn't seem to be registered at all in BIOS, but I wouldn't know how or if this affects the initial problem.

---

### Post by yancek on 2020-04-28
It's always best to modify windows partitions with windows software although the process usually works from Linux.  You did verify that windows was still bootable after the resizing before beginning the Ubuntu install, correct?  It's also generally recommended that you run chkdsk on windows after a change like this.

You have an entry in the grub.cfg menu of Ubuntu for windows on sdc1, the 119GB drive which appears to have windows 10 on sdc1 and sdc2.  Your other windows ( 7 ) is on sdb1.  

One problem you have is explained on line 163 of boot repair, the reference to Flexnet being on sdc.  Not sure how to repair/change this as I've never used it.  I don't think Grub will boot while this software is there.
You have Grub boot code in the MBR of sdb which is the drive on which Ubuntu is installed.  Is that device set to first boot priority in the BIOS?

---

### Post by oldfred on 2020-04-28
Years ago there were huge issues with flexnet. Grub overwrote flexnet & flexnet overwrote grub.
Now grub writes around sector 32, where flexnet is normally, so it still should work.
Since 2012 Windows has used UEFI as standard and then has a separate gpt partition for info like flexnet's code.

With BIOS & multiple drives best not to use Boot-Repair's default of installing grub to all drives. 
If you have Windows  on another drive, you really want the Windows BIOS boot loader in the MBR of that drive. You can use your Windows repair disk & fixMBR or Boot-Repair's advanced options and choose install and drive. It can install a Windows "type" boot loader, syslinux that will work. 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Grub only boots working Windows.
So if Windows turns fast start up back on with updates, grub will not boot it. If Windows is shutdown abnormally and needs chkdsk or has file issues and needs chkdsk grub will not boot it. Then you may be able to directly boot it, if the Windows boot loader is in MBR & f8 into repair console. Still better to have Windows repair flash drive.

---

### Post by hansefricke on 2020-04-30
After days of getting to know much stuff to Bios mbr gpt grub etc. I finally got it done!

With  flexnet wasn't a real problem, even if it was stated by BootRepair. The  Windows repair flash drive couldn't repair the issue. After all I  changed the boot priority to the sdc drive. With this i could boot up  with MBR directly into Win7, but the chkdsk was working over an hour for  every boot I made and soon windows freezed and I ultimately had to  force the shutdowns. Luckily i got able to use EasyBCD and got to use  Win10, unfortunetely with the same problem. Turns out the sda drive got  damaged and paralyzed the whole system. After I dismounted the sda drive  (500GB) from the computer everything worked well thanks to EasyBCD.

Thank you for your support, without your thoughts I wouldn't have gotten able to solve this!

---

