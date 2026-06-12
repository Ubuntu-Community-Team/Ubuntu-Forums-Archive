---
title: "Stuck at &quot;Boot from CD/DVD:&quot;"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by superawesomepanda on 2011-11-06
I tried installing Ubuntu/Kubuntu 11.10 and 10.04 using a usb drive and I got stuck at "Boot from CD/DVD:" with a blinking cursor beneath it. Doesn't respond to anything unless I pull the drive out then it gave a fail to boot msg and when I hit Enter, it loads Windows.

Windows 7 is already installed on the hard-disk. I'm trying to go for dual boot.

Anyone know how do I go about solving this?

---

### Post by critin on 2011-11-06
> I tried installing Ubuntu/Kubuntu 11.10 and 10.04 using a usb drive and I got stuck at "Boot from CD/DVD:" Are you trying to boot from a usb stick or cd?

You tried both versions at different times, or are they both on the same usb (together)?  Have you installed before this?  In other words, you know how and when to choose 'boot from cd / flash after starting the computer?
It  sounds like the image on the usb isn't a live image or you should be choosing usb boot instead of cd boot.  it isn't clear (to me)  if you're using a usb flash to install, or trying to install from a cd onto a usb drive.

---

### Post by superawesomepanda on 2011-11-06
> **critin said:**
> Are you trying to boot from a usb stick or cd?

You tried both versions at different times, or are they both on the same usb (together)?  Have you installed before this?  In other words, you know how and when to choose 'boot from cd / flash after starting the computer?
It  sounds like the image on the usb isn't a live image or you should be choosing usb boot instead of cd boot.

I used a usb stick. Tried both at different times of course. I have the following images:
kubuntu-11.10-desktop-i386
ubuntu-11.10-desktop-i386


The usb boot is set up using UNetBootin. I opened up the boot menu during boot and I selected the usb stick.

---

### Post by oldfred on 2011-11-06
I would change BIOS so CD is not first. But it should fail and go to next device. 

Do you have a bootable CD in the tray that really is broken so it tries to boot CD?

---

### Post by superawesomepanda on 2011-11-06
Nothing in the CD tray. I just removed CD-ROM from the 3 boot priorities in BIOS and set the usb stick to boot first. Same result.

---

### Post by oldfred on 2011-11-06
It seems like the system thinks the flash drive is a CD. Was it  created correctly? Is it really a bootable USB flash drive?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by superawesomepanda on 2011-11-06
I just realised the ISOs I have are for x86. and I'm using AMD64. Does that make much difference?

Edit: I got wubi installed so I'm gonna stick to that for now. Previously I installed Kubuntu wubi then I uninstall it and installed Ubuntu wubi instead. Now, at boot where I have to pick an OS to load, Kubuntu is still there along with Ubuntu and Windows 7. But when I clicked on Kubuntu, I get an error (of course, since I uninstalled it). How do I stop it from showing up?

---

### Post by oldfred on 2011-11-07
i think with Windows 7 you need to edit the BCD with BCDedit.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by superawesomepanda on 2011-11-26
Problem not solved but I used a CD so its all good. 

Thanks guys.

---

