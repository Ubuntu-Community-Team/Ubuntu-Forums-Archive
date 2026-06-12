---
title: "Boot repair with full system encryption failed"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by afavaro on 2013-01-11
I've just bought this Inspiron 14 3420 laptop, with 1TB HD, 4GB RAM. I tried installing Windows 7 which did work, I partitioned it with a 500GB partition for windows, and left the rest as unused space. A problem is that the Ubuntu installer and the Debian installer (I tried, and installed both sucessfully in this laptop not at the same time) doesn't see those partitions it only sees a 1TB partition. I tried more than once, a time with creating two partitions also. It didn't recognize it either. So my option was trying to install first Ubuntu then install Windows and later use boot repair to recover GRUB. I ran boot repair on Ubuntu and I did setup something wrong I think I choosed to install GRUB on /boot which is uncrypted, along this /boot i had two crypto partitions one for /, other a swap space.I want full system encryption, I installed it with full system encryption with Ubuntu and Debian at different times. Now the notebook loops on boot, it loops the screen before boot. I tried the Boot Repair Disk and it didn't work, it had options disabled for some reason. It generated a log which is this [http://paste2.org/p/2730912](http://paste2.org/p/2730912) . Any thoughts on how could I get Ubuntu with full system encryption working in a dual boot with windows? (I already did that in a desktop) Is it possible or recommendable to repair the system now?

---

### Post by oldfred on 2013-01-11
I do not know encryption. But think you have to mount that first as Boot-Repair will not ask for passphase.

You have gpt partitions. Windows only install in UEFI mode with gpt partitions, but it looks like you have Ubuntu in BIOS mode.

Windows 7 has the separate 100MB boot/repair partition so you can encrypt your main install. 

While grub2 has drivers for LVM and RAID, with encryption I would think you still need the separate /boot??

Not sure about dual boot and full disk encryption.

       Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
settings and lots of info:
sudo tune2fs -l /dev/sda1
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

