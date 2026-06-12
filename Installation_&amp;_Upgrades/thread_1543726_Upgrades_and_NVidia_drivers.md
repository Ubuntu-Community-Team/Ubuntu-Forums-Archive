---
title: "Upgrades and NVidia drivers"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-08-01
So how does this work? Apparently the new 10.04 distros, Mint or Ubuntu and friends simply flat out wont work with certain newer video cards or monitors or whatever....This is a major obstacle.


So I can get an older version to work, but then when I upgrade is the screen going to go blank again?


The other solution I thought of is installing from USB.....but is that going to work? Can I create a USB image installation with the drivers already installed.....I mean, can I create a USB drive installation, add the Nvidia drivers, then install it to another PC so that the Nvidia drivers are also installed? Otherwise the screen will go blank again.



On a different thread I was given some advice that I didnt know how to follow involving f6 and some modes that did not appear on the boot loader for linux mint 8.

---

### Post by gnwiii on 2010-08-01
> **Nick_Jinn said:**
> So how does this work? Apparently the new 10.04 distros, Mint or Ubuntu and friends simply flat out wont work with certain newer video cards or monitors or whatever....This is a major obstacle.

So I can get an older version to work, but then when I upgrade is the screen going to go blank again?

The other solution I thought of is installing from USB.....but is that going to work? Can I create a USB image installation with the drivers already installed.....I mean, can I create a USB drive installation, add the Nvidia drivers, then install it to another PC so that the Nvidia drivers are also installed? Otherwise the screen will go blank again.

On a different thread I was given some advice that I didnt know how to follow involving f6 and some modes that did not appear on the boot loader for linux mint 8.

Hardware that is newer than the distro will always present some problems.  The basic strategy is to arrange to install without using
the unsupported hardware and then upgrade to a version (drivers, kernel) that supports the hardware.   In the case of newer graphics hardware, 
install from the normal media using text mode or the VESA driver, then install current drivers to get support for your hardware.

---

### Post by Nick_Jinn on 2010-08-01
I doubt this PC is newer than the latest Ubuntu release. Its at least a year old... Also, OLDER versions of Ubuntu install on this PC but not newer ones. Thats a problem.


So I can install the previous stable release of Ubuntu, but is it going to go blank again when I upgrade? Do I have to reinstall the drivers again?



What if I dont install the drivers from the repository? What if I install with WINE or some other way? Will that help keep the drivers from being lost?

How can I install the OS so that that I have the latest version without the screen going blank? Karmic works but lucid doesnt, on this paticular PC.

---

### Post by Cavsfan on 2010-08-01
> **Nick_Jinn said:**
> So how does this work? Apparently the new 10.04 distros, Mint or Ubuntu and friends simply flat out wont work with certain newer video cards or monitors or whatever....This is a major obstacle.


So I can get an older version to work, but then when I upgrade is the screen going to go blank again?


The other solution I thought of is installing from USB.....but is that going to work? Can I create a USB image installation with the drivers already installed.....I mean, can I create a USB drive installation, add the Nvidia drivers, then install it to another PC so that the Nvidia drivers are also installed? Otherwise the screen will go blank again.


On a different thread I was given some advice that I didnt know how to follow involving f6 and some modes that did not appear on the boot loader for linux mint 8.

Are you using Lucid? There are good drivers for nvidia. I have a nvicia 9800 GT and the recommended driver works excellently.

---

### Post by Nick_Jinn on 2010-08-01
Did you read the OP?

I get a totally blank screen. I cant do or install anything. Nothing shows up on the monitor. I cant even fix the system if nothing is visible. I have nothing to work with.

---

### Post by Cavsfan on 2010-08-02
> **Nick_Jinn said:**
> Did you read the OP?

I get a totally blank screen. I cant do or install anything. Nothing shows up on the monitor. I cant even fix the system if nothing is visible. I have nothing to work with.

Guess you need more help than I can offer... I thought it was just a nvidia driver problem.
You failed to mention what nvidia card you have other than "NVidia Geforce 768mb dedicated"...

---

### Post by Nick_Jinn on 2010-08-02
Thanks for trying. Yeah, this was a 6150 series. It had some letters after it.

The work around that I came up with involved plugging the hard drive into my other PC (The one in my sig) and updating it from there, and once it was installed it was able to trouble shoot on the other PC in graphical mode....it was a real pain too because I couldnt get the last bolts out of the HD as the back of the case wasnt meant to come off like I expected, so I had to sit it next to my PC and run the cables across.....So I installed it and it was able to fix itself once it was properly installed on the other PC.

---

### Post by Cavsfan on 2010-08-02
> **Nick_Jinn said:**
> Thanks for trying. Yeah, this was a 6150 series. It had some letters after it.

The work around that I came up with involved plugging the hard drive into my other PC (The one in my sig) and updating it from there, and once it was installed it was able to trouble shoot on the other PC in graphical mode....it was a real pain too because I couldnt get the last bolts out of the HD as the back of the case wasnt meant to come off like I expected, so I had to sit it next to my PC and run the cables across.....So I installed it and it was able to fix itself once it was properly installed on the other PC.


Glad you got it working! :D

---

