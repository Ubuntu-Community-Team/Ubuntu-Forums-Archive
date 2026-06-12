---
title: "Freeze after login screen..."
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by Squeeze on 2005-11-05
Hi guys,

Im having serious issues on a fresh installed Breezy Ubuntu box : it boots up and lauch gdm perfectly, then I enter my login/pass, I can hear the welcome sound, and ... nothing happens.
Gnome doesn't start, all I'm getting is the brown screen.
The thing is that I can move the cursor with my mouse, but I cannot kill X or even switch to another terminal : as if my keyboard was frozen...

Im desperetly looking for a solution to this problem : Im using Ubuntu on many other workstation, and it is by far my favorite distro, I really don't want to try another one in this case...

Here are some details about the dreaded computer :
- Intel P4C 2.4@3.0 with Hyperthreading ON
- 2x512M Dual-Channel RAM
- NVidia Geforce 6800GT

If you need any more details, just ask !

Eli

(I didn't know where to post this : Im not sure wether it's an installation issue, a gnome issue, or hardware ...)

---

### Post by joelypolly on 2005-11-05
I also have this problem but i am running on
AMD64 X2 3800
1024MB Ram
6800LE

---

### Post by Squeeze on 2005-11-06
> I also have this problem but i am running on
AMD64 X2 3800
1024MB Ram
6800LE

I'm sorry to hear that, but Im glad Im not the only one with this problem.

So guys, do you have any idea on what's going on here ?

Here is another info : Ive tried to install breezy KUbuntu, and had the same issue...

Come on, Im sure someone here can help us !

Eli

---

### Post by 23meg on 2005-11-06
This is a known Nvidia issue. You need to install the official Nvidia drivers and the Nvidia kernel module. Check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=75074") for instructions.

---

### Post by steelerguy on 2005-11-09
[QUOTE=23meg]This is a known Nvidia issue. You need to install the official Nvidia drivers and the Nvidia kernel module. Check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=75074") for instructions.[/QUOTE]

Wow!  This is sure convenient when you just installed Ubuntu for the first time and have to boot into another OS just to read the instructions.  I especially like all the "click on this" and "click on that" when you can't even get a window manager running.

---

### Post by youngdaniel on 2005-11-11
Is it me, or am I reading this same problem over and over again!!!

Surely theyre must be a post with the right solution!! Please help me!! It is making me so god dam mad!!! even angry!!!

Its like having a ferrari with no petrol!!! It is killing me!! 

I have a apple powerbook G3, 400mhz "Firewire" Model. 192mb of Ram, 8mb Video and DVD Drive. (I think my video card is ATI, but not sure???)

Ubuntu 5.10 Installed perfectly fine. On first attempt to login it took the details fine and proceeded to a brown screen, with an active mouse and even played the jingle to annoy me even more!! 

I have read so many dam posts talking about changing stuff in Xorg.conf but whatever i have tried has failed to help!! 

Please guys anything you can do to help!!! Please!!!

Dan

---

### Post by ssam on 2005-11-15
[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by nevc64 on 2005-11-16
I have been struggling with this issue for a couple of nights now. My iMac G3 500MHz reports the Date accurately so I don't believe my problem is related to the date issue SSAM refers to    [https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

At my last attempt I reinstalled Hoary 5.04 and repartitioned my Drive so that any residual configuration should have been destroyed. Hoary installed fine I was able to Log-in as normal and the iMac worked as expected. I did not make any changes to the standard install. Because some posts on this issue have referred to xorg.conf problems I printed out my xorg.conf file so I could check it against the Breezy updated version

I then inserted the Breezy Install CD which Synaptic detected straight away and asked me if I wanted to Update. I ran the complete update process which appeared to work fine. I rebooted and attempted to Log-in. When logging in I experienced the same problem I had with previous Breezy installs. System going unusably slowly. I could get out to a terminal with cntl-alt-F1. So I checked the xorg.conf file. It appeared to be the same as the file I had printed from Hoary.

**I don't know what else to try.** :confused:   There appears to be a lot of people experiencing this similar problem on different platforms. Hopefully a cause and a fix can be found soon. Unfortunately I'll have to re-install Haory and wait ...........

Neville

---

### Post by jack&amp;mary on 2005-11-29
[QUOTE=Squeeze]Hi guys,

Im having serious issues on a fresh installed Breezy Ubuntu box : it boots up and lauch gdm perfectly, then I enter my login/pass, I can hear the welcome sound, and ... nothing happens.
Gnome doesn't start, all I'm getting is the brown screen.
The thing is that I can move the cursor with my mouse, but I cannot kill X or even switch to another terminal : as if my keyboard was frozen...

Im desperetly looking for a solution to this problem : Im using Ubuntu on many other workstation, and it is by far my favorite distro, I really don't want to try another one in this case...

Here are some details about the dreaded computer :
- Intel P4C 2.4@3.0 with Hyperthreading ON
- 2x512M Dual-Channel RAM
- NVidia Geforce 6800GT

If you need any more details, just ask !

Eli

(I didn't know where to post this : Im not sure wether it's an installation issue, a gnome issue, or hardware ...)[/QUOTE]
Hi,
    Unfortuntely this problem of freezeups with wired (USB)  Keyboard AND wired (USB) Mice is also in our newest Apple iMac G5 17" LCD Flat Screen Hardware. Our new months old  from new iMac has the onboard ATI 9600 Video Graphics Chipset. 

So "IF" this is a graphics driver problem it isn't "JUST" nVida that has the problem, ATI must have the same problem.
 
                                                            cheers,
                                                            jack&mary

---

### Post by astranberg on 2005-12-30
I just got through fighting with similar brown cursor only screen after login screen issues in breezy live.. this is on a amd x2 4200 system..  I did a little searching in /var/log/syslog and saw that it was trying to get a dhcp address and failing for some reason.. after this it was sleeping!  so I did the following to kill off the dhclient process.. I hope this helps some of you out.

ctrl-alt-f1 - drop to cli
ps -ef |grep dhclient note the pid
sudo kill (PID for dhclient)
sudo /etc/init.d/gdm restart - this resulted in a hang still
after the brown screen appears 
ctrl-alt-backspace this restarts x and i logged in fine

---

### Post by ATAQ on 2005-12-30
Did you update the kernel or anything? Because this happened me before, but it was after I updated the kernel. Was strange aswell at the time!!

---

### Post by b_bycroft on 2005-12-31
I currently have the problem of Ubuntu freezing after the login screen. After about 15 seconds after the login screen loads up, everything freezes, stopping any input from the mouse or the keyboard. It can happen while I am still in the login screen or in the process of logging in.

I have not had this problem before, and it has only occured after I got a short PPPoA program to boot at startup (as directed to, so that I could I could get my speedtouch adsl modem to work).

Is there anyway to fix this problem or find out what is actually causing it?

---

### Post by Aphorism on 2005-12-31
Generally, IF there is a freeze, start with the basic XWindows config.

Chances are, it is some silly 3rd party proprietary chipset (like ATI or Nvidia) that is causing the problem.

START with changing the "Driver" line in your /etc/X11/xorg.conf line from "nv" for nvidia or "ati" for ati to "vesa".

That will at least usually get you up and off the ground window manager wise.

Hope this helps.

PS:  This is NOT a problem with Linux, OpenBSD, FreeBSD, or other... This *is* a problem with CLOSED source hardware vendors like ATI, Nvidia, etc.  Send your hate mail there if you want to see the world change.

---

