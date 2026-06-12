---
title: "Inspiron 1100 suspend problems ubuntu 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by SirWeazel on 2011-05-03
Let me thank anyone in advance for helping me with this old laptop.  I've installed Ubuntu 11.04, and have pretty much everything working ok.... kind of.  

When the laptop goes to "Suspend" it will not wake up.  Sometimes it locks up.  Sometimes the display is backlit, sometimes it does nothing. But i haven't been able to get it to work once.  I've read several of the other threads, and have tried several combinations that people have reported to work with other Ubuntu versions.  But i've had no success.

Hibernation mode does work, and if i can't get suspend to work, then is there away to remove "suspend" from all menus or have suspend default to hibernation mode?

---

### Post by OpenSage on 2011-09-21
> **SirWeazel said:**
> Let me thank anyone in advance for helping me with this old laptop.  I've installed Ubuntu 11.04, and have pretty much everything working ok.... kind of.  

When the laptop goes to "Suspend" it will not wake up.  Sometimes it locks up.  Sometimes the display is backlit, sometimes it does nothing. But i haven't been able to get it to work once.  I've read several of the other threads, and have tried several combinations that people have reported to work with other Ubuntu versions.  But i've had no success.

Hibernation mode does work, and if i can't get suspend to work, then is there away to remove "suspend" from all menus or have suspend default to hibernation mode?





I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---

### Post by SirWeazel on 2011-10-04
Thanks for the info. This sounds more like a "work around" rather than a fix? It's not really practical for my situation if it has to be done every time, but i'll look into it.

---

### Post by benjaminlaurent on 2011-10-10
Hi,

I tried to install ubuntu 11.04 on the same laptop as you (Inspiron 1100).
I managed the upgrade of the bios for foing that.
Everything works with the livecd but after the install I can't manage to have a clean display.
I only get  a display 480X600 in the left uper corner of the screen.

Can you help me to fix it !

---

### Post by benjaminlaurent on 2011-10-10
See here : [http://ubuntuforums.org/showpost.php?p=11014558&postcount=3](http://ubuntuforums.org/showpost.php?p=11014558&postcount=3)
There is the solution to my issue and yours also !

---

### Post by SirWeazel on 2011-10-10
> **SirWeazel said:**
> Hibernation mode does work, and if i can't get suspend to work, then is there away to remove "suspend" from all menus or have suspend default to hibernation mode?

I had the answer posted in another thread, but should put this standby solution here as well. 

Note: I don't think "suspend" works correctly with the display. It shuts off the display and doesn't turn it on upon resume. So i removed the option to suspend. (gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy) and change <allow_active>yes</allow_active> to <allow_active>no</allow_active> under the suspend to remove this feature, or under the hibernate feature if you want to remove that also) basically change "yes" to "no". The hibernate feature works for me. 

 Hope this helps.

---

### Post by SirWeazel on 2011-10-10
> **benjaminlaurent said:**
> See here : [http://ubuntuforums.org/showpost.php?p=11014558&postcount=3](http://ubuntuforums.org/showpost.php?p=11014558&postcount=3)
There is the solution to my issue and yours also !

I was going to send you to that thread, but you were quicker than i could respond.

---

### Post by bslayers on 2011-10-17
I have a Inspiron E1405, It has been working well in Ubuntu 11.04 classic. After the updrade three days ago to 11.10 all I have is a screen that that has a heading "File Edit Go Bookmark Help". There are no icons. My desktop files and folders do show. Also the screen will dim and I have to do a restart in order to get a bright screen back, never had this problem before. 
There were two errors or failures, can't remember which, during installation "Flashplugin-downloader" and "Firmware-b43-installer". 
At this point I am dead in the water. I would just like to go back to 11.04. I have looked for threads that address my particular issue but haven't found any information. 
Help would be greatly appreciated.

---

### Post by SirWeazel on 2011-10-17
bslayers,

I wish i could help, but i haven't upgraded yet. It sounds like a display/driver/unity issue. I don't think the two errors/failures that you encountered would cause your problem. Flashplugin-downloader is obvisouly flash and wouldn't cause your problem. And Firmware-b43-installer has to do with wireless network card.

I've seen multiple threads in regards to upgrade issues. Do you have an option before login to select unity2d? Or maybe backup your stuff and try a clean install. There are alot of changes from 11.04 to 11.10, and this leaves a lot of room for stuff to go wrong. Good luck, if i read of a solution somewhere i'll let you know.

---

