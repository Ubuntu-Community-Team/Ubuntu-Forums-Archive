---
title: "xgl, compiz"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by benndamann33 on 2006-11-16
This new compiz thing looks amazing. Is it hard to install? what is xgl exactly? And also, if I have a dell latitude D610 with standard video card - will this not be enough?

---

### Post by John.Michael.Kane on 2006-11-16
Heres all the links with info 
[**HOWTO: Beryl with latest nvidia drivers and EDGY's built in AIGLX (no XGL)**]("http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl")

[**Guide for ATI or Nvidia**]("http://doc.gwos.org/index.php/BerylOnEdgy")

[**beryl + ati**]("http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7")

dell latitude D610 comes with a (RADEON X300) acording to the spec's I found. which should work out just fine.

---

### Post by benndamann33 on 2006-11-16
is it necessary to go through the nvideo driver installation or is that just for installing a new video card?

---

### Post by benndamann33 on 2006-11-17
I ended up not messing with my video card. It seems to work fine except the message "splash effect" cannot load or something along those lines. Any ideas? Also - is there a command or keystroke to manually rotate cube?

---

### Post by benndamann33 on 2006-11-17
Hi, I was pretty sure there was a way to view a 3d cube with beryl unless i'm thinking of something else. If it is beryl, what command runs this??
Thank you

---

### Post by John.Michael.Kane on 2006-11-17
benndamann33 make sure your using the right guide for your hardware.

to start beryl 

open terminal and type

beryl-manager

you should see a red icon in your task bar click on it to make any other adjustments

---

### Post by benndamann33 on 2006-11-17
I can't get my xconf to work with the raedon configuration.  just typing beryl-manager results in a lot of errors. Typing beryl-manager followed by beryl gets the program to run perfectly - oddly enough...unless there's some additionaly splash effect i'm missing out on

---

### Post by John.Michael.Kane on 2006-11-17
Which guide did you use. are you doing this on dapper or edgy?

Also your ati card is supported.

---

### Post by benndamann33 on 2006-11-17
beryl + ati guide
I used that guide. Also, I set up xconf as instructed but x would not start so I reverted ot backed up version, which simply used default configuration - so I didn't follow the instructions perfectly, but they were not working with my video card.

---

### Post by benndamann33 on 2006-11-17
Edit the device section in your xorg.conf to be like this
Section "Device"
Identifier "{your card model}" <-do not edit this line in your xorg.conf
Driver "radeon"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
Option "AGPFastWrite" "on"
EndSection


this is the setup recommedned. i'm a little curious as to why it says you shouldn't edit the identifier because the itdentifier is intel corporation mobile 915GM/GMS/9211GML Express Graphics Controller - which is inaccurate, is it not?

---

### Post by benndamann33 on 2006-11-17
sorry for so many messages - last thing - I'm using edgy.

---

### Post by John.Michael.Kane on 2006-11-17
benndamann33 if your xorg is reading your video card as an intel then the specs i read was wrong. you will need to use a guide for intel which there are two listed here one for dapper and one for edgy
[http://ubuntuforums.org/showthread.php?t=267232&highlight=beryl+intel+915](http://ubuntuforums.org/showthread.php?t=267232&highlight=beryl+intel+915)

Being that your setup is intel based I would post any futher issues in the thread I posted since most of those users have the same video card as you.

---

