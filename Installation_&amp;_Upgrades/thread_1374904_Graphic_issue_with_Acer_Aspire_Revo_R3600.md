---
title: "Graphic issue with Acer Aspire Revo R3600"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by waheedrafiq on 2010-01-07
I have install Ubuntu 9.10 on my Acer Aspire Revo R3600 system. the installation went fine ,my only issue is when I want to change the display setting in the display pannel to normal or extra it is grey out.

I have nvida graphic cards and don't understand why i can't use the best feature on this OS 


can someone point me to the right direction.

---

### Post by kansasnoob on 2010-01-07
Please post the output from terminal of:

```
lspci | grep VGA
```

```
xrandr
```

---

### Post by waheedrafiq on 2010-01-08
i will do this tonight thanks:popcorn:

---

### Post by waheedrafiq on 2010-01-09
infoseeker@infoseeker-desktop:~$ lspci | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
infoseeker@infoseeker-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
infoseeker@infoseeker-desktop:~$ 



the  above is my output , where do i need to go from here please 

many thanks for your support. :popcorn:

---

### Post by waheedrafiq on 2010-01-10
:( hi all just checking if there is any fix for the above issue please do help 

I think Linux can beat  iMac and Windows OS , with the correct support , I think all issues can be easily fix

---

### Post by tn812 on 2010-01-10
If you have Nvidia graffic card, I think you should install the Nvidia driver.  I had a lot of problems with booting up to ubuntu 9.10.  It usually hangs at the logo screen.  Then I tried the recovery mode and it listed unknown card....could not find driver, etc.  Anyway, some reading and install Nvidia driver.

Here's how: System/Administration/Hardware Driver.  You'll see the Nvidia driver is not activated (propriety thing).  Activate it and restart.

I don't know if I've solved my bootup problems, but so far it hasn't hanged yet after 3 restarts.  But it'll definitely fix the flickering problem if you experience that too.

good luck.  I'm very new to linux too, but liking it more and more....would be too bad if I/we could not smooth out these problems.

---

### Post by waheedrafiq on 2010-01-11
yes can't believe you have fix it for me the { System/Administration/Hardware Driver. You'll see the Nvidia driver is not activated (propriety thing). Activate it and restart.} 

The above did the job 

many thanks and I owe you one :):D

---

### Post by Kevbert on 2010-01-12
Had a similar problem with a R3610. Check what driver you are using. The default driver did not show up under Hardware Drivers, so I had to install the nvidia-glx-180 driver through Synaptic. Logged out and then back in again and everything was fixed.

---

### Post by hughesey on 2010-01-24
hi peeps, i cant seem to sort this out for me - any idea's - i've installed the propietry drivers thing - thru' system/adminstration- which went well and sorted the hdmi sound issue i had - but i'm not satisfied at all with the screen resolution - its set at 1280x720 or something - i know from the htpc i had before the screen res at 1360x768 was perfect and i cant seem to get this revo to go to that - any idea's?????

---

### Post by waheedrafiq on 2010-01-24
I know I am newbie like yourself but have you double check that you have downloaded the right drivers and also have you perform your hardware check to make sure the graphic cards is working fine.

---

### Post by hughesey on 2010-01-25
i've manually downloaded the drivers, but never used them, i let the sympatic.... thingy sort it for me - 180.53 - i think it was? going to try another distro instead of ubuntu, see if i have any other joy with that.   will keep my eye on this thread incase someone finds a fix.
cheers again peeps...much thanks.x

---

### Post by waheedrafiq on 2010-01-26
Never give up on Ubuntu , its the best distro  out there ,and the most userfriendly , I think you will find that as newbie there are new way of installing drivers,  I will do some research into installing hardware / drivers for unbuntu.

I hope someone can help you here.

---

### Post by st0kes on 2010-04-27
Sorry to revive a dead thread but I just wanted to ask how you even installed Ubuntu on the R3600? My installation of Ubuntu Lucid will not boot. I get about 2 inches of mess at the top of the screen and then the boot process just hangs. I can't get to the other virtual terminals on ctrl+alt+F-keys either. 

I can boot off the live cd and while I'm in a live session it seems to work ok. I can chroot to my dodgy installation and access the file system ... anyone know what is the best way forward from here though?

---

