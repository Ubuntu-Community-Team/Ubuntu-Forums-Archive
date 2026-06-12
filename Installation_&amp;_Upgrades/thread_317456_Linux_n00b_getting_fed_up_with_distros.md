---
title: "Linux n00b getting fed up with distros"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by DreadStorm on 2006-12-12
I've downloaded (and ordered) several distributions of Linux.  I have 7 total.  Only one has worked so far, and that one is Mepis. But I hate KDE.  Every time I either install or try a LiveCD, the video never works.  All these distros claim "superior hardware support".  Only Mepis seems to know what a GeForce4 MX 4000 is.  Everything else, including X/K/Ubuntu, kills video.  Makes my monitor act like I unplugged it.  The rest of the system keeps running, but with no video, what good is it? Even the "lesser" video settings have no effect.  NOTHING works.

To be quite frank about it, I'm getting fed up.  If anyone can save me from returning to Windows, please do so.  I'm about to give up on Linux altogether.

---

### Post by aysiu on 2006-12-12
Well, I don't think it makes sense to threaten to give up. If you want to give up, give up. If you want to get it working, ask for help.

That said, since Mepis is now based on Ubuntu, it shouldn't be that hard to use something other than KDE. If you like Gnome, for example, just paste these commands into the terminal: ```
su
apt-get update
apt-get install ubuntu-desktop
exit
exit
``` Then log out and choose *Gnome* from the session menu and log back in again. Now you're using Gnome on Mepis.

---

### Post by bswilson on 2006-12-12
> **DreadStorm said:**
> If anyone can save me from returning to Windows, please do so.  I'm about to give up on Linux altogether.

I'm sorry to hear you're having such problems.  Honestly, lots of folks have problems with the GeForce4 MX 4000 card.  Nothing is wrong with the card; but Nvidia cards are hard to configure on Linux in general because they don't make the device drivers easily available.

I strongly recommend you give [envy]("http://albertomilone.com/nvidia_scripts1.html") a try; it is a script created by Alberto Milone that automates the installation and configuration of the proper Nvidia drivers for Ubuntu.

---

### Post by aysiu on 2006-12-12
> **bswilson said:**
> I'm sorry to hear you're having such problems.  Honestly, lots of folks have problems with the GeForce4 MX 4000 card.  Nothing is wrong with the card; but Nvidia cards are hard to configure on Linux in general because they don't make the device drivers easily available. That's probably why the OP had no problem with Mepis--it has a simple one-click way to install Nvidia drivers during installation. No learning Synaptic first or enabling extra repositories.

I would advise sticking with Mepis and installing Gnome.

---

### Post by DreadStorm on 2006-12-12
I was a bit irritated, and I apologize.  Perhaps I should explain a bit.

About a year ago, a friend of mine who owns a Wireless-T1 internet service provider, introduced me to Linux.  Within a month of his tinkering, he switched his entire business from Windblows to Linux. (I'm not certain which one he landed on, but about 3 months later, he discovered Ubuntu.) 

When he told me about it "Something with a weird African name" (hehe) I kept in mind, when I moved from Alabama to NY (where I am now).  I figured if it's good enough for him to run his business on, it's gotta be good for what I do. (I'm a movie ripper - don't ask, don't tell - and no I don't share them).  Anyway, I had my hopes up, because LeRoy (him) had told me it was the best one he's come across [for n00bs].

From then till now, being stuck on dial-up, I attempted (and still do) grab distros that boast ease of use, good hardware support, etc.  Trick is, I don't know diddly about OPERATING Linux. So of all the distros that completed recently (and the Ubuntu CDs that finally arrived), Mepis was the only one that worked.

See, I'm a rather powerful Windows user.  I often send Microshaft alerts about certain vulnerabilities, most they ignore, but some warrant testing, I suppose. Either way, there's little to nothing I can't do on Winblows. Having been introduced to Linux, I saw this as a new and irresistable challenge to learn something new.

So, I hope you can see why I was so very PO'd about nothing but one distro working.  Kinda had my heart set on X/Ubuntu (not the KDE variety, looks too much like a Mac to me).

And thanks, guys, for yer understanding.  It takes a lot for me to give up on something, so when I wrote this post, I hope it explains why.

---

### Post by aysiu on 2006-12-12
As I tried to explain to you before, Mepis is based on Ubuntu now and uses Ubuntu repositories, so you can easily install and use Gnome or XFCE. You don't need to be stuck with KDE.

I, too, am sorry only one distro worked with your hardware. I was lucky enough to have everything except PCLinuxOS work with mine. It is what it is. If you want to give yourself a challenge, stick with Ubuntu. Otherwise, go with Mepis. I think it's that simple.

---

### Post by DreadStorm on 2006-12-12
Okay.  To make more sense of it, what I'll do is install Mepis, grab Gnome, get the drivers for Ubuntu, then switch over.  Sound like a plan?

---

### Post by aysiu on 2006-12-12
I'm not sure I know what you mean by "get the drivers for Ubuntu, then switch over."

Hardware detection is built into the kernel. It's not something you just grab. If you want, though, you can install Nvidia drivers for Ubuntu by following these instructions:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by DreadStorm on 2006-12-12
Can you tell I'm still too used to Winblows?  heh

So, if I understand correctly, there are no binary executable installers for Linux things?  Was hoping there'd be some way to download them now, and install later.  

I'm assuming I can change my video card for an old S3 or something to get things running, then "add" the drivers, and put the card back in.

---

### Post by aysiu on 2006-12-12
You don't have to agree with me, of course, but I think your best course of action is to install and use Mepis for a couple of weeks. You can use Gnome in Mepis, as I've said before. Once you get used to the general Linux way of doing things (managing software, navigating the interface, learning appropriate terminal commands), then that would be a great time to take on the challenge of installing and configuring Ubuntu to work on your hardware.

What do you say?

---

### Post by DreadStorm on 2006-12-12
Better plan than mine.  heh  Thanks, boss.  I owe ya one.  And thanks for your patience.

Amazing what you can do when slow down and look at things.

---

### Post by aysiu on 2006-12-12
By the way, I used Mepis for about a month before switching to Ubuntu, and I've been using Ubuntu for more than a year and a half since then. It's a plan that worked... at least for me.

And if you have even Mepis questions, chances are people on the Ubuntu Forums can help you out.

---

