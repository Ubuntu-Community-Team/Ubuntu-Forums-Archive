---
title: "Partial Install of XP partition"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by jdmarsh2g on 2011-01-29
Good morning, I have an older Dell Inspiron e1505. The hard-drive went bad years ago and I look to revive it. I purchased a new hard-drive and proceeded to install Windows XP Pro that I have a partial install of XP professional but do not have the key.
Microsoft explained because I cannot find I would have to buy a new one instead of keeping my key within their Microsoft store. So instead of purchasing a new key I would like to install the latest version of Ubuntu and go the Linux route. I downloaded the latest version(non pc I believe) and have it booting of the Cdrom. I am now stuck because it bypasses the cdrom /disk and starts to load XP home again. Will continue to research as I move forward but would definitely like some pointers on what I can do as far as removing the partial install of Windows XP home.
Greatly appreciated.
thanks, 
Jonathan

---

### Post by nogoodnamesleft on 2011-01-29
if you download the ubuntu live CD the installer there has an option to trash the existing drive contents and start fresh

---

### Post by irv on 2011-01-29
It sounds like you have the HD set to boot first in your CMOS. When your computer starts to boot just hit the F2 key (I believe this is the key to get into the CMOS on the Dell 1505). Change the boot order to boot from the CD first.
Another way to do this is to just hit the F12 key at boot up and pick "boot from CD". Make sure you have the Ubuntu CD in the Drive and go through the install. Pick use the whole drive and it should install.

---

### Post by jdmarsh2g on 2011-01-29
Hey guys,
I guess you are speaking of the windows installer? (Please confirm will give it a try in the mean time)
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) 
I downloaded this Ubuntu version openSUSE-11.3-DVD-i586.iso nogoodnamesleft

I have the boot sequence set to the cd/dvd/cd-rw drive.
It sits for a while then goes into Windows XP Grande Half-n-Half

---

### Post by jdmarsh2g on 2011-01-29
oops my mistake this .iso ubuntu-10.10-desktop-i386.iso

---

### Post by nogoodnamesleft on 2011-01-29
No, this one

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

The main link there will give you the Ubuntu Live installer (which is also the main installer that most people use). You put that on a CD then boot up from that CD (not into windows). To do that, see what irv wrote above.

On the same page below it you can click "if you are running windows" to get WUBI (the windows installer), but WUBI works from inside windows so that won't help if windows is broken.

---

### Post by jdmarsh2g on 2011-01-29
Okay so I believe that is what I downloaded already the .iso file (trying again) ubuntu-10.10-desktop-i386.iso 693MB file 
1). Ubuntu 10.10 - Latest version 32-bit (recommended)
1). Chose CD
2). Chose Ubuntu

Now burning to a DVD+R.
Will try USB flash next if it still isn't picking up the .iso
Anything I'm missing or does that look good so far?

---

### Post by jdmarsh2g on 2011-01-29
Comes to a blank screen after reboot then goes right back to Windows XP where it left off as far as installation. The installation for XP was all the way up to where it was going to install Windows but I did not have the Product Key. The DVD light is still green.
Interesting :)

---

### Post by jdmarsh2g on 2011-01-30
Good Morning,
Last thing I tried was extracting the .iso file before burning it to cd. Burned all files to Cd instead of just having the .iso file sitting on the cd. Put cd into laptop and booted off the cdrom still just reads disc then boots up Windows XP.
What can I be missing here? 
Inspiron E1505.....
Any Suggestions...????

---

### Post by oldfred on 2011-01-30
It has to be an image copy that extracts the files and creates a bootable Cd, not a copy of the ISO or just copy of the files. You also want to burn at the slowest speed your drive allows. CDs seem to work better than DVDs. Is your system new enough to boot USB, if so then that is often easier.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by jdmarsh2g on 2011-01-30
This is perfect and much appreciated will read through all the documentation. 
The laptop has Boot Sequence Options:
1). CD/DVD/CD-RW Drive
2). Internal HDD
3). USB Storage Device
Onboard Nic ??? 

So yes I believe from the Boot Seq that the machine can boot off of an USB. Will obtain USB from Best Buy. 

Thank you so very much and will let you know of the progress.
Have already downloaded InfraRecorder.

---

### Post by oldfred on 2011-01-30
My desktop had many USB boot choices, none of which I could get to boot. I tested flash drive on portable & it booted without any  problems, so I knew it was a good install. Then later I still had flash plugged into desktop but was experimenting with which hard drive to boot from and there it was. It was not a USB device but a hard drive.

Long story short, check hard drive list if you have trouble finding USB device to boot.

---

### Post by jdmarsh2g on 2011-01-30
> **oldfred said:**
> My desktop had many USB boot choices, none of which I could get to boot. I tested flash drive on portable & it booted without any  problems, so I knew it was a good install. Then later I still had flash plugged into desktop but was experimenting with which hard drive to boot from and there it was. It was not a USB device but a hard drive.

Long story short, check hard drive list if you have trouble finding USB device to boot.

Success finally!
This is great and I really appreciate your help and everyones to get this OS installed. I ended up using a CD-R to get it to pick up the install. Used the InfraRecorder at the lowest burn rate. 
I have yet to start using the OS as I have other work to do but this an excellent start having the OS up and running thus far and able to connect to internet etc... 

a HUGE THANK YOU

---

### Post by jdmarsh2g on 2011-01-30
> **oldfred said:**
> My desktop had many USB boot choices, none of which I could get to boot. I tested flash drive on portable & it booted without any  problems, so I knew it was a good install. Then later I still had flash plugged into desktop but was experimenting with which hard drive to boot from and there it was. It was not a USB device but a hard drive.

Long story short, check hard drive list if you have trouble finding USB device to boot.

That is quite interesting as this will probably be tried in the near future when going with a Netbook or even possibly an Android / Linux based tablet. I'm learning just do not want to be tied to Microsoft.

---

### Post by nogoodnamesleft on 2011-02-01
> **jdmarsh2g said:**
> Good Morning,
Last thing I tried was extracting the .iso file before burning it to cd. Burned all files to Cd instead of just having the .iso file sitting on the cd. Put cd into laptop and booted off the cdrom still just reads disc then boots up Windows XP.
What can I be missing here? 
Inspiron E1505.....
Any Suggestions...????

What you do is take the ISO and burn the ISO to a CD. Burn the whole ISO, do not extract it. And I do not mean "copy the ISO file onto to a CD like it was a document". I mean use the "Burn Image" function of the CD creator program.

Then go into the BIOS on the laptop and set it to boot from CD ROM.

Then stick in the CD and reboot.

---

