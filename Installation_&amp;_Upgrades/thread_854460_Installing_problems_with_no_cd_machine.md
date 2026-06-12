---
title: "Installing problems with no cd machine"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by chadcan on 2008-07-09
Okay,

I am having a hard time install Ubuntu Server 8 on a machine with no CD rom. I have looked into the installation documentation ie. [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) and [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux). And have been able to boot the installer and start the installation process.

But it still checks and ask for the cd when installing. 

My question is what do I need to change to make the installer read the installation files on the hard drive and stop it from trying to find a cd?

---

### Post by pytheas22 on 2008-07-09
What are the steps that you've taken so far, and at which point exactly is it asking you for the CD?

Also, if your machine can boot to USB, have you taken a look at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ?

---

### Post by chadcan on 2008-07-09
I tried most of the installation guides from [https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/).

But have the same problem the installation files on the hard drive still as for the CD-ROM.

Anyone have an experience in change the scripts in the files to read the hard drive?

Please note I am installing from hard drive online. Don't want to do network installation.

---

### Post by chadcan on 2008-07-09
pytheas22,

I got everything working to the point where it starts the installation process. But gets stuck when the ubuntu installer ask for the cd.

It's the same point as if I was installing from a cd. It get's to the point where it verifies the cd and try's to copy the installation files from it.

I need the Ubuntu installer to see that there is no cd and copy the installation files from the hard drive.

Unfortunately this machine is to old to boot off USB. But even if it did I think I would still run into the same problem. If the installation files where on a USB drive. When the installer launchers it would still ask to find the cd.

I completed the installation tutorial on [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) and [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
to the end of the tutorial and everything works. But the installer will ask for the cd in the installation process which is not covered in the Tutorial.

---

### Post by CC_machine on 2008-07-09
could you borrow a CD drive from one of your other systems for the 10-20 mins that installation takes? or is the system a laptop / other proprietary "fixed" hardware?

---

### Post by chadcan on 2008-07-09
yea, I was thinking about that, but unfortunately there is no cd rom on this computer. I tried a usb cd-rom but the bios does not allow for boot from any USB devices. So i am stuck with putting the installation files onto another partition on the hard drive.

---

### Post by avtolle on 2008-07-09
Silly question, but let me ask it; you are using the alternate install iso, correct?

---

### Post by chadcan on 2008-07-09
Not a silly question at all. I am not using the alternative cd. According to the documentation on the web sites I noted above. It should work with Ubuntu 8.04 and Ubuntu 7.10. And 8 does not have an alternative cd.

---

### Post by avtolle on 2008-07-09
Well, according to the Wiki piece, it indicates that the alternative iso is to be used (the one about installing from Windows). There is an alternate install iso available for 8.04, BTW, go to the download page at ubuntu.com, and about half-way or a bit more down the page is a check box to obtain the alternate iso.

EDIT: For clarity, this is the one to which I was making reference: [https://help.ubuntu.com/community/Installation/FromWindows ]("https://help.ubuntu.com/community/Installation/FromWindows")
where about two-thirds the way down the page there is a discussion about using the iso.

---

### Post by chadcan on 2008-07-09
You are absolutely right. I will give that a try. MANY Thanks. I will post the outcome.

---

### Post by chadcan on 2008-07-09
Sorry guys alternative cd did not work either. Came up with the same result. I can run the installer off the hard drive. But then it goes to try and find a cd. If it can't it just says failed and cancel to quite installation. 

Anyhow What I did was. I found the driver for the network card and did a minimal download and installation with floppies. So I got it going.

Thanks to all who replied.

---

