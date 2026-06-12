---
title: "Advice building *minimal* Xubuntu 9.10"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Redmage913 on 2010-01-11
Greetings,

I was thinking of creating an extremely minimal version of Xubuntu using XFCE.  I have a Dell Mini 9, a netbook that uses a wireless-g card requiring bcmwl-kernel-source to work.

What I would like to do is use either the alternate CD or mini.iso minimal install file to perform a command line install-style installation of the system.

So far, what I am thinking (from reading this DistroWatch.com article:  [HTML]http://distrowatch.com/weekly.php?issue=20090504[/HTML]) is to start off with these packages to begin with:

xorg
slim (if possible with 9.10, unsure if it is still available. in short, i want to use a lightweight display manager)
xfce4
xfce4-goodies
xubuntu-default-settings
bcmwl-kernel-source
aptitude

My opening questions are:

[LIST]
[*]Should I go with mini.iso or the Xubuntu Alternate Install CD (or the Ubuntu one)?  If so, which one?
[*]What additional packages will I need to make the hardware accessible and fully functional? All I can think of so far would be sound (I'd like to stay away from PulseAudio if possible, it wreaks havoc with my computer), my webcam, and the memory card slot, if additional packages are needed for it?
[*]What other "core" packages should I include in this list? Should I include Synaptic, or other packages, and why?
[*]What do I need to take into consideration, since this is both a directly- and battery-powered computer?
[/LIST]
Any and all input will be greatly appreciated.  I didn't want to start out completely on my own, so I thought I would ask the community what they thought.  What inspired me was the [HTML]http://ubuntuforums.org/showthread.php?t=1155961[/HTML] post regarding a "Ubuntu-Desktop-Minimal"-type system.

Cheers!

--Redmage913

---

### Post by zenxi on 2010-01-11
> **Redmage913 said:**
> Greetings,

I was thinking of creating an extremely minimal version of Xubuntu using XFCE.  I have a Dell Mini 9, a netbook that uses a wireless-g card requiring bcmwl-kernel-source to work.

What I would like to do is use either the alternate CD or mini.iso minimal install file to perform a command line install-style installation of the system.

So far, what I am thinking (from reading this DistroWatch.com article:  [html]http://distrowatch.com/weekly.php?issue=20090504[/html]) is to start off with these packages to begin with:

xorg
slim (if possible with 9.10, unsure if it is still available. in short, i want to use a lightweight display manager)
xfce4
xfce4-goodies
xubuntu-default-settings
bcmwl-kernel-source
aptitude

My opening questions are:

[LIST]
[*]Should I go with mini.iso or the Xubuntu Alternate Install CD (or the Ubuntu one)?  If so, which one?
[*]What additional packages will I need to make the hardware accessible and fully functional? All I can think of so far would be sound (I'd like to stay away from PulseAudio if possible, it wreaks havoc with my computer), my webcam, and the memory card slot, if additional packages are needed for it?
[*]What other "core" packages should I include in this list? Should I include Synaptic, or other packages, and why?
[*]What do I need to take into consideration, since this is both a directly- and battery-powered computer?
[/LIST]
Any and all input will be greatly appreciated.  I didn't want to start out completely on my own, so I thought I would ask the community what they thought.  What inspired me was the [html]http://ubuntuforums.org/showthread.php?t=1155961[/html] post regarding a "Ubuntu-Desktop-Minimal"-type system.

Cheers!

--Redmage913

i know this isnt exactly what you were looking for but its cool! [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
you can basically build your own distro buy following those instructions, great learning experience and you can really get down to the nitty gritty so to speak

---

### Post by Redmage913 on 2010-01-11
Thank you for the link, the books will be very interesting to look over.  However, I think they'll make a lot more sense in a year or so after I get in a lot more computer science courses, at least two of them being linux-related.

---

### Post by buntunub on 2010-01-12
A year or so for LFS? :P

If your feeling psychotic maybe.. Just maybe.

If you really want a fantastic minimal learning Distro go with ArchLinux. That aside, to ANSWER YOUR QUESTION, you should go with the alternate install method for *buntu, and install only that which you need. Either way, you will be required to do some homework and find out what exactly it is you will need.

---

### Post by Redmage913 on 2010-01-12
Forgive the noobish question, but where would a good place be to start this homework?  From what I can tell, I should be looking for a list of xfce (or gnome) tools required for my specific hardware.  Any advantageous places to begin?

---

### Post by buntunub on 2010-01-13
Google?..

Thats where I would begin anyway. Never has let me down! Good 'ol Google.

Another place might be the Ubuntu Wiki. All DE's come as a bulk of packages with the minimal stuff required, so no real decision to be made there unless you want the *extra's packages for that DE. Each DE tends to have underpinnings required for it to do all the cool automated things we take for granted like dbus, hal, udev, etc. Sometimes those things are included in the base packages, sometimes not, sometimes you will have to hand configure all these things yourself like in Slackware or Arch. I think the Alternate install guides you through a few of these things (but probably not all). There are thousands of guides out there to help get you through any issues that may crop up. Bottom line is that there is no "easy way" to do things from scratch in Linux, although some of these walk-through guides do make it much easier (but not necessarily correctly or without creating more issues later on down the road). You cant learn without doing and making mistakes, so backup your data and let er rip!

---

