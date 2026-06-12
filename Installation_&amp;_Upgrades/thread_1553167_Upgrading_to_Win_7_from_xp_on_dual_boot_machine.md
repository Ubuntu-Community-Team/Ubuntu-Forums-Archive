---
title: "Upgrading to Win 7 from xp on dual boot machine"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by Dreigo42 on 2010-08-14
I am currently running Ubuntu Desktop 10.04 and windows xp in a dual-boot. I am looking to upgrade to windows 7 on the windows side soon but would rather not do a complete rebuild of the whole thing. The two are on separate hard drives so would i just install it on the Windows drive and then follow the instructions at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) or is there an easier way?

---

### Post by oldfred on 2010-08-15
When you installed Ubuntu did grub get installed to the windows drive or the Ubuntu drive? I like to have the boot loader in the MBR of the system on that drive and use BIOS to set to boot the Ubuntu drive as grub will let you choose Ubuntu or windows.

I would install grub to the Ubuntu drive and make sure it boots (one time key or BIOS), then install windows on the other drive. Not sure if it makes a difference if windows is sda or sdb, but I know if windows is sda it works easier.


Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Dreigo42 on 2010-08-15
I would assume that GRUB is on the Ubuntu drive as I originally did it Win XP install then Ubuntu. I just followed the on screen install guide for ubuntu and picked the empty disk for the ubuntu install. Thats why this is all new to me. XP is on sda, Ubuntu on sdb. Not sure which drive boots in terms of sda or sdb. I believe it boots sdb first as I currently use GRUB to pick between the two.

---

### Post by oldfred on 2010-08-15
Unless you used the advanced button in the Ubuntu install, it installs to sda. And it then overwrites the windows boot loader, but you do not then have to change boot drives in BIOS.

[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

If you are in you Ubuntu install you can to this to install grub to the sdb drive.
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb

---

### Post by Dreigo42 on 2010-08-15
Installing GRUB to sdb went smoothly and can now boot from either. Thanks for your help. Would it be easiest to install 7 on sda and then switch to make sdb the primary boot drive?

---

### Post by oldfred on 2010-08-15
Yes make sda the primary and install win7. You can directly boot it and make sure it works ok.

Then you can in BIOS switch to sdb. After booting if you run this it should find your new win7 install and let you boot either Ubuntu or win7.

sudo update-grub

Win7 apps sometimes write hidden data into the MBR, and because grub2 is slightly larger than the win7 boot loader, it gets corrupted. With grub2 in the MBR of sdb you avoid those type of issues.

---

### Post by Dreigo42 on 2010-08-16
Thanks a lot. This will make my upgrading much easier

---

