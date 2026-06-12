---
title: "Trying to install"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by kkeller87 on 2012-07-01
Hello, 

Im trying to install ubuntu on my desktop to dual boot with windows. Ive done this before on this same computer. Ive tried booting from a live cd, installing on my external HDD and installing on my main C:\ drive that windows is on. Every time I try to boot into Ubuntu I get the purple loading screen with the orange dots. Then this 

[http://www.imgur.com/iZpdB.jpg](http://www.imgur.com/iZpdB.jpg)

Does anyone have any ideas?
Edit 

I tried an older live cd from a previous installation. It booted fine. Something must have been wrong with my new cd.

---

### Post by Frogs Hair on 2012-07-01
Hello and Welcome

There are a couple things to investigate . First is check the disk quality.[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Provide some information about your system specs in particular the graphics card or chip.  I think the screen capture is an extremely distorted login screen , which leads me to suspect a graphics card/chip problem.  The 12.04 login screen has a dot grid , but the dots are much smaller and don't  run at an angle.

---

### Post by kkeller87 on 2012-07-01
Thanks for the info. Currently in the middle of installing through means of an older version of ubuntu. For some reason that's working. Would I be able to get to the newest update once I'm up and running? I can get you some info on my pc soon.

---

### Post by kkeller87 on 2012-07-01
So after trying to use my live CD from 10.10 I went through the install and got to what you say is supposed to be the login screen for ubuntu. This isnt making sense to me because i have had 10.10 installed on this computer before, and havent changed any of the hardware.

 Im running an acer aspire desktop with an AMD Athlon 64 X2 dual core 4400+ 2.30GHz and the graphics card is an NVIDIA GeForce 6100 nForce 405.

I just checked the iso i downloaded for 12.04 was for i386, I dont know why I got that one when I clicked the link here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

But either way, my disc for 10.10 got me through the install, but couldnt display the login screen. But i have had this one working before. 

EDIT

looking through the md5 hashes i see there is no 10.10. I must have wrote it wrong with the sharpie. 


Thoughts from here?

---

### Post by Frogs Hair on 2012-07-01
There have been problems reported with that graphics chip/card on 12.04. I would suggest searching the forums for threads.

---

### Post by critin on 2012-07-01
The link downloads 32 bit by default.  You have to change the radio button for 64 bit.

---

### Post by kkeller87 on 2012-07-01
> **Frogs Hair said:**
> There have been problems reported with that graphics chip/card on 12.04. I would suggest searching the forums for threads.

Any thoughts on why 10.04 won't work anymore?

---

### Post by kjmitch on 2012-07-01
I'm having issues getting the live cd to boot as well. I get to the ubuntu splash screen "Try Ubuntu, Install Ubuntu etc etc" but am unable to get any further even with noapic, nolapic and nomodeset enabled.  I get to a black screen with a white cursor in the top left hand corner and get call stacks repeatedly. Recovery mode would probably allow me to get in, install and download graphics drivers, but I can't access recovery mode. Pressing shift continuously during bootup gets me nothing but sore fingers. Any suggestioins?

I have a quadro 4000/ tesla c2075 and an asus workstation board. If you need any other details let me know.

---

### Post by black veils on 2012-07-02
> **kjmitch said:**
>  Recovery mode would probably allow me to get in, install and download graphics drivers, but I can't access recovery mode. Pressing shift continuously during bootup gets me nothing but sore fingers. Any suggestioins?


you have to press and hold the Shift key

---

