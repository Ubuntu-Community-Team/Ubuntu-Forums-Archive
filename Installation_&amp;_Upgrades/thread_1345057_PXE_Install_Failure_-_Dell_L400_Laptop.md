---
title: "PXE Install Failure - Dell L400 Laptop"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Domwilko on 2009-12-03
[LEFT]Hi,

Hoping someone can help with this one. I acquired an old Dell Latitude L400 laptop which was loaded with Windows XP, however because of the reasonably low spec. of the laptop it was predictably extremely slow. I therefore decided to install Ubuntu, which would be quick enough for general use.

Unfortunately, the Dell L400 is fitted with no floppy drive, optical drive and despite having a USB port, you are unable to boot to it.

Therefore, I decided to go down the PXE route.

To achieve this, I thought I'd use some existing equipment I already had configured:

Windows 2003 Server (DNS & DHCP Server) - running on VMware ESXi 4.0

I setup a DHCP scope and configure the boot options 66 & 67

Installed TFTPD32 and configured the TFTP server (obviously disabled the DHCP server).

I then followed the excellent instructions found in this post:

[http://ubuntuforums.org/showthread.php?t=327597](http://ubuntuforums.org/showthread.php?t=327597)

As the thread is a little old, I download the 'Jaunty' Netboot image from [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com)

From there, I created a new Virtual Machine on my VMware ESXi, forced it to PXE boot and 'BINGO' it all worked first time round. The PXE boot worked perfect and I was able to fully install Ubuntu.

Now confident that my setup was working, I now tried to PXE boot the Dell L400 laptop.

All appeared to be going well. The PXE boot worked, obtaining an IP address and loading as far as the Unbuntu Install splash-screen. From there I selected a standard Install (first menu option).

The screen then goes all black with 'Loading' in the top left corner. After a while, the message "Boot Failed: press any key or wait for reset" appears.

Checking on the TFTP server, the log shows the following entry:

File <ubuntu-installer\i386\linux> : error 131 in system call ReadFile An attempt was made to move the file pointer before the beginning of the file. [03/12 20:27:04.409]

I did some research and found this post that mentions this problem:

[http://ubuntuforums.org/showthread.php?t=1184285](http://ubuntuforums.org/showthread.php?t=1184285)

which suggests using the image ubuntu 8.04; however this image no longer seems to be available for FTP download. As a trial, I downloaded the 'Karmic' netboot image, but I still get the same problem.

Apologies for the long post, but I wanted to make sure I included as much information as possible.

Can anyone suggest a fix for this or offer any advice?

Thanks,

Dom



[/LEFT]

---

