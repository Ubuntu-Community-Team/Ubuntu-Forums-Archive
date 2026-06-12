---
title: "Can't boot from Kingston DataTraveler r3.0 usb 3.0 device"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by Darngood on 2013-03-07
Hello. I want to install the new ubuntu 13.04 on my asus zenbook ux32vd but I encounter a problem.
I have just bought a new usb 3.0 stick: Kingston DataTraveler r3.0 16GB. Then I created a bootable usb with the daily build of ubuntu 13.04. 
However, when I try to boot from the stick, a booting option from the stick doesn't show up. I have tested it on my desktop and it works ( boots into live CD ).

Is there any way I can make it work?
I'm thinking about bios update but since the stick is not recognized I don't know how I can do that... :(

Note: I have tried all 3 usb 3.0 ports.

UPDATE:

It finally worked but I can't figure out why exactly. I have installed usb 3.0 windows 7 drivers so the stick would be recognized, then rebooted and it worked when I inserted the stick in a specific usb 3.0 slot(left slot if some may encounter this problem)! I don't know what does installing win 7 usb 3.0 drives have to do with the detection of the usb stick in BIOS!!

However, there is another problem now. Booting in live usb is smooth, but after installation if I don't set nomodeset boot parameter I get a freezed pink screen when booting...
And with nomodeset the VESA drivers are used and the unity is really slow cause of this...

---

### Post by kurt18947 on 2013-03-07
Have you set the Asus boot order?  Does the BIOS check for USB hdd before booting from the internal hard drive?  I'm not familiar with this machine so don't know how to check/change the boot order.  Usually you either change something in BIOS setup or press a key early in the boot process to select a specific device to boot from.  I hope you don't have what I have on one machine.  I have 4 boxes of various vintage.  3 work perfectly with USB drives formatted to FAT32 using Gparted.  1 machine will give 'boot error' and stop.  For that machine, I *must* format the flash drive in Windows, then it boots fine.

---

### Post by Darngood on 2013-03-07
The problem is that it doesn't show up in the bios booting options. Also I can see that there's no blinking light on the usb stick when the laptop boots. I will try to format the stick again though. So far i have tried lilo, unetbootin, gtk-usb-creator, usb-imagecreator, and dd command from CLI in linux.

---

### Post by schragge on 2013-03-07
Hopefully [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) could be of some help.

---

### Post by oldfred on 2013-03-07
Does this system boot with UEFI?
It looks like an UltraBook which will also have issues with RAID as that is Intel SRT.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Intel is standard with all brands so this may be relevant
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by Darngood on 2013-03-07
This is how the bios looks: [http://www.youtube.com/watch?v=qEpoBfVPKHo](http://www.youtube.com/watch?v=qEpoBfVPKHo) . In the booting options i don't see anything when inserting the stick. 

I have tried to boot from an usb 2.0 sticks and it works...

---

### Post by oldfred on 2013-03-07
Turn off the Intel AntiTheft. I think that lock systems so you cannot boot anything else to prevent theft.

Someone posted this for UEFI boot.

---

### Post by Darngood on 2013-03-07
I've updated the 1st post.

---

### Post by oldfred on 2013-03-07
If these links do not help best to start a new thread on video issues, so those who know those may help.

You generally need the proprietary drivers if nVidia or AMD.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

And if dual video laptop you may need bumblebee. 
      
 Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

