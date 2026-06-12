---
title: "Is Kubuntu Slow For Anyone Else?"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-10-07
I really don't understand this. I have an Ubuntu Dell that I upped to have 4GB of RAM (instead of 2GB), a Core 2 Duo processor (instead of a Pentium Dual Core) and a 500GB hard drive. This thing runs slow as heck.

Booting up is extremely fast. However, there is a noticeable delay in opening files/folders, minimizing applications, and pretty much everything else.

The strange thing is that CPU usage is always really low, as is the memory usage. All of this with or without desktop effects.

My AMD-based desktop kills this thing. Is this a bug or perhaps a configuration issue?

PS. I did check my power settings, I set it up to push the CPU to performance mode while plugged in and I have it plugged in now.

I can't think of anything else that would cause this. :(

---

### Post by raygj on 2009-10-07
in "ubuntu"to speedup desktop you need  to install a  "restricted accelerated 3D video driver".goto "menu->System->Administration->Hardware Drivers".
enter your user password in the pop-up window.it will then scan for Proprietary Drivers.if it finds a  "3D-accelerated proprietary graphics driver" then select it and click on the Activate button at the lower right of the window.when its finished it will ask you to reboot the computer. if no 3D drivers are found,exit "Hardware Drivers" program then goto "menu->System->Administration->Software Sources" and make sure that the small "square" box to the left of  
"Proprietary drivers for devices(restricted)" 
has a "tick" mark inside it.if it is not "ticked", click on the small square and a tick will appear.close the "Software Sources" program.it will rescan the download repositories.after it has finished,  rerun "menu->System->Administration->Hardware Drivers" scan for restricted hardware drivers and activate the newly found "3D-accelerated proprietary graphics driver".
in "Kubuntu" you need to do the same,but as i haven't got "Kubuntu" installed .But you should find both
 "Hardware Drivers" & "Software Sources" in the "Control Center"

---

### Post by jlacroix on 2009-10-07
> **raygj said:**
> to speedup desktop you need  to install a  "restricted accelerated 3D video driver".goto "menu->System->Administration->Hardware Drivers".
enter your user password in the pop-up window.it will then scan for Proprietary Drivers.if it finds a  "3D-accelerated proprietary graphics driver" then select it and click on the Activate button at the lower right of the window.when its finished it will ask you to reboot the computer. if no 3D drivers are found,exit "Hardware Drivers" program then goto "menu->System->Administration->Software Sources" and make sure that the small "square" box to the left of  
"Proprietary drivers for devices(restricted)" 
has a "tick" mark inside it.if it is not "ticked", click on the small square and a tick will appear.close the "Software Sources" program.it will rescan the download repositories.after it has finished,  rerun "menu->System->Administration->Hardware Drivers" scan for restricted hardware drivers and activate the newly found "3D-accelerated proprietary graphics driver".

Thank you for the assistance, but your instructions are for Ubuntu, though I'm using Kubuntu. The only restricted driver required by my system is for my network card, my video card is an integrated Intel so I don't think there are restricted drivers there. At least, it doesn't show me that there are any.

---

### Post by raygj on 2009-10-07
i have edited my post.reload this page. you should find both
"Hardware Drivers" & "Software Sources" in the "Control Center"
you should check what setting you have in 
 "Software Sources" & try again "Hardware Drivers"

---

### Post by inportb on 2009-10-07
Pretty much the only slowness I get is when I open Dolphin. Lately though (for an hour or so), I've been getting frequent KDE crashes. I've been using Fluxbox.

---

### Post by jlacroix on 2009-10-07
> **raygj said:**
> i have edited my post.reload this page. you should find both
"Hardware Drivers" & "Software Sources" in the "Control Center"
you should check what setting you have in 
 "Software Sources" & try again "Hardware Drivers"

Thank you, but I can assure you drivers aren't the problem from my research. Installing such hardware drivers is the first thing I do when I set up my laptop.

---

### Post by Lukios on 2009-10-07
I suggest the next time you install kubuntu that you do it from a mini.iso. It will be much lighter and a bit quicker.

---

### Post by inportb on 2009-10-07
I discovered that a while ago. However, with the Karmic pre-release, the mini.iso couldn't even install the kernel properly :)

---

### Post by jlacroix on 2009-10-07
> **Lukios said:**
> I suggest the next time you install kubuntu that you do it from a mini.iso. It will be much lighter and a bit quicker.

I might do that. I just find it odd that there is this much of a difference from an Intel Core 2. You'd think it would've been a decent processor. I guess not.

It seems to get quicker after the fact. What perplexes me is that when it slows down to a crawl, the CPU usage and RAM usage do not go that high at all. CPU is around 10%. 

In fact, it seems to have trouble doing more than one thing at a time...

---

### Post by Lukios on 2009-10-07
Its not your processor trust me. I have the same thing. In all reality, ubuntu in general is slow. It doesn't matter if its running xfce or kde its its a hog. I refuse to install from a live cd any more. Instead of getting all of the bs that comes with the live cd, I can simply install what I need taking up less resources.

---

### Post by jlacroix on 2009-10-07
> **Lukios said:**
> Its not your processor trust me. I have the same thing. In all reality, ubuntu in general is slow. It doesn't matter if its running xfce or kde its its a hog. I refuse to install from a live cd any more. Instead of getting all of the bs that comes with the live cd, I can simply install what I need taking up less resources.

Yeah, but I don't remember it being that way with Arch Linux, but my memory may be fading.

---

### Post by NormanFLinux on 2009-10-07
Just updated Kubuntu Jaunty through the backports to KDE 4.3.2. Runs smooth here. Waiting for the official Karmic release later this month.

---

### Post by sleepitoff on 2009-10-07
Funny, I was surprised how fast and smooth Kubuntu IS running with Karmic. ;) I wasn't expecting it. 

Changing your swap memory from 60 to 10 might help you out some, though...  
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by jlacroix on 2009-10-08
> **sleepitoff said:**
> Funny, I was surprised how fast and smooth Kubuntu IS running with Karmic. ;) I wasn't expecting it. 

Changing your swap memory from 60 to 10 might help you out some, though...  
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

It runs extremely awesome on my desktop. I'll try that swap thing tonight.

---

### Post by Lukios on 2009-10-08
I was going to say that it was probably something that didn't get set up properly

---

### Post by zevans on 2009-10-08
Yes, there is a definitely a problem with your install. Karmic Kubuntu is pretty rapid on Intel gfx. My netbook flies and that's only an Atom so you should be really flying.

Try booting off a live CD and seeing how quick that is? Did you upgrade or do a new install?

---

### Post by DeeZiD on 2009-10-08
Kubuntu is only slow here switching desktops (how to kill this ugly desktop switcher OSD??) :(
And of course QTcurve in GTK2 apps. Try enabling smooth scrolling in firefox with qtcurve theme and compare it to any other gtk2 theme ;)


Dennis

---

### Post by jlacroix on 2009-10-08
> **zevans said:**
> Yes, there is a definitely a problem with your install. Karmic Kubuntu is pretty rapid on Intel gfx. My netbook flies and that's only an Atom so you should be really flying.

Try booting off a live CD and seeing how quick that is? Did you upgrade or do a new install?

I did a fresh install. The Live CD's generally run slower for me due to how much slower CD access speeds are generally.

> **DeeZiD said:**
> Kubuntu is only slow here switching desktops (how to kill this ugly desktop switcher OSD??) :(
And of course QTcurve in GTK2 apps. Try enabling smooth scrolling in firefox with qtcurve theme and compare it to any other gtk2 theme ;)


Dennis

Where is that smooth scrolling option? I don't see it. :(

---

### Post by gjoellee on 2009-10-08
I have tried vanilla KDE and there is nothing slow about it, and sadly I have to confirm that Kubuntu is slow and is a bad KDE distro in my opinion.

---

### Post by buzzmandt on 2009-10-08
I gotta say
kubuntu is very snappy
on my lappy

my laptop does very good with kubuntu, not any speed difference between it and ubuntu, both are very snappy and user friendly

celeron 1.86 mobile
intel graphics
2 g ram

EDIT: and thats with kwin in kde and compiz in gnome both active

---

### Post by kayosiii on 2009-10-08
I was having some speed issues with dolphin - it turned out to be a 1.2GB jpeg in my home folder that it was trying to index (don't ask)

---

### Post by DeeZiD on 2009-10-09
> **DeeZiD said:**
> ...(how to kill this ugly desktop switcher OSD??) :(

...

Dennis

Does anybody know, how to disable this crap? :mad:

---

### Post by ptn107 on 2009-10-09
Karmic Beta (2.6.31-13.42) x86_64 works well and fast here.

---

