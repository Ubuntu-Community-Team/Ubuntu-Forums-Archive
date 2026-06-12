---
title: "How to enable accelerated graphics in Ubuntu v7.04"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by system366 on 2007-05-22
Hio all

Ok... basicly i want to enable accelerated graphics in Ubuntu v7.04

But i have no idea where to start im very new to Linux

Could someone please help me get it all up and running? But be sure to talk simple talk coz i have no idea what todo XD

My GFX card is Nvidia geforce 2 Ultra

Thx in advance

-Nick-

---

### Post by hardyn on 2007-05-22
you will want to install the nvidia-legacy package though synaptic... im sure there are many howto's on the forum.

---

### Post by system366 on 2007-05-22
i just did an "Aptitude search nvidia" to see if it had it there since u said its a package

It has :

system366@Ubuntu-7:~$ aptitude search nvidia
p   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
p   nvidia-glx-new-dev              - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.9631          -                                           
v   nvidia-kernel-1.0.9755          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-legacy-kernel-source     - NVIDIA binary 'legacy' kernel module sourc
p   nvidia-new-kernel-source        - NVIDIA binary 'new' kernel module source  
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool     


Are any of these what i need?

---

### Post by system366 on 2007-05-22
is it this?

p nvidia-kernel-source - NVIDIA binary kernel module source 

Or is it much more complex than just installing sumthing from an "aptitude search"? XD

---

### Post by luctor on 2007-05-22
the package is called

nvidia-glx-legacy

---

### Post by system366 on 2007-05-22
ooo... okays so i need to install the

p nvidia-glx-legacy - NVIDIA binary XFree86 4.x/X.Org 'legacy' d

from the aptitude search i did?

---

### Post by system366 on 2007-05-22
ok... i installed the package above... but wht do i do now? i have no idea... i believe i have to do sumthing with sum sort of Xorg.conf???

---

### Post by hardyn on 2007-05-22
it should have done it all by its' self, but crack open the xorg.conf file, and see what you are using for the driver

gedit /etc/X11/xorg.conf

and look for "Driver"

---

### Post by bigken on 2007-05-23
you could use [envy ]("http://www.albertomilone.com/projects.html")this will do it all for you

---

### Post by system366 on 2007-05-23
Envy is ONLY for Dapper and Edgy??? i am using Fiesty

Me and my half bro did the Xorg.Conf

The driver was still "nv" so he told me to set it to "Nvidia" which i did

We also commented out the

Load "dri"

From the "mode" thingy or sumthing... after this when i tried to "startx" it showed the Nvidia logo for about half a second then it gave errors saying something lyk fatal error, and could not load screen or sumthing...

Any ideas of what todo?

We also tried commenting out the last 3 lines cant remember what they wer but it had a number at end of middle line which was 0666... It still didnt work so i set everything back to normal and it still wouldnt let me startx... so i rebooted and then it let me... should i try reinstalling the driver and reconfiguring the xorg.conf file then restart the computer? (Last time i didnt restart after installing and editing Xorg)... Also the legacy driver did nothing but the glx-new driver worked but i couldnt change the resolution... it only gave me 800x600 and a smaller one...

---

### Post by bigken on 2007-05-23
sorry to disagree but it does work in feisty

I run 2 laptops 1 a ati which works out of the box the other runs xp so it dont matter 

and 3 work stations all with variations of nvidia cards running feisty and used envy to install the drivers without any probs

---

### Post by system366 on 2007-05-23
Awsome! thx for the info guys! ima try this Envy out in a few mins =D

---

### Post by system366 on 2007-05-26
Hio guys... ok i tried the Envy thing and it went through it all didnt show any errors... then it rebooted the computer and it wouldnt Start X it gave an error sumthing about x server not able to start or summin... so yeh... i put the Xorg.conf backup in and restarted n back to normal now... any other ideas on how i can do this?

---

