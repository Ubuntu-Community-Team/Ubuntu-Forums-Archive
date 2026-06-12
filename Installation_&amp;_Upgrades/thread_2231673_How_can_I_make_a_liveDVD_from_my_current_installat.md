---
title: "How can I make a liveDVD from my current installation?"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by awsedrfedcfrvg on 2014-06-27
How can I make a liveDVD from my current installation?

I have win7 on sda1, and Ubuntu 12.10 on sda5, swap sda6.


I install more software to Ubuntu, add bookmarks in Firefox, Crome, etc.
Make Thunderbird perfectly for my need.
I add data to my home folder, setup desktop to look how I like it.


Basically, I have everyhing setup, with best software and data I need in that software.


How can I make a liveDVD from my current installation so I can install it on another machine or in Virtualbox?


Remastersys is not supported anymore and I don't know how do this with Clonezilla (clone one partition and setup in Virualbox)?


Any other way/software to do this?

---

### Post by mastablasta on 2014-06-27
re-linux and the new "remastersys": [http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/)

for virtualbox use you just need to create an image (various tools can do that) and then you just load the image no need to install.

---

### Post by monkeybrain20122 on 2014-06-27
> **awsedrfedcfrvg said:**
> How can I make a liveDVD from my current installation?


Basically, I have everyhing setup, with best software and data I need in that software.


How can I make a liveDVD from my current installation so I can install it on another machine or in Virtualbox?



I am sorry to hear that, as Ubuntu 12.10 has reached end of life back in April. If it were a supported OS I would recommend cloning your installation with fsarchiver and simply restore it to a different machine. In this case I think you should save your data and wipe out 12.10 and do a fresh install of 14.04. To make your next upgrade experience less traumatic I would suggest a separate /home as well.

---

### Post by awsedrfedcfrvg on 2014-06-27
> **mastablasta said:**
> for virtualbox use you just need to create an image (various tools can do that) and then you just load the image no need to install.

What tools can do that?

I try with clonezilla and can NOT restore just ubuntu partition. I don't know why. I can backup just ubuntu partiton, but when I try to restore in virtualbox it doesn't work.

---

### Post by yancek on 2014-06-27
You could try reading the man pages for mkisofs or genisoimage or google it to get some background on using it to create an iso file of your Ubuntu partition.  Although remastersys has not been supported for some time, I used it successfully on Ubuntu 12.04.  Don't know if it will work on 12.10 but since it is no longer supported, probably not a good idea anyway.

---

### Post by awsedrfedcfrvg on 2014-06-28
I manage to install Remastersys, [http://remastersys.com/](http://remastersys.com/)

#Remastersys Quantal
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) quantal main


Remastersys start and I click Backup. After 20 minutes I can see new folder /home/remastersys/. but can not find .iso?


I follow this tutorial [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)
No .iso in /mnt/.


Do I need to do something else?

---

### Post by yancek on 2014-06-28
As I recall, it should be in the /home/remastersys directory and the default name is "custom.iso" unless you changed it manually to something else.

---

### Post by awsedrfedcfrvg on 2014-06-28
No. iso anywhere.

From log, what does it means?


"Cleaning up the install icon from the user desktops
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Removing remastersys-firstboot from system startup
The filesystem.squashfs filesystem is missing.  Either there was a problem creating the compressed filesystem or you are trying to run sudo remastersys dist iso before sudo remastersys dist cdfs" 


Btw, I'm linux newbie, so...

---

### Post by yancek on 2014-06-28
> The filesystem.squashfs filesystem is missing.  Either there was a  problem creating the compressed filesystem or you are trying to run sudo  remastersys dist iso before sudo remastersys dist cdfs" 


The filesystem.squashfs wasn't created.  The second sentence gives a possible resolution.  I've always used the dist option and not the backup so can't really advise you.

---

### Post by yancek on 2014-06-28
> The filesystem.squashfs filesystem is missing.  Either there was a  problem creating the compressed filesystem or you are trying to run sudo  remastersys dist iso before sudo remastersys dist cdfs" 


The filesystem.squashfs wasn't created.  The second sentence gives a possible resolution.  I've always used the dist option and not the backup so can't really advise you.
Another program which you could use is grubmkrescue.  Unfortunatelly, it won't work from an installed system the way remastersys does.  You would need a second installation of Ubuntu on another partition.  Might work from a Live DVD but I've never tried that.

---

### Post by awsedrfedcfrvg on 2014-06-29
Does "dist option" keep programs settings, like firefox settings, firefox bookmarks, skype settings, thunderbirdet settings, etc?

I try "dist option" and get .iso, but can not run that iso in virtualbox.
What is problem here?

---

### Post by yancek on 2014-06-29
> Does "dist option" keep programs settings, like firefox settings,  firefox bookmarks, skype settings, thunderbirdet settings, etc?

No.  It keeps nothing from any user /home directory.   

What happens when you try booting from VirtualBox, black screen, error messages?

---

### Post by awsedrfedcfrvg on 2014-06-29
[COLOR=#000000][FONT=Ubuntubeta]Just black screen.

[/FONT][/COLOR] What is max GB for remastersys to make iso?

Is it possible build more than 4.7 GB (DVD size)?


Maybe I need to setup that somewhere?

---

### Post by awsedrfedcfrvg on 2014-06-30
How to remove ATI open source driver?


Is it possible to run system without GPU card like ATI/AMD?


I read that remastersys can work if GPU driver are gone.

---

### Post by yancek on 2014-06-30
> [COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR] What is max GB for remastersys to make iso?

According to the post below, it is 4GB.  Post #3 at the link below by fragadelic who is the developer of remastersys.  Sorry, I don't have an answer to your other questions. 

[http://www.remastersys.com/forums/index.php?topic=2092.0](http://www.remastersys.com/forums/index.php?topic=2092.0)

---

### Post by awsedrfedcfrvg on 2014-06-30
Thanks about iso size!!!

Anyone know how to remove opensource ATI driver and do not install any other driver?

---

### Post by mastablasta on 2014-07-01
> **awsedrfedcfrvg said:**
> 
Anyone know how to remove opensource ATI driver and do not install any other driver?

Opensource drivers are part of kernel. you can compile your own modified kernel and throw out the drivers you don't want. but why would you do that? they are loaded and used only if you have AMD/ATI card. aside from these there are also intel and nVidia opensource GPU drivers already included. and a few others as well. furthermore getting rid of certain drivers means the live CD Will work only on one or PC with certain components.



not install any other driver? how will you run an OS then? software uses drivers to communicate with hardware. no drivers and all you have is disk data that can't even be read...

no GPU drivers? then you will have text interface only. there would still be some basic vesa drivers used in text mode...

---

