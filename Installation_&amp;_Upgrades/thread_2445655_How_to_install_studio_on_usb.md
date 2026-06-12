---
title: "How to install studio on usb"
date: 2020-06-17
forum: Installation &amp; Upgrades
---

### Post by ozstar on 2020-06-17
Hi,

I am trying to capture from a DV cam to a PC.  Win 10 won't allow 1394 card anymore so it has been suggested I go to ubuntu and dvgrab.

I want to keep my Win10 on the Desktop but would like to get Linux on a usb stick to use or  as a dual boot which ever is easiest.

I have read a few install tutors but still a little confused on how to get it onto the stick as an o/s.   

I have both studio and regular ubuntu downloaded but where to now to get it into the stick ready?

Thanks

oz

---

### Post by sudodus on 2020-06-18
It is always easier to install Ubuntu and an Ubuntu family flavour (e.g. Ubuntu Studio) into an external drive, if you unplug, disconnect or otherwise disable the internal drive. It is particularly important if your computer boots in UEFI mode (and computers that were sold with Windows 10 usually do).

There are some methods to do it. See the following links,

[Step-wise instructions for installed system in a USB drive](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

[How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by ozstar on 2020-06-18
Many thanks.  

I installed it onto a USB drive using Rufus and although it said it was Ready, I haven't been able to boot from it.  I tried a few PC boxes but Win explorer cannot even detect it is in the port.

Read those articles but still can't see what I need to do.  In the bios of the box I went to use this, I cannot see the UEFI mode option, if that is what I need to do. It is an old home mad tower which works fine in 7 and 10 except for the firewire.

---

### Post by sudodus on 2020-06-18
Rufus has a good reputation, and will usually create bootable drives from Ubuntu [Studio] iso files.

- Have you checked with md5sum that the iso file was downloaded correctly? (Rufus can do this check for you.)

- It is not relevant if Windows Explorer can see the drive. It is important that the computer's UEFI/BIOS system can see it and boot from it. [This link](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB) can help you.

- When booted into one USB drive (with a system created by Rufus), you can install Ubuntu [Studio] into another USB drive. This second USB drive should be a big and fast USB3 drive. Otherwise the system will be slow. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/pre).

It was this step that I described in my first post ([Post #2](https://ubuntuforums.org/showthread.php?t=2445655&p=13966243#post13966243)) in this thread.

---

### Post by sudodus on 2020-06-18
How old is the computer? Can it run 64-bit operating systems? (The current Ubuntu and Ubuntu Studio versions are 64-bit systems and cannot run in old 32-bit computers.)

---

### Post by ozstar on 2020-06-18
Thanks again. Yes it is x64 and is about vintage 2010. It was when used to build them up myself.

I still can't get to that stick in windows or Linux so decided to try again with another one and this time is worked well.

It booted up okay and looks really nice. 

I now need dvgab and Openshot but not sure how to get them onto the stick.

Any suggestion please?

---

### Post by ubfan1 on 2020-06-18
If you have network connectivity (either ethernet or wireless), in a terminal (ctrl-alt-t will start one), just type:  
sudo apt-get install dvgrab openshot

---

### Post by ozstar on 2020-06-19
Thank you. Did that but the usb stick didn't have enough room so am now trying to get Rufus on a 32GB one but it has stuck on Deleting partitions for the last 2 hours..  Doing from Win 10 x64 box

---

### Post by sudodus on 2020-06-19
> **ozstar said:**
> Thank you. Did that but the usb stick didn't have enough room so am now trying to get Rufus on a 32GB one but it has stuck on Deleting partitions for the last 2 hours..  Doing from Win 10 x64 box

This USB drive should be a **big and fast** USB3 drive. Otherwise the system will be slow. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/pre).

---

### Post by ozstar on 2020-06-21
Many thanks.  I decided to install on a 120GB SSD I had but am having trouble getting it to boot to it after I installed it. 

It says is has installed but the cursor just blinks top left when I boot.  I have set it okay in Bios to boot to the SSD.
I started a Thread here..
[https://ubuntuforums.org/showthread.php?t=2445857](https://ubuntuforums.org/showthread.php?t=2445857)

---

### Post by C.S.Cameron on 2020-06-21
A couple of my computers are only seven years old but are BIOS boot only.
The GPT - UEFI (non CFM) do not work on BIOS only computers.
Rufus might need to be run MBR - BIOS or UEFI.
balenaEtcher or UNetbootin are also a good choice for installing on older systems.

---

