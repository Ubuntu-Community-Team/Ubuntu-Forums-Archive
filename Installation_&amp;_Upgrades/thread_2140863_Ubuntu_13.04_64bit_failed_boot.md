---
title: "Ubuntu 13.04 64bit failed boot"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by mruck05 on 2013-04-30
I've been trying to boot Ubuntu 13 from a usb that I made using yumi. I went in changed to boot from legacy first and got yumi to come up with Ubuntu but then when I try to boot it, it comes up with an error saying invalid or corrupt kernel. I have a Lenovo Y500 with a core i7 and NVidia gt650m graphics card which ive seen can cause to problems with Ubuntu. Any suggestions on how to get Ubuntu booted?

---

### Post by oldfred on 2013-05-01
Corrupt kernel still sounds like either a bad ISO or install to flash drive. You can use md5sum to verify download.

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Others have had issues.

 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

With nVidia you will need the nomodeset boot option to boot live installer and on first boot or until nVidia driver is installed. Use e on grub menu, and on Linux line change quiet splash to nomodeset.

---

### Post by mruck05 on 2013-05-05
so I used md5sum and the hashes were different, what would cause that to happen? Should I use a different USB creator? I used yumi when I did it.

---

### Post by oldfred on 2013-05-05
That would be the download. Some have success with different install creators. Or maybe doing it a second time works?

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

      
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

---

### Post by mruck05 on 2013-05-07
So I didn't burn the iso to a disk or usb and have tried downloading the iso from Ubuntu 4 different times and all 3 times I get a different hash then is listed. I'm not sure where I'm going wrong here.

---

### Post by oldfred on 2013-05-07
Never mind those instructions were from a Linux terminal, if you only have Windows it will not work.

How are you downloading? Are you using Firefox. I have stopped & started Firefox & gotten good downloads.

---

### Post by mruck05 on 2013-05-07
yeah I only have windows 8 and its terrible btw I hate it need it gone lol. I'm just using internet explorer ill try downloading from firefox next. thanks.

---

### Post by mruck05 on 2013-05-08
Thank you so much downloading from firefox did the trick, as well as possibly the update from pendrivelinux. I'm going to be running Ubuntu live for a while until I get the feel for it this is my first run in with Linux. I have notice the problem of not being able to control my brightness so I suppose ill tackle that task next when I install Ubuntu.

---

