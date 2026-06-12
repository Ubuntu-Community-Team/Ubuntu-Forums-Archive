---
title: "'Live install' on internal HDD"
date: 2016-04-19
forum: Installation &amp; Upgrades
---

### Post by v1sual-3rr0r on 2016-04-19
I am interested in running Kubuntu 14.04 on my internal HDD live, in essence as a frugal install. I have Kubuntu on sda3 on my drive. It is in its own folder named kb. The folder structure to run live is correct. I am using syslinux as my bootloader.  I also have a partition sda4 labeled casper-rw. Both partitions are ext4. I have spent the last couple of days trying to get this to work. It starts loading but then I get the following initramfs error.

> (initramfs) Unable to find a medium containing a live file system

It works on my USB stick which is also formatted ext4. Any help would be appreciated.

This is the syntax I am using right not to boot Kubutu.

> LABEL KUBUNTU
MENU LABEL Kubuntu
kernel /kb/casper/vmlinuz.efi
append initrd=/kb/casper/initrd.lz file=/kb/preseed/kubuntu.seed boot=casper  quiet splash -- persistent

---

### Post by yancek on 2016-04-19
> The folder structure to run live is correct.

It won't work if you have the directories and files in the 'kb' directory.  You need to put the directories and files in the root of the partition.  I've tried this a number of times with various Ubuntus and it never worked unless the files were in the root of the partition.  Works like a charm in the root of the partition.  There should not be any directories/files with the same names but check before you copy everything to the root of that partition and modify the syslinux.cfg menuentry.  It works with Grub and should work with syslinux although I don't use syslinux and haven't tried it.  I don't know if the casper-rw will work.

---

### Post by sudodus on 2016-04-20
Welcome to the Ubuntu Forums :-)

I suggest that you try [mkusb](https://help.ubuntu.com/community/mkusb). It can make a persistent live system automatically (all the configuring), and it boot in UEFI as well as in BIOS mode. In what computers are you planning to run it?

See this link [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Notice: mkusb wipes the drive, so make sure that you have nothing else there. If you want a dual boot system with Windows, you have to make it manually.

---

### Post by yancek on 2016-04-20
> I don't know if the casper-rw will work. 		

I tested the method I suggested above of putting all the extracted directories/files from the loop mounted iso in the root of an empty partition.  I used another empty partition and gave it the label 'casper'rw'.  Then put an entry in grub.cfg fom another OS installed on the drive and it booted without problems.    I could create directories and files which remain on reboot so I think the problem is the 'kb' directory and having everything in it.  This has never worked when I tried with any Ubuntu.

---

### Post by v1sual-3rr0r on 2016-04-21
Thanks! It worked for me as well. Weird about it not working in it's own folder. Now I just need to figure out a way to disable the default live user session from logging in. Nothing I do seems to stop it.

---

### Post by yancek on 2016-04-22
Almost every Linux I have used in this manner requires the directories/files needed to boot the Live system in the root of the filesystem/partition so that's pretty common.  The only distribution I can remember using that will work with these directories/files in another  directory is Puppy Linux which is pretty different from the average Linux.

---

### Post by yancek on 2016-04-22
I have a Live Install of Zorin which is based on Lubuntu and uses the LXDE Desktop also.  To disable the autologin of the live user, I used this:  sudo leafpad /etc/lightdm/lightdm.conf  which opened that file.  Near the top of the page is:
autologin-user=live  Delete live from that line.  

Some other possibilities at the link below:

 [http://askubuntu.com/questions/182274/how-to-disable-autologin-in-lubuntu](http://askubuntu.com/questions/182274/how-to-disable-autologin-in-lubuntu)

---

### Post by C.S.Cameron on 2016-04-23
I have had a hard time getting persistent installs of post 12.04 64bit 'buntu running with persistent partitions made using SDC or Unitbootin.
Persistent partitions still work ok with a 64bit grub2 / iso install, see MultiBootUSB or grub-n-iso / mkusb.

---

### Post by v1sual-3rr0r on 2016-04-23
> **C.S.Cameron said:**
> I have had a hard time getting persistent installs of post 12.04 64bit 'buntu running with persistent partitions made using SDC or Unitbootin.
Persistent partitions still work ok with a 64bit grub2 / iso install, see MultiBootUSB or grub-n-iso / mkusb.


I have the persistent on HDD part resolved. Cannot be in a sub-directory has to be in root.

---

### Post by C.S.Cameron on 2016-04-23
Did you say both O/S and casper-rw are on ext4 partitions?
I have never been able to make a persistent or live O/S on anything but a FAT32 partition.
Ext4 used to work for casper-rw but I have not had success with persistent partitions since 12.04 unless 32 bit.

---

### Post by sudodus on 2016-04-23
***mkusb*** makes a persistent live system that boots off a FAT32 partition, that works in both BIOS and UEFI mode. The small separate files from inside the iso file are copied to that partition. The whole iso file is cloned to another partition with its ISO9660 file system and everything. See this link for details.

[mkusb/persistent#Partitions](https://help.ubuntu.com/community/mkusb/persistent#Partitions)

Notice that GPT (GUID partition table) is used and there is an NTFS partition with number #1 but located at the end of the drive. This way it is possible to have a persistent live system in a huge external hard disk drive and use the main part of it for storage, which is available to Windows as well as linux. I have tested that it works with a 4 TB hard disk drive.

---

