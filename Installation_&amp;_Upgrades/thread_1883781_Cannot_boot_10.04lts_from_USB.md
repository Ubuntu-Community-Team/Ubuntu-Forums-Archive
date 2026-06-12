---
title: "Cannot boot 10.04lts from USB"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by davidshelton on 2011-11-19
I have tried with disc creator twice to make a bootable usb with the image file for ubuntu 10.04LTS but all I get is  some credits to Alvin someone or other and then this message directly below :
**unknown keyword in configuration file : gfxboot **

Then I get the following repeated constantly: 

[B]vesamenu.c32 : not a CDM32R image 
boot :
vesamenu.c32 : not a CDM32R image 
boot: [/B]
 

...and so on. I did md5checksum on the iso file. All good there. Tried with disc creator and the other usb disc creator from the software centre with the exactly same result. It's corrupted or something needs to be corrected. How?  What can I do to fix it? I couldn't find any matches to that message neither with google nor on the forums....

[COLOR=Red]**PLEASE NOTE : my system is a Toshiba laptop(c655-6001L)  running celeron and intel onboard graphics and ubuntu 11.10(way too slow!)**[/COLOR]

---

### Post by raja.genupula on 2011-11-20
look at post number 10
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by davidshelton on 2011-11-20
Ok. Thanks for the response. So I tried that line of code in the terminal and to no avail. Just says /dev/sdb1 is invalid directory. Other combinations including my USB stick name don't work either. So I tried the work arounds mentioned. Tab got me past that annoying bug to the next annoying bug whereby it says it is unable to find live file system on the media or words to that effect. Why does creating a bootable usb have to be such a hassle? I'm trying to roll back to 10.04lts because performance is terribly slow at times with 11.10. Sometimes DVD's are unviewable because of choppy slowness. I hate to say it but Windows 7 worked very well and was way faster on my puny little toshiba. (Celeron with Intel onboard graphics = very puny). 
Any ideas before I sell my laptop and get a Mac? I'm at the end of my tether here but don't really want to give up on Ubuntu just yet...

---

### Post by davidshelton on 2011-11-20
**(initramfs) unable to find a medium containing a live file system**

This is the error I am getting now.... any ideas?

---

### Post by davidshelton on 2011-11-20
....so I've tried messing around with the syslinux.cfg file inputing copying and pasting code from other threads. Could this be the way to solve it? What is the correct code for this file?

---

### Post by davidshelton on 2011-11-20
......sooooooooo tried to make a new bootable usb with unetbootin. No go! Get's stuck at a blue screen where only option is default and the 10 second countdown keeps resetting. I can get to a dos prompt by pressing escape but then I have no clue what to do... giving up for today!

---

