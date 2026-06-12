---
title: "says low graphics mode then goes blank (ati allinwonder)"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by uxe1 on 2007-10-19
i get a little box saying running in low graphics mode, it gives 3 options; configure, continue, quit.

when i chose configure it gives me a screen that lets me pick my monitor and greaphics card. (basic lcd, acer al1912; and Ati all in wounder card)
then it returns to the screen before the warning box and does nothing. (took a nap to see if it was just being slow... woke to same screen)

continue gives me the same screen.
its 

*starting deferred execution scheduler ati                  [ok]
*starting periodic command scheduler crond             [ok]
*checking buffer state...                                              [ok]
running local boot script (/etc/rc.local)                        [ok]
(and then i get a curser)

its not even a command line because regardless of what i type in it wont do any thing
when i tried safe graphics mode my monitor flashed its "input not supported" box
every thing worked simply in feisty but now im stuck on my xp again :,(
please help, im a bit new to this but having a good time learning. thankx

---

### Post by Therion on 2007-10-19
Have you tried using [[COLOR="Blue"]Envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html")?

---

### Post by Wiebelhaus on 2007-10-19
lol , worst gpu of all time "All in wonder if it'll work?"

Crtl+Alt+F2 to drop to console ,

Run:


```
sudo dkpg-reconfigure xserver-xorg
```


Manually choose your configuration , read carefully , three finger salute to restart.

---

### Post by uxe1 on 2007-10-20
thanx ill try it and  repost

---

### Post by uxe1 on 2007-10-20
ok im missing some thing, ctrl+alt+f2 gives me   ^@
i dont know when to enter it.
envy looks promising, but how/when would i have a chance to load it. 
id just reinstall my feisty, if my girlfriend didnt take it to her house (if its like my hoodies il never get it back)
 i tried the install with a driver disk , and put in the disk i got with my ati card, that gave me some whirrs and beeps from my tower and then the curser that doesn't do any thing came back again.

i know in the future ill stear clear of the ati/amd combo, but i cant afford any thing right now

---

### Post by Laidbacklux on 2007-10-22
I am having a similar issue.  Fresh install of 7.10, everything works except I am in low graphics mode.  Have ATI All in wonder radeon.  

Tried dkpg-reconfigure xserver-xorg, went through the whole config and the system goes back to low graphics anyway.  

Tried System>Admin>Screens and Graphics and tried to change the driver with no luck, tried to change the monitor type (from pnp to generic widescreen) with no luck, tried changing both at the same time with no luck.

Tried Envy and it failed.  ( Build of the package fglrx-kernel-src failed! How do you     
       &#9474; wish to proceed?  )

---

### Post by bibliophage on 2007-10-31
> **Laidbacklux said:**
> I am having a similar issue.  Fresh install of 7.10, everything works except I am in low graphics mode.  Have ATI All in wonder radeon.  

Tried dkpg-reconfigure xserver-xorg, went through the whole config and the system goes back to low graphics anyway.  

Tried System>Admin>Screens and Graphics and tried to change the driver with no luck, tried to change the monitor type (from pnp to generic widescreen) with no luck, tried changing both at the same time with no luck.

Tried Envy and it failed.  ( Build of the package fglrx-kernel-src failed! How do you     
       &#9474; wish to proceed?  )


I have an Acer AL1917W and an ATI All-in-Wonder, and I´ve done everything you´ve done except try Envy, and all with the same result. Everything works, but I´m in low graphics mode and can´t seem to do anything about it. I&#314;l give Envy a try and see what happens.

---

### Post by craigsn on 2007-11-24
> **uxe1 said:**
> i get a little box saying running in low graphics mode, it gives 3 options; configure, continue, quit.

when i chose configure it gives me a screen that lets me pick my monitor and greaphics card. (basic lcd, acer al1912; and Ati all in wounder card)
then it returns to the screen before the warning box and does nothing. (took a nap to see if it was just being slow... woke to same screen)

continue gives me the same screen.
its 

*starting deferred execution scheduler ati                  [ok]
*starting periodic command scheduler crond             [ok]
*checking buffer state...                                              [ok]
running local boot script (/etc/rc.local)                        [ok]
(and then i get a curser)

its not even a command line because regardless of what i type in it wont do any thing
when i tried safe graphics mode my monitor flashed its "input not supported" box
every thing worked simply in feisty but now im stuck on my xp again :,(
please help, im a bit new to this but having a good time learning. thankx

I have the same problem, but this is on an install, where I'm booting off the liveCD. I have an ATI XPRESS 200 integrated graphics card on my computer, and I've tried both the 32bit and the 64bit CDs (I have an AMD 64 bit processor). 

So I do not have Ubuntu up and running on the computer to even try some of the things suggested in this post.

Any help would be appreciated

Craig

---

### Post by uxe1 on 2007-11-25
i reloaded feisty and am using that, (gutsy is akin to vista in my eyes, all about trying to look good not so much on being any good.) 
recently i had an old cvt monitor in my room and thought i wonder if i could load gutsy if i used my motherboards monitor out not my allinwonder's. -it didn't work,
but as i had my computers back to me and another monitor cord, i plugged it in the other out. so i had both my lcd and the cvt in the same time. it worked on the cvt!

mind you i didn't install, but the live disk works, my lcd blinks unsupported input then goes black. so this may be a problem caused by a low refresh rate on my lcd? 

just wondering if any of you have experienced the same, what monitors are you using, and have you tried them after removing the g-card? (just to see, no point in owing a g-card that isn't plugged in!)

---

### Post by tom1979 on 2007-11-25
> **uxe1 said:**
> i get a little box saying running in low graphics mode, it gives 3 options; configure, continue, quit.

when i chose configure it gives me a screen that lets me pick my monitor and greaphics card. (basic lcd, acer al1912; and Ati all in wounder card)
then it returns to the screen before the warning box and does nothing. (took a nap to see if it was just being slow... woke to same screen)

continue gives me the same screen.
its 

*starting deferred execution scheduler ati                  [ok]
*starting periodic command scheduler crond             [ok]
*checking buffer state...                                              [ok]
running local boot script (/etc/rc.local)                        [ok]
(and then i get a curser)

its not even a command line because regardless of what i type in it wont do any thing
when i tried safe graphics mode my monitor flashed its "input not supported" box
every thing worked simply in feisty but now im stuck on my xp again :,(
please help, im a bit new to this but having a good time learning. thankx

Im having the same problem, Packard bell Easy note, my graphics according to xp is Via S3G Unichrome IGP , theres no drivers in the live cd for it , and i cant locate a cd for drivers...

I installed gutsy from the same cd fine on my thinkpad...

---

### Post by nemesis8601 on 2007-11-30
EDIT:

I fixed the problem: in the /etc/X11/xorg.conf file I uncommented something I wasn't supposed to. doh.

I got the same error when I installed some drivers for a Wacom USB Tablet. I used the following command line:

sudo apt-get install wacom-kernel-source wacom-tools xserver-xorg-input-wacom

I had to restart the computer after installation, but when I did I got the low graphics mode window. Also, I type in Dvorak but everything was back in QWERTY when I booted. When I tried to reset the resolution of my monitor to native, it went crazy and had trouble redrawing windows. 

I un-installed all the stuff I had just installed, and rebooted a couple times to the same problem. 

My graphics card is NVIDIA GeForce 7950

Does anyone else have this problem or know how to fix it? I pressed ctrl alt f2 and tried running "sudo dkpg-reconfigure xserver-xorg" but it says the command dkpg-reconfigure is not found

---

