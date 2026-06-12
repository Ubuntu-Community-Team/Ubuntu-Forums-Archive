---
title: "How to chain GRUB for Ubuntu from Truecrypt &amp; its bootloader (multiboot alongside XP)"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by arjaydavis on 2010-08-23
I want Truecrypt to ask for password for Windows XP as usual but with the standard [ESC] option, on selecting that, i.e via Escape key, I want it to find the grub for the (unencrypted) Ubuntu install.

I've installed Windows XP on the 120Gb hard drive of a Toshiba NB100 netbook then partitioned to make room for Ubuntu 10.04 and installed that after the Windows XP install.

When I encrypt Windows XP, Truecrypt will overwrite the grub entry in the master boot record (MBR), I believe (?) and I won't be able to choose between XP and Ubuntu anymore. So I need to restore it back.

I've searched fairly extensively for answers on Ubuntu forums and elsewhere but have not yet found a complete answer that covers all eventualities, scenarios and error messages, or otherwise they talk of legacy GRUB and not GRUB2. Ubuntu 10.04 uses GRUB2.

My setup:

Partitions:

[LIST=1]
[*]Windows XP, NTFS (to be encrypted with Truecrypt), 40Gb
[*]/boot (Ext4, 1Gb)
[*]Ubuntu swap, 4Gb
[*]Ubuntu / (root) - main filesystem (20gb)
[*]NTFS share, 55Gb
[/LIST]

I know that the Truecrypt boot loader replaces the GRUB when boot up because I've already tried it on another laptop.



I want boot loader screen to look something like the usual:

Truecrypt

Enter password:

(or [ESC] to skip)

password is for WindowsXP and on pressing [ESC] for it to find the Ubuntu grub to boot from

Thanks in advance for your help.

The key area of the problem is how to instruct Truecrypt when escape key is pressed, and how the Grub/Ubuntu can be made visible to the truecrypt bootloader to find it, when the esc key is pressed. Also knowing as chaining.

---

### Post by Globestern on 2010-09-01
thats exactly the same where I was looking for..

---

### Post by oldfred on 2010-09-01
This says it will work:

[http://grub.enbug.org/TrueCrypt](http://grub.enbug.org/TrueCrypt)

More discussion:
[http://ubuntuforums.org/showthread.php?t=1229541&highlight=truecrypt](http://ubuntuforums.org/showthread.php?t=1229541&highlight=truecrypt)

[http://www.howtoforge.com/forums/showthread.php?p=184776#post184776](http://www.howtoforge.com/forums/showthread.php?p=184776#post184776)

---

### Post by Add3r on 2010-09-02
I am VERY interested too:
I have a laptop with Windows 7 and Truecrypt, and I'd like to know how to install Ubuntu in a non encrypted partition, without losing Windows 7 :-P
From the Truecrypt forums here
[http://forums.truecrypt.org/viewtopic.php?t=18667](http://forums.truecrypt.org/viewtopic.php?t=18667) 
I read:
"1. Install windows. Encrypt it. 
2. Install Ubuntu, **make sure to place GRUB on the Ubuntu-partition, not mbr. **
Now when the computer boots, the password prompt for windows will  appear. Typing correct password will boot windows. Pressing ESC will  boot Ubuntu."

will then it work with a simple Ubuntu installation, or do I have to perform some kind of advanced install to place grub in /boot?

Thanks!

---

### Post by oldfred on 2010-09-02
It is not saying install grub to /boot but to the Ubuntu partition.

Normally you install grub to the MBR - sda, sdb etc. Old grub could easily be installed to a partition boot sector or PBR - sda1, sda2, sdb1 etc. 

New grub can be installed to the Ubuntu partition boot sector but it will complain about blocklists. I as I understand block lists, they are hard coded addresses to find boot files. So if  a file gets moved then grub2 breaks and you have to reinstall it. New installs offer the advanced button on the last install screen and let you choose where to install grub2. If already installed you have to use -- force to get it to install.

---

### Post by slny on 2010-09-13
I think when they say to place grub on the Ubuntu partition they mean /boot.

I have a Windows 7 dual boot with Truecrypt along with Ubuntu 10.04 encrypted volume. 
Hitting escape allows me to choose to boot the Ubuntu /boot partition on which I've installed grub (Truecrypt bootloader brings up a menu)

Here's how to set it up:
1 - Install Windows (I have 7 but should be the same with XP)
2 - After install you'll have 2 partitions--a 100-200mb recovery partition and the actual system partition (XP will only have one partition)
3 - Install Linux with the alternate CD and create at least 2 partitions--/boot and an encrypted volume to house /root and /swap (or however you want it)
4 - When it asks where to put grub, select /boot (/dev/sda3 in my case) Note: if you have only one windows partition, the installer may not ask and just put grub on the MBR.  I've seen posts suggesting this, but I didn't run into this as the windows boot loader is on my recovery partition which is unencrypted.  If you have this problem, you'll need to use the Truecrypt recovery disc to restore Truecrypt to the MBR and then use the Ubuntu install disc to install grub to /boot
5 - After reboot, hitting escape at the Truecrypt bootloader will now ask you which unencrypted partition to boot--choose the one corresponding to /boot

This setup allows you to have a Truecrypted Windows install and Linux on an encrypted volume.
The only thing unencrypted will be /boot (unavoidable) and in Windows 7 case, the recovery partition (avoidable if you force one partition during install)

---

### Post by arjaydavis on 2010-09-30
Thanks slny I will give this a try - the key point here is using the Alternate CD instead of the usual LiveCD, and in the Alternate CD install process to choose where grub goes.

The Ubuntu 10.04 Alternate CD ISO image can be downloaded from here:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

You can then use something like, for example, the free ImgBurn burner program in Windows to burn it to a CD-R to boot from.

---

### Post by Add3r on 2010-10-07
Dear all, thanks for the precious hints.
I managed to install Ubuntu (with /home folder encrypted) besides Truecrypted Windows 7.
I had some problems, in the beginning to resize the windows 7 partition through the Ubuntu startup usb, because Gparted saw it as a unidentified or blank partition. I had to make space from within Windows 7, and since I cannot use administrative tools on WIndows7 ( ;-) ) I used the power terminal, with the utility "diskpart" to shrink the main Windows partition,
see here:
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)
[http://www.sevenforums.com/tutorials/2674-partition-volume-create-new.html](http://www.sevenforums.com/tutorials/2674-partition-volume-create-new.html)
 
once created the partition, I used Gparted from the Ubuntu startup disk to eliminate one of the primary partitions, and finally make the ext4 partition for Ubuntu.
From there this tutorial site proved useful:
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

I only had to take care to where I installed Grub (click on Advanced installation), and I opted for an encrypted /home folder, for the rest everything works smooth and fine.

Cheers!

---

