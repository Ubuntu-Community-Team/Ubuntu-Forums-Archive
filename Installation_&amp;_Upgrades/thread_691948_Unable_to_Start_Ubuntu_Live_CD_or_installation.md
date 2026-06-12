---
title: "Unable to Start Ubuntu Live CD or installation"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by Anish_M on 2008-02-09
Hi Guys,

I am new to Ubuntu and Linux altogether. Trying to install Ubuntu for the first time using the 7.10 32 Bit CD. I have Vista installed on 2 drives. On C drive its a 64 Bit Vista and on the D drive its 32 Bit.
Below are the steps i have performed and the issues that am facing :

1. Booted the CD > Can see the Ubuntu boot menu.
2. Selected the first option Start or Install Ubuntu.
3. It shows : Loading linux Kernel 100%
4. I see a Blank screen for about 2-3 mins, when i did it for the 2nd time i actually saw the loading bar rolling sideways, then the normal loading begins.
5. Then i get a mouse pointer, it again stays there for a couple of mins
6. Then comes the low resolution warning. (using 8800GT).
7. I tried installing the GeForce 8 series drivers from the same warning.
8. I clicked on OK.
9. now the main part :( : It shows the following script and stays there forever.

* starting deferred execution scheduler atd    [OK]
* starting periodic command scheduler crond   [OK]
* checking battery state...                               [OK]
* running local boot script (etc/rc.local)            [OK]


Thats it ... I would really appreciate if any one could help me out in this .. 

System configuration : 
Intel E6300 OC'ed @ 2.ghz
Corsair 2 GHz 6400 
8800GT MSI OC edition
XFX 650i Ultra motherboard
250+160GB WD & Hitachi HDD

Thanks,
Anish 
Pointsec Lead Infrastructure Engineer.

---

### Post by Partyboi2 on 2008-02-09
when you get to where it stops press Ctrl+Alt+F2
this will get you to a terminal then type this command
```
sudo dpkg-reconfigure xserver-xorg
``` choose nv for the driver and answer all the questions, if unsure just choose the default answers.
when finished type
```
startx
``` If nv does not work try with vesa.
Hopefully this will allow you to install ubuntu. Then after it is installed you will need to install the restricted nvidia drivers to fix the graphics problems.
If none of the above work then use the [alternate cd]("http://releases.ubuntu.com/releases/7.10/") then install the nvidia drivers.
See [post #4]("http://ubuntuforums.org/showthread.php?t=687120") on how to install the nvidia drivers after you have ubuntu installed

---

### Post by Anish_M on 2008-02-10
Hey that worked!!.. But only thing i had to do after putting 'startx' command was to press CTRL+ALT+F10 (wht does this mean anyway?) and that showed the live CD with the install button on the deskop. I have another query.. why is the refresh rate stuck at 85/86 or 61 Mhz with some resolutions? .. Do i have to install the NV drivers ?

---

### Post by Partyboi2 on 2008-02-10
> Do i have to install the NV drivers ?That link to post #4 will install the correct drivers for your graphic card. So when you get to this part 
> dpkg-reconfigure xserver-xorg choose the nvidia driver.

---

### Post by TwoPly on 2008-02-10
Thanks a ton for your help PartyBoi2, I was having the same problem as the OP and this cleared it right up.

---

