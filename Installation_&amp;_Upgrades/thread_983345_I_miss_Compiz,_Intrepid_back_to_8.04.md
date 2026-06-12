---
title: "I miss Compiz, Intrepid back to 8.04"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by yogo on 2008-11-15
Since Intrepid really does not do anything but make sure I can not run Compiz. I am going back to 8.04 after a couple of weeks thinking a fix/workaround would come about.

I have burned 8.04 so I am ready to install. I am guessing I will lose Crossover and other programs rolling back. 

What is the best way to undue Intrepid?

Thanks for suggestions.

---

### Post by alwayshere on 2008-11-15
Compiz i got it going fine on 8.10 

what exactly is the problem you having

---

### Post by alwayshere on 2008-11-15
these are are the goodies i got you could copy and paste the below 12 commands all at once into terminal push enter and let it do its thing run the next command if asked then the next command to update.should sort compiz for ya 

> sudo apt-get install compiz
sudo apt-get install Compiz-Fusion-bcop
sudo apt-get install Compiz-plugins
sudo apt-get install Compiz-wrapper
sudo apt-get install Compiz-core
sudo apt-get install Compiz-gnome
sudo apt-get install libemeraldengine0
sudo apt-get install emerald
sudo apt-get install libdecoration0
sudo apt-get install Compiz-Fusion-plugins-main
sudo apt-get install Compiz-Fusion-plugins-extra
sudo apt-get install compizconfig-backend-gconf

if asked in terminal  run below command 
sudo apt-get autoremove

then 
sudo apt-get update


---

### Post by yogo on 2008-11-15
Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation** 82845G/GL[**Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

I have an intel chipset, seems this does not work in 8.10, I have looked everywhere and tried to find someway to get Compiz up and running.

Other than I have no desktop effects, Intrepid works just fine for me.

I do miss the desktop effects.

I will give those a try, running all twelve commands at once but I think it will break my desktop and then I will have to remove compiz at console, I have gone though this a coulpe of times already.

---

### Post by yogo on 2008-11-15
I gave those twelve commands at once a run but as I expected, my desktop was gone and had to boot into recovery mode and at console run sudo apt-get remove compiz and sudo apt-get remove compiz-core then exit and boot normally.

I have done this a few times before, just do not know if there is a workaround for this chipset listed above.

---

### Post by oldsoundguy on 2008-11-15
From what I can garner in posts here and "Why?  posts here, the video drivers in Intrepid DO leave a lot to be desired for a LOT of cards (somehow not all)  The folks at Envy are struggling to get something to work other than basic stuff for NVidia and for some ATI cards.

Right now all I have is single mode landscape displays on 3 different 8.10 machines that used to have all the bells and whistles including rotation on 7.10 using various NVidia cards. (did manage to get a wide aspect ratio on one of them by using the OLDEST driver in the package manager.  But as to anything else such as COMPIZ and such, not now!)

The blog at Envy indicates that they are working on it, but no idea as to when there will be any progress.  The Envy crew is now doing the writing of the NVidia stuff as anything older than 6 months and out of production is no longer updated by NVidia itself.

SOME of the driver work they are doing MAY migrate to other video display cards/chips.  But Ubuntu is also rather silent on the matter.  And their supposed "help" at LaunchPad is non existent on the video issues .. they put you on ignore right now!

---

### Post by alwayshere on 2008-11-15
on my macbook 1.1 , I have a 

Intel Corporation Mobile 945GM/GMS, 945/940GML Epress Intergrated Graphics Controller (rev 03)

running  full affects 

I don,t no if this is of any good to you but I thought id through it out there just in case it my help somehow

---

### Post by yogo on 2008-11-15
> **alwayshere said:**
> on my macbook 1.1 , I have a 

Intel Corporation Mobile 945GM/GMS, 945/940GML Epress Intergrated Graphics Controller (rev 03)

running  full affects 

I don,t no if this is of any good to you but I thought id through it out there just in case it my help somehow


What are you suggesting I do to get mine running?

TIA

---

### Post by alwayshere on 2008-11-15
i had a look about and i see i have these youcould try them and see if they help might be woryh a go ??

sudo apt-get install xserver-xorg-video-i740
sudo apt-get install xserver-xorg-video-intel-dbg
sudo apt-get install displayconfig-gtk
sudo apt-get install fglrx-modaliases

---

### Post by yogo on 2008-11-15
> **alwayshere said:**
> i had a look about and i see i have these youcould try them and see if they help might be woryh a go ??

sudo apt-get install xserver-xorg-video-i740
sudo apt-get install xserver-xorg-video-intel-dbg
sudo apt-get install displayconfig-gtk
sudo apt-get install fglrx-modaliases


I tried this as well, I ran those all at once then I ran the previous 12 from above that you posted.

My desktop was gone again, I had to run the sudo apt-get remove compiz ......etc to get my desktop back.

Thank you for these ideas. 

Sure would be nice to get Compiz working...?

---

### Post by bonfire89 on 2008-11-16
I too am having issues with my thinkpad x60 tablet and the 945gm/940gml

---

