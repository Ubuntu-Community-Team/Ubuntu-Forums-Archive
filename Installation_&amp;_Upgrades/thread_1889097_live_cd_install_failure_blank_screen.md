---
title: "live cd install failure blank screen"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by Comfort_fal on 2011-11-30
i recently bought a new computer, and have been trying to install linux on it, 11.10 x64. 

it is a HP pavilion dv6-6117dx.

2.4GHz/1.5GHz VISION A8 Technology from AMD with AMD Quad-Core A8-3500M Accelerated Processor


AMD Radeon HD 6620G Discrete-Class Graphics

preinstalled windows 7.

i am pretty sure i picked a unsupported graphics card or something.

i have tried booting from usb, and i have also tried "nomodeset' boot. 

any idea would be welcome.

---

### Post by Steve H on 2011-11-30
This may be a stupid question but are you sure that your system is 64bit?

---

### Post by Comfort_fal on 2011-11-30
i checked and yes it is x64, but i might be a good idea to try x32. i will see if that works

---

### Post by BC59 on 2011-11-30
I checked HP pavilion dv6-6117dx is 64bit.

Try to use the Live CD you are using not to install but to Try Ubuntu, to check if the system is working in your computer.

About the USB you are using, maybe is not well prepared. Unfortunately only a CD is working well for installations. USBs create problems and when you have to extract them, you have to shutdown the computer, safe eject is corrupting the files.

---

### Post by Comfort_fal on 2011-11-30
i have tried to use the "try Ubuntu" and it gives me a blank screen. 
i can get to command line, but thats all.
i am not sure if my computer is incompatiable, or just some mistake i am making is causing it not to work

---

### Post by BC59 on 2011-11-30
Well most probably is USB problem. Try to recreate it.

---

### Post by ajgreeny on 2011-11-30
What graphic card does that machine have.  There are big problems with some of the newer ATI cards and 11.10, and also some of the new nvidia optimus cards are causing problems which some users have solved with the bumblebee driver.

Search **bumblebee nvidia optimus** if you have one of those cards.

---

### Post by Comfort_fal on 2011-11-30
AMD Radeon HD 6620G
 
i was thinking that was the problem. 
I think it is a new one, or recently put out enough that there isn't support for it? 
I still haven't tried all the options, but that might be the answer.

---

### Post by MAFoElffen on 2011-12-01
> **Comfort_fal said:**
> AMD Radeon HD 6620G
 
i was thinking that was the problem. 
I think it is a new one, or recently put out enough that there isn't support for it? 
I still haven't tried all the options, but that might be the answer.
Use " radeon.modeset=0 " as a boot option. Then:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")[/SIZE][/COLOR][/SIZE][/COLOR]

Yes, it is supported... In fact the review on your card at Phoronix was on an Ubuntu box:[SIZE=2]
[/SIZE]**[SIZE=1][AMD Llano Graphics / Radeon HD 6620G On Linux]("http://www.phoronix.com/vr.php?view=16141")[/SIZE]**

---

### Post by Comfort_fal on 2011-12-01
thank you for the help, 

but i tried installing 11.04, and it seemed to recognize my graphics card. 
it allowed me to "try ubuntu" and had no other problems, beside the wireless not working, but that isn't related to the blank screen. if anyone is having blank screen trouble you might want to try using natty. 

thanks for the help.

ubuntu has the best community.

---

### Post by east_injun on 2011-12-09
I can concur with the above observation. I recently purchased an ASUS laptop which has AMD A6 processor with RADEON HD 6720G2 graphics card. It was working perfectly with ubuntu 11.04 Natty Narwhal (amd64 version). However when I tried to upgrade to 11.10 the graphical display stopped working. I could go into recovery mode and get a terminal but nothing I tried from the suggestions on thes forums fixed it. Thereafter I also tried to do a fresh installs of ubuntu 11.10 64bit  followed by 32bit but to no avail.
My conclusion is also that the graphics drivers and the new Linux kernel 3.x are not playing well together yet. I hope this can be sorted out in time so that those of us with AMD processors can also upgrade to 11.10.

---

### Post by jackharvest on 2012-01-23
When I plop in the 11.10 or 12, or 11.04, the result is the same: Black Screen when loading.

Using radeon.modeset=0 gets me at least to the "dots loading" screen, followed by a black and white login screen (just text). Using "startx" gets me Fatal Server Error: "no screens found".

:\ I wonder when it'll natively get supported... seeing as AMD is pushing this into almost all of it's laptops.

---

