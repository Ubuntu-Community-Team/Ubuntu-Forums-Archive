---
title: "Screen Settings - the 800 Pound Paper Cut Gorilla"
date: 2009-07-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by artsci2 on 2009-07-03
On huge problem for my adoption of Ubuntu/Linux has been the frequent problems related to getting the output of the video card to match the specs of the monitor(s). Not 3D or video acceleration, just pixel x pixel and refresh rate. 

An end user should be able to System>Preferences>ScreenResolution and type in the pixel x pixel and refresh rate then click apply and have a 10 second do-you-want-to-keep-this-setting-window.

(BTW as I write this there is a pink box with "Unknown" in the upper left corner which popped up when I checked the resolution change command. It will not move or go away) 

[B]Stop reading here unless you are interested in a dabbler's Linux-life story.
[/B]

I'm a science/techno guy that at one time has programmed MC6800 (8bit 1Mhz) on a system that the code was entered directly in hexadecimal on an extended numeric keypad. 

Computers to me are tools used to do things faster. Any time used getting a computer to work is a delay in the current project's progress. But I also know that time taken to sharpen a saw saves more time in cutting a big stack of wood. However, there is a point somewhere that work on the tools can use all the time allocated for a project. It would take me less time to saw a small stack of wood with a dull saw than it would for me to build a whole new saw. 

I gave up programming in C when I noticed that I could finish a typical scientific project using Exel spreadsheets before the programmers could get past the debugging stage. One sheet that calculated temperature change across the depth of skin exposed to IR light was more than 10k lines. I finished in a week and the programmers were still working on a C version a month later. Good thing for me that I didn't wait for them to finish, and also that I didn't taunt (never told them actually) because later projects needed programming that Excel couldn't do.

My first Linux was Redhat 5.x bought in a retail set.
The Visa bus 486 motherboards didnt mix well with Redhat. 

Later I got acess to a 133Mhz pentium machine with an S3 virge video card and ended up being the first guy in my research building to surf the web on a linux machine. Back then the spreadsheets on linux were too far below Excel for me to switch from Windows/Mac.

I became addicted to dual screens, kept a main system with excel and a second system to try linux. 

Looked at DSL and actually contributed$

After getting a fast internet connection and downloading many different  
linux versions which were usually discarded because of video/monitor problems. I settled on SUSE and decided to buy it at BestBuy so I had a full set of printed manuals. The experience was much better with SUSE but the spreadsheet problem still existed and any hardware changes were so problematic that I ended up just planning a complete system re-install whenever I opened the case or plugged in a different monitor.

My interest waned because linux was consuming too much time. A year or so went by.

Now to 2008. I tried Ubuntu. Much better! Maybe even dual screens working...

So I went out and bought all new hardware to make an Ubuntu machine AMD 7750, 4Gb Ram, 2 big HD, Radeon HD 4550, (2) 1680x1050 lcd.

Maybe screen setting is a decapitating paper cut, 'ended up removing the dual heads and buying a 1920x1200 monitor to use instead of fighting with the two screen set-up.
Then to save time I just re-installed the whole system on a separate drive from my data disk.

Am now looking a Gnumeric spreadsheet because I found it has the MINVERSE function I need.

---

### Post by BwackNinja on 2009-07-03
Okay, this is something I can agree with. I still have to manually add my screen resolution (1360x768) to be able to use it, though once I do everything looks perfect.

Its just functionality missing from the gui - you can still do it from xrandr so it shouldn't be too hard to implement.

---

### Post by halfsane on 2009-07-03
Yes,  Also better dual monitor (if your not using nvidia) and TV controls should be looked into.

---

### Post by wayne_cat on 2009-07-04
This is a screenshot from the gnome 2.26 dokumentation:

[http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/)

Don't know if there is something like this in kde.

[[IMG]http://ubuntu-pics.de/thumb/17862/rnusers_display_settings_png_de_09sQU2.png[/IMG]]("http://ubuntu-pics.de/bild/17862/rnusers_display_settings_png_de_09sQU2.png")

---

### Post by Regenweald on 2009-07-05
This is actually an item that i remove from my menu entirely, as the first time i messed with it i was screwed royally. Messing with refresh rates and screen resolution is something you take for granted in Win and it is quite a source of contension here for tweakers. 

In any case it is not something i need to play with as my stock dell 17" is always properly recognised and Ubuntu adopts my max res of 1400 by 900 60hz beautifully. There is definitely room for improvement, but no complaints here.

---

### Post by meborc on 2009-07-05
well... if you backup your xorg conf, you can mess with the resolution and refresh rate because it is easy to restore the old state...

now-days the xorg conf is not used any more, you can even work without having one, but it is still necessary for manual tinkering 

if you once set up your dual screen system, you don't need to spend time on it again... :) good luck

---

### Post by caryb on 2009-07-05
This is the Kubuntu screen when 2 monitors are connected they both show up. Mind you I have never managed to get this goin & as I have a Nvidia card I use there utility program:lolflag:

Cary

---

### Post by lithorus on 2009-07-05
> **caryb said:**
> This is the Kubuntu screen when 2 monitors are connected they both show up. Mind you I have never managed to get this goin & as I have a Nvidia card I use there utility program:lolflag:

Cary
Interesting that in Gnome, when I select the "Display" option in Preferences. It comes up and says : "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

And opens up nvidia-settings instead when I press 'yes'.

I like :)

---

### Post by meborc on 2009-07-05
> **lithorus said:**
> I like :)

me too, though i think the nvidia-settings program should be opened automatically... the error message and the pointless YES/NO selection should go... user OBVIOUSLY wants to configure the resolution... so just open the nvidia panel automatically ;)

---

### Post by soapytheclown on 2009-07-05
> **meborc said:**
> me too, though i think the nvidia-settings program should be opened automatically... the error message and the pointless YES/NO selection should go... user OBVIOUSLY wants to configure the resolution... so just open the nvidia panel automatically ;)

agreed

---

