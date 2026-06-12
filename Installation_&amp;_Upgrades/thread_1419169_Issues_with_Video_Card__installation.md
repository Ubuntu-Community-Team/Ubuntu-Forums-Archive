---
title: "Issues with Video Card / installation"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by MeNtuxRoKinU on 2010-03-01
So, I have been trying to install ubuntu on my Compaq Presario. The computer has a graphics card, and this is where my issues start. 

I tryed to install 9.10 on the computer, blank screen at install. 
I took the graphics card out, blank screen at install.

I tryed to install 8.04, blank screen at install.
I took the graphics card out, blank screen at install. 
I tryed to install in safe graphics mode, success! 
I put the graphics card back in. Unable to log in. 

Graphics card is Nvidia 8400 gs.
Celeron 2.44 single core
1gb ram
80,40 gig IDE hard drives, both set to cable select. 80g hard drive split into 2 equal partitions, with half Win XP installed, and half free space. Using the 40g for extra storage.

ARGH!!  Does anyone know anything about installing ubuntu with a graphics card installed? I want to use the graphics card, as I use it on my windows installation. Let me know if you need anymore info.

---

### Post by quixote on 2010-03-03
Try 9.10 with a safe graphics install option.  If it succeeds, it should detect your card and ask if you want to install special drivers.  If it doesn't ask, under System > Administration > Hardware Drivers, it should list drivers you can install.  (See, eg [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)).

If there are no drivers listed there, then you could try the command line way.  [Ubuntugeek]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") has instructions that work for karmic too.  The [Ubuntu docs]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") have info for Intrepid and earlier. (They need to catch up! :D)

---

### Post by MeNtuxRoKinU on 2010-03-03
Thanks, I think I am onto something. 

I wiped out the C: drive removing the partition, then wiped the D: drive out, and started all over. I reinstalled windows to C: and got that up and running. Then I created a primary partition in the D: drive and formatted NTFS. I then did a wubi install of 9.10 on the D: drive using 30g. The only way I could do this was to switch the video adapters in BIOS. I thought the install was ok until I rebooted and "poop". The ubuntu spalsh screen just kept blinking at me.

Back to the drawing board. 

I again wiped the D: drive, reformatted, and installed 8.04 on D: 30g. Again with the adapters switched in the bios. (By the way, this took a ******** of work switching the monitor and BIOS back and forth!). I was able to boot into ubuntu after the install and update the system. The system also prompted to install the 3rd party Nvidia driver, which I did. After all updates and the driver were installed, I rebooted, and OUCH!, computer prompted me to start up in safe graphics mode, and was unable to log in! This was about 1 in the morning, so I decided to shack it and restart tomorrow.

Thanks for the reply, and I'll keep up the play by play.

---

### Post by quixote on 2010-03-03
I don't have any experience with wubi installs.  I can't help thinking that might be a complicating factor.  Linux does not have to be installed on a primary partition.  So even if you're trying to keep the number of primaries down, you could make a 30GB logical ext3 or ext4 partition for ubuntu.  I have no idea if that would make any difference, and you may have reasons why you have to go the wubi route.  Anyway, something to think about perhaps.

---

### Post by Frogs Hair on 2010-03-03
Hi
I have an 8400GS and I had trouble with loosing monitor signal @ boot . After updating to the I.85 driver 
in hardware/ drivers It runs great. KK 9.10  64

---

### Post by MeNtuxRoKinU on 2010-03-08
SUCCESS!!! 

I had to step away from the situation and break it down, and with the help of this link, was able to "git er done"!!!

[http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/](http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/)

Best regards and Many thanks to Josh Carrier.

Ubuntu up and running!!!! Full Graphics enabled!!!

---

