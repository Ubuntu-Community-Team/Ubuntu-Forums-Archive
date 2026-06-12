---
title: "install ubuntu directly onto a HDD?"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by agent-orange2 on 2011-03-18
Ok, I have big problems. I tried to install ubuntu 10.10 onto an HP laptop and could not get anything to boot apart from windows vista. When I entered the boot options and selected CD to try and load the ubuntu CD it just booted off the HDD repeatedly. I removed (foolishly perhaps) the HDD and formatted it on my other machine, then created a start-up disk for ubuntu on it. I re-installed the hard drive and loaded ubuntu with no problems, but I can't install it. What do I need to do to the HDD (partitions, flags, etc) to make it so I can boot the iso from one part of the drive and install on the other? HELP PLEASE, its not even my laptop!!! Thanks, Rob.

---

### Post by oldfred on 2011-03-18
How did you install to the drive. What partition(s) do you have. It should work if you created the installer to a small 1GB partition and then have other partitions that are not mounted that you can install to.

```
sudo fdisk -lu
```

If CD was not booting did you burn it at the slowest speed you could, did you verify the down load?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Will laptop give you the option to boot a USB, that is quicker an easier if it is new enough.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by zvacet on 2011-03-18
If you still have iso then run [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") to be sure that iso is O.K.After that burn iso on lower possible speed.When you boot you will see option check disc for errors.If that goes fine go for install.

---

### Post by agent-orange2 on 2011-03-18
Sorry, I installed to the drive by using my other PC to create a start-up disk on it. I now have a drive with an ubuntu iso on it, and when I put the drive back into the laptop I can get to the use ubuntu now/ install ubuntu now options. I can use it fine, but when I go to install it I get a message. I thought that creating a startup disk on a small partition of the drive so the install can use the rest would work, but its not playing ball.

---

### Post by oldfred on 2011-03-18
Unless you manually set it up, the normal install assumes a 1 or 2GB flash drive and formats the entire drive to FAT and copies the files over. 
Can you run it in the liveCD mode?

---

### Post by Hedgehog1 on 2011-03-18
> **agent-orange2 said:**
> I** removed** (foolishly perhaps) **the HDD** and **formatted it** on my other machine, then created a **start-up disk for ubuntu _on it_**. I re-installed the hard drive and loaded ubuntu with no problems, but I can't install it. .
 
Rob,
 
I think I see the issue. Because you were unable to get a tradition CD to boot the laptop, **you copied the contents of the install CD onto hard drive, right?**
 
Sadly, you cannot install any OS this way. While it comes up as a LiveCD **_(now a LiveHDD)_**, the very hard drive you are running from is the same one the install wants to overwrite.
 
You will need to do the following:
 
One way or another, you need to get into the bios (or the one-time boot selection) and boot off of a LiveCD or a LiveUSB.
 
The real issue that got you here was that you could not boot off the CD drive, right? Everything else after that was trying to work around the not-booting issue.
 
**_What is the make and model of the laptop?_** Perhaps we can find the correct key to press during boot up up to get the BIOS to boot off of LiveCD or LiveUSB; which is what we all wanted in the first place.
 
***The Hedge***
 
:KS

---

### Post by agent-orange2 on 2011-03-18
Hedgehog1 you got it bang on the money mate! The laptop is a Packard Bell Easynote, serial numbers are well rubbed so I can't even make them out. It has an 80gb HDD (it must be old!) and intel 1.6ghz dual core. I can enter the boot menu but it won't load from the cd. have checked the drive and thats ok. It won't load of the usb stick, I don't even get that option from the boot menu. Any help greatly appreciated, love you lot!!!!

---

### Post by Hedgehog1 on 2011-03-18
agent-orange2,

***We hedgehogs have a sense for these things, you know.*** :D

Here is the link to the service manual for this laptop:  [Service-Manual-Packard-Bell-Easynote]("http://www.scribd.com/doc/46807390/37-Service-Manual-Packard-Bell-Easynote-Dt85")

Page 39 has what you want (***hedgehogs are also very fast readers of manuals, too***).

You can alter the boot order, boot off the LiveCD and be Ubuntu(ing) in no time (we hope).

***The Hedge***

:KS

---

