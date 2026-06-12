---
title: "Xubuntu ISO won't boot?"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by mike183 on 2014-05-01
Hi guys, I'm trying to install Xubuntu and downloaded, burned the .iso to a disc but my computer won't boot the image. Autoplay window pops up and only directs me to the directory of the .iso. I can't seem to find the file to boot and install.

Any ideas?

I'm running Windows 7 with an i7-2670QM and 8gb on ram on an Acer Aspire 5750G.

Thanks guys!

---

### Post by grahammechanical on 2014-05-01
Could it be that you are running this disk with Windows loaded? How do you wish to install Ubuntu? Do you wish to install Ubuntu to the hard disk as a dual boot with Windows? Or do you wish to install Ubuntu inside Windows using Wubi.exe?

We usually change the motherboard boot options to look for an OS on either a DVD drive or a USB port (whichever is applicable) before the motherboard looks for an OS on the hard disk. In this way a live Ubuntu/Xubuntu session load and we can Try Xubuntu or Install Xubuntu.

Please clarify what you are trying to do.

Regards.

---

### Post by mike183 on 2014-05-01
Hi and thank you very much for the reply! Sorry, I should of mentioned what I wanted to do!

I'd like to install and have a dual boot with Windows, if that is possible.

Thanks

---

### Post by oldfred on 2014-05-01
You have to install ISO to DVD or flash drive not copy it. Then it becomes bootable.
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Most Windows 7 systems use all 4 primary partitions under MBR(msdos( partitioning.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

Best to use Windows to shrink the main Windows install and reboot so it can run its chkdsk and may whatever repairs it needs for its new size.

Make a full image backup and a Windows repairCD or flash drive. You may need it.

 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)       

 [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[URL="http://www.ubuntu.com/download/help/install-desktop-long-term-support"]http://www.ubuntu.com/download/help/install-desktop-long-term-support
[/URL]

---

### Post by lisati on 2014-05-01
If you're using CD/DVD, did you use "burn as image"? Doing a straight copy of the ISO file to disk doesn't usually work.

---

### Post by Bashing-om on 2014-05-01
mike183; Hi !

Let's get you installed and booting ubuntu !

1) Check the integrity of the downloaded .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

2) Burn th .iso to disk as an IMAGE, not data - at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

3) Install ubuntu along side - dual booting:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://ubuntuforums.org/showthread.php?t=2126166&page=2](http://ubuntuforums.org/showthread.php?t=2126166&page=2)
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

3a) Some Windows 7 "Might" be UEFI endowed - 
------dual boot & UEFI advise--------
[http://ubuntuforums.org/showthread.php?t=2059640](http://ubuntuforums.org/showthread.php?t=2059640)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

I hope in your next post we can welcome you to our world.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

