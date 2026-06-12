---
title: "Boot-Repair Failed"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by ali.ghandour on 2015-08-20
Hi all,

The link of the BootInfo
[http://paste.ubuntu.com/12135524/](http://paste.ubuntu.com/12135524/)

At the end of boot-repair, I got the following error:

boot-repair linux-signed-generic-** depends *** is to be installed

---

### Post by oldfred on 2015-08-20
If you want to turn secure boot on, then you need the signed versions of grub & the kernel. But with secure boot off, you do not need them.

What brand/model system?

You have installed with full drive LVM. Did you also install with the LVM with encryption option.
I do not use LVM, as it is a lot more complicated, but has some advantages for some users. But it is required if you want full drive encryption.

---

### Post by ali.ghandour on 2015-08-20
Thanks oldfred.

I am using HP Proliant server with Ubuntu server 14.

I am not sure if LVM with encryption option was chosen when installed Ubuntu the first time.

---

### Post by oldfred on 2015-08-20
I know LVM is often suggested for severs as it does give more flexibility on moving the logical partitions around. 

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

I know HP desktops are not UEFI boot friendly for anything but Windows. But I would expect them to support booting Linux on a server.
With desktops they modify UEFI to also use description. And only valid description is "Windows". That is not UEFI standard.

From summary report your efibootmgr -v shows a lot of entries, but both Windows & Ubuntu.
If you set ubuntu entry 0018 as first in boot order does it boot ubuntu?

Desktop changed boot order:

 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
      
 Change boot order with efibootmgr, some require all 4 char others 1 is ok.
[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr

[/URL]
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]
[/URL]

---

