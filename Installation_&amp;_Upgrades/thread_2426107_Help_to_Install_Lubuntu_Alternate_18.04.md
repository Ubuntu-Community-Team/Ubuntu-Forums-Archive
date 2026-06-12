---
title: "Help to Install Lubuntu Alternate 18.04"
date: 2019-09-04
forum: Installation &amp; Upgrades
---

### Post by lord.radel on 2019-09-04
Hello, through this publication I strongly urge you to help me solve installation problems for Lubuntu Alternate 18.04 on an old PC with the following features:

Machine: LENOVO - 8773DDS
Operating System: Windows 10 Home 32 Bits
RAM memory: 2GB
Processor: Intel Pentium 4 CPU 3.00 GHz
Main Board: LENOVO - GA-8S664FXM-775
Video Card: NVIDIA Geforce 6200 512 MB
Solid Disk: Kingston UV500 480GB SSD
Network Card: Realtek RTL8139 / 810x Family Fast Ethernet NIC

The problem lies in the fact that Lubuntu Alternate 18.04 of 64 and 32 Bis should not be installed on the Described PC, since opting on the startup list for ubuntu only has a dark screen.

It is worth mentioning that I have installed Windows 10 Home 32 Bits and I have left a free space that is half of the Solid Disk. It is in this half of free space that I install Lubuntu Alternate to which the problem described is presented.

I also mention that the starter grub is presented in the following way;

*Ubuntu
                     Opciones de Ubuntu
                  Windows 10 /dev/sda

This is correct since in a Video Tutorial it is presented in the following way;

Ubuntu With Linux ... Generic
Ubuntu With Linux ... Generic ( Mode Recovery )
Memory Test (memetest86+)
Memory Test (memetest86+, serial console ... )
Microsoft Windows XP Sp3 ( on /dev/sda1 )
    
I would like to know if Lubuntu Alternate is possible to install it in Spanish without the Internet, since I have not been able to install it. In Lubuntu Desktop 64 or 32 Bit I can not install it because of the Video Graphics Card that apparently is not compatible or tolerate.

Please help me with a tutorial to install Lubuntu Alternate with Internet and without Internet in Spanish language on the PC Described and shared with Windows 10.

I thank you in advance for your kind attention, help and prompt responses.

---

### Post by mörgæs on 2019-09-04
For Nvidia 6xxx graphics cards it's often necessary to select closed-source drivers as soon as possible during install. 

Does the alternate ISO offer this choice? Else try the standard ISO.

---

### Post by pcfan1234 on 2019-09-05
The proprietary nvidia driver for the 6 and 7 GeForce series isn't compatible with Ubuntu 18.04 anymore.
Use nouveau, maybe with nomodeset.

---

### Post by mörgæs on 2019-09-06
This was news to me. Thanks for posting.

---

### Post by pcfan1234 on 2019-09-07
To find that out go to nvidia's website an look for the driver. There you can see the latest driver that is available for such cards. Then check the Ubuntu repositories out for this driver (e.g. nvidia-304 nvidia-340). If the old version isn't included, you have no alternative to nouveau.

---

### Post by guiverc on 2019-09-07
[COLOR=#333333][FONT=Ubuntu]"if you need either full language support or ...., please use the [/FONT][/COLOR][server ISO]("http://www.ubuntu.com/download/alternative-downloads")[COLOR=#333333][FONT=Ubuntu]. "

says [/FONT][/COLOR][https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO) about the Lubuntu alternate ISO.  It then tells you how to add the `lubuntu-desktop` on to your system post-install.

The alternate 18.04 image hasn't been created since 18.04 (ie. no 18.04.1, 18.04.2, nor 18.04.3) thus older and is not what I'd recommend using. On your machine I don't understand why you're trying to use it (it has functionality disabled so as to reduce ram needed by installer).

---

### Post by pcfan1234 on 2019-09-07
What CPU do you exactly have?
Is it a x64 capable?
Some P4s on socket 775 have x64 extension.
Use CPU-Z under Windows and Post the full CPU info.
Maybe use the boot option nomodeset if the screen is black.

---

