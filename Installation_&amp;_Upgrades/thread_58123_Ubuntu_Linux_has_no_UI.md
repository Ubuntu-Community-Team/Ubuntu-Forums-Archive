---
title: "Ubuntu Linux has no UI?????"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by 0vermind on 2005-08-18
I don't know if this is the right place or not, anyway.

I tried installing Ubuntu Linux the normal way (default). It's just a commandline I'm disapointed, I was hoping for what I previed on the Live CD. I'm wondering if this is what it is or am I doing somthing wrong?

I tried all three installations: server, expert, and default. There all the same but install differently, I don't understand :-?!! If this is all the OS is then that is screwed up!! The live CD has nice slick UI and the real OS sucks? This does not make any sence. 

[FONT=Arial][SIZE=5][COLOR=DeepSkyBlue]Could someone please help me???[/COLOR][/SIZE][/FONT]

Thanks in advance,
0vermind

---

### Post by Velox Letum on 2005-08-18
[QUOTE=0vermind]I don't know if this is the right place or not, anyway.

I tried installing Ubuntu Linux the normal way (default). It's just a commandline I'm disapointed, I was hoping for what I previed on the Live CD. I'm wondering if this is what it is or am I doing somthing wrong?

I tried all three installations: server, expert, and default. There all the same but install differently, I don't understand :-?!! If this is all the OS is then that is screwed up!! The live CD has nice slick UI and the real OS sucks? This does not make any sence. 

[FONT=Arial][SIZE=5][COLOR=DeepSkyBlue]Could someone please help me???[/COLOR][/SIZE][/FONT]

Thanks in advance,
0vermind[/QUOTE]
 This will provide little support, but the install disk does indeed have X and GNOME (or KDE if using Kubuntu). The differences in installations is usually the packages installed...servers would (probably) lack a UI, and instead install GCC and such.

The problem could lie in your X config, and could be crashing upon startup, resulting in the command line view being presented in lieu of a graphical interface.

---

### Post by 0vermind on 2005-08-18
What would be the solution then??

---

### Post by 0vermind on 2005-08-18
Please, if anyone can give me some ideas as to what to do for this problem or just one idea would be great.  :) 

Thanks in advance,
0vermind

---

### Post by codejunkie on 2005-08-18
[QUOTE=0vermind]Please, if anyone can give me some ideas as to what to do for this problem or just one idea would be great.  :) 

Thanks in advance,
0vermind[/QUOTE]
if you do a server install it does not include a gui by default, but since you said at first you did a default install its most likely a video card problem that your having so if you could post a little info like what kind of videocard you have, and do you also have onboard video, what version of ubuntu you are trying to install x86, ppc, athlon64 what kind of pc you have would help.

---

### Post by Velox Letum on 2005-08-19
[QUOTE=codejunkie]if you do a server install it does not include a gui by default, but since you said at first you did a default install its most likely a video card problem that your having so if you could post a little info like what kind of videocard you have, and do you also have onboard video, what version of ubuntu you are trying to install x86, ppc, athlon64 what kind of pc you have would help.[/QUOTE]
 Some graphics cards don't like the default drivers, therefore a list of your target system would be nice, the graphics card especially.

---

### Post by 0vermind on 2005-08-19
K, I'll try to explain about my system the best I can!  ;-) 

------------------------------------------------------------------------------------------------------
            Ubuntu Version: 5.04 x86
                   Video Card: Intel Corporation 810 Graphics Controller Hub
                System Type: x86-Based PC
First Operating System: Microsoft Windows 2000 Professional

                                         --GRAPHICS--
             **Graphics Card is bulit into the mother board**

Name: Intel Corporation 810 Graphics Controller Hub
PNP Device ID: PCI\VEN_8086&DEV_7121&SUBSYS_43418086&REV_02\3&61AAA01&0&08
          Adapter Type: Intel810, Intel Corporation compatible
Adapter Description: Intel Corporation 810 Graphics Controller Hub
     Installed Drivers: i81xdnt5.dll
         Driver Version: 5.11.01.0133.3-NT5 Eng. Sample 03:01AM 
                    INF File: i81xnt5.inf (i81x section)
            Color Planes: 1
  Color Table Entries: 65536
               Resolution: 800 x 600 x 60 hertz [Note-Changable]
                 Bits/Pixel: 16   
------------------------------------------------------------------------------------------------------
Is this enough info or do you need more??

Just a small question, how come my video card can handle the Live CD but not the real thing??  :-? 

Thanks,
0vermind

P.S. Please reply back ASAP!!

---

### Post by az on 2005-08-19
[QUOTE=0vermind]What would be the solution then??[/QUOTE]

1-  Boot into Ubuntu.
2- log in
3-  type this:

sudo apt-get -f install


If that gives you no errors, then do:

sudo apt-get install ubuntu-desktop.


If nothing great happens, then you have a properly installed system with a misconfigured graphics server (X windows, or Xorg)

type:
sudo init 1
and then wait until you get to a comman line again and type:

dpkg-reconfigure xserver-xorg


and try to enter the correct settings for your hardware (video, keyboard, mouse, screen)  Do your best, but take the default if you have any doubt.  Say yes to autodetection and see what the default is.  When you are fininshed type
init 2
and see if that works.

If not, try again from 
init 1 
onward, again.


Good luck!

---

### Post by MetalMusicAddict on 2005-08-19
[QUOTE=0vermind]Video Card: Intel Corporation 810 Graphics Controller Hub[/QUOTE]
That is why. ;) I willing to bet you hear a start-up sound but you get a blank screen. If this is the case keep hitting Ctrl+Alt+Backspace till you kill Xserver. You should be able to log-on with a command prompt. 
Once you log in type **sudo nano /etc/X11/xorg.conf**.

Edit this:
```

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

```
To this:
```

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

```
That should get your screen workin till you find a solution. I have this problem on a Dell Inspiron 2200. It is fixed in Breezy though.

This is all of course if this is the problem your having. ;)

---

### Post by 0vermind on 2005-08-20
thanks, azz!!!

> 
1- Boot into Ubuntu.
2- log in
3- type this:

sudo apt-get -f install


this was the most help, here's what the system replyed back...

```

E: dpkg was interrupted, you must manully run 'dpkg --configure -a' 
to correct the problem.

```

I ran dpkg and to told me I must be super privilaged (root) sence 
I didn't know the password for root (didn't tell me), I typed in 
**sudo init 1**. Which shut everything down thus logging 
me into root. 

I typed in [b]dpkg --configure -a[/a] and it told me [i]Sorry [errno]. 
No space left on disk.[/i]. I'm now attempting to correct this disk space problem!!  ;-) 


Is there anything else I should try if this fails to correct the problem??

[SIZE=3]Thanks,
0vermind[/SIZE]

---

### Post by Velox Letum on 2005-08-20
Well, once you have the disk space issue corrected, you should be able to successfully repair your installation and install ubuntu-desktop.

---

### Post by az on 2005-08-20
Where did you install your system?  How much free space was there on the partition?


You need at aleast 2.5 gigs for a filesystem andd swap.  The installed files take up 1.8 gigs and you need a swap space and some free space...

P.S. there was a bug filed about this.

---

