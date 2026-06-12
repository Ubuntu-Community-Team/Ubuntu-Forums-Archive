---
title: "After installing Ubuntu to USB, Netbook won't boot without USB drive"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by dougiemo on 2010-08-09
I recently purchased a Eee 1005PE.  I used a Ubuntu live USB and installed Ubuntu 10.04 onto a different USB drive.  My plan was that I would run Win 7 when I didn't put in the USB, but when I put in the USB, I could dual boot and run Ubuntu.  Ubuntu works great and I love it.  The problem is that the install put the grub in such a place that when I don't have the Ubuntu USB drive in, I can't boot to windows but get the grub recovery screen.  

I have searched these threads and have attempted to move the grub.  The only problem is when I open a terminal and type "sudo grub" I get the response "command not found."  Here is what i get when I search for "grub"

/etc/default/grub
/var/lib/ucf/cache/:etc:default:grub
/usr/lib/grub
/usr/lib/linux-boot-probes/mounted/40grub
/usr/lib/grub-legacy/update-grub
/usr/share/recovery-mode/options/grub
/usr/share/grub
/usr/share/grub/default/grub
/usr/sbin/update-grub
/boot/grub

What do I need to do to move the grub and fix Windows' MBR?  I am new to Linux except for the days I have spent trying to fix this problem.  Thanks in advance for any assistance.

---

### Post by clrg on 2010-08-09
I guess GRUB is on the USB drive now. To fix windows' MBR, boot from your windows installation DVD, start a recovery shell and run fixmbr. That should restore the MS bootloader.

---

### Post by elliotn on 2010-08-09
Then install grub on the win7 drive, that way u will use win7 even if u have removed the usb

---

### Post by dougiemo on 2010-08-09
I installed Windows revcovery onto a USB and it works on my other laptop (Eee netbooks don't come with the Windows DVD), however, when I attempt to run it on my Netbook, I still get the grub rescue menu.
 
I do have my boot booster disabled and have set the netbook to boot first to the USB.

---

### Post by confused57 on 2010-08-09
You should be able to repair your installations using the live usb:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by dougiemo on 2010-08-09
**Re: After installing Ubuntu to USB, Netbook won't boot without USB drive** 
You should be able to repair your installations using the live usb:
[http://sourceforge.net/apps/mediawik...external_drive]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive")
__________________
[Dualboot]("http://members.iinet.net/~herman546/index.html")
[UbuntuTutorials]("http://www.psychocats.net/ubuntu/index.php") 
[Dualboot 2 HD]("http://www.ubuntuforums.org/showthread.php?t=179902") 
[Documentation]("https://help.ubuntu.com/community/UserDocumentation") 
 
 
Thanks for the info and the link.  It all went smoothly.  Win 7 now boots up again whether or not the Ubuntu usb drive is in.  Now I just need to figure out how to set it up so I will get the option to dual boot when the ubuntu usb drive is in, but still pull up windows when the ubuntu drive is not in

---

### Post by confused57 on 2010-08-09
Also see section #13 here for reinstalling grub2 to the mbr of your USB drive:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The key is to first run this in a terminal:
```
sudo fdisk -l
```
This will determine which is your Ubuntu USB drive where you will want to install grub2's mbr(e.g. /dev/sdb or possibly /dev/sdc), just make sure not to put a number(partition) after the drive designation(e.g. /dev/sdb1 or sdc1).

Once you get Ubuntu booting from your USB drive, you'd need to run:
```
sudo dpkg-reconfigure grub-pc
```
then select where grub is to be installed when update-grub is run(after a kernel update).

---

### Post by dougiemo on 2010-08-09
I have been having a hard time booting fom the USB, but it all works now.  I just need to hit "esc" when it is booting to get into the grub on the USB drive.  Thanks for the posts.

---

### Post by clrg on 2010-08-09
Please mark the thread as solved.

---

