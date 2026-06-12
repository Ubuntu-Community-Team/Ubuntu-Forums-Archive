---
title: "sync.out of range"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by excl12 on 2008-01-09
I am getting sync.out of range when installing xubuntu 7.10.
I tried safe graphics mode but problem persits.
Please help

---

### Post by Gina on 2008-01-09
Do you mean you can't run the Live CD or that you can't install onto HD from a Live CD session?

---

### Post by oldsoundguy on 2008-01-09
If you are using an NEC/Mitsubishi  monitor, that pop up indicates that there is NO VIDEO SIGNAL coming from the computer.
You need to post your equipment list (including the video card set up.)

---

### Post by excl12 on 2008-01-09
> **Gina said:**
> Do you mean you can't run the Live CD or that you can't install onto HD from a Live CD session?

I cant run live cd.

> **oldsoundguy said:**
> If you are using an NEC/Mitsubishi  monitor, that pop up indicates that there is NO VIDEO SIGNAL coming from the computer.
You need to post your equipment list (including the video card set up.)

I am using samsung monitor.
Vdeo card is geforce2 integreted.

---

### Post by or1on on 2008-01-09
are you trying to install the 64 bit os?
i have a similar problem with the 64 bit
u can add nosplash noapic and nolapic to the boot cmd and i got the live cd to work like that

---

### Post by excl12 on 2008-01-10
> **or1on said:**
> are you trying to install the 64 bit os?
i have a similar problem with the 64 bit
u can add nosplash noapic and nolapic to the boot cmd and i got the live cd to work like that

No,I am running 32 bit.
I will try what you have said.

---

### Post by murali on 2008-02-01
[B]I am also getting the Same problem.
I can run the live cd and I installed it on my pc(32 bit).
After that when i start the system, it shows [COLOR="Red"]SYNC. OUT OF RANGE[/COLOR]
I don't know how to change the resolution like in Windowx XP safe mode.
Can anyone pls help?[/B]

---

### Post by confused57 on 2008-02-01
> **murali said:**
> [B]I am also getting the Same problem.
I can run the live cd and I installed it on my pc(32 bit).
After that when i start the system, it shows [COLOR="Red"]SYNC. OUT OF RANGE[/COLOR]
I don't know how to change the resolution like in Windowx XP safe mode.
Can anyone pls help?[/B]
You could try booting the live cd, open a terminal(Applications---Accessories---Terminal), then check the monitor section in your xorg.conf:
```
gedit /etc/X11/xorg.conf
```
make a note of the vertical & horizontal refresh rates & near the bottom of the file which resolutions are listed.

Then reboot your pc with the live cd removed, boot into recovery mode, open your xorg.conf:
```
nano /etc/X11/xorg.conf
```
compare these values with the live cd xorg.conf...if different, change them to your live cd values..."Ctrl+x, y, enter" to save.  reboot.

Added:  You might also want to check which video driver the live cd uses.

---

### Post by murali on 2008-02-01
[B]Yeah. I tried all of them. Editing xorg.conf files , and techniques from wiki.
Still, when I start ubuntu it shows SYNC. OUT OF RANGE for some time
and then its working. Is there any solution?[/B]

---

### Post by Sargan on 2008-02-01
I have the same problem.

Also got a Samsung monitor. An old 19" that can handle very high resolution and timing but does not work at all with ubuntu install.

I was looking forward very much to try this new Ubuntu but now it is no fun any more because it cannot even start up from live cd :( I even send for cd's from far away to install but alas, does not work :(

:cry:

---

### Post by murali on 2008-02-02
My monitor is also samsung. I got the problem after installing it.

---

### Post by Sargan on 2008-02-05
Doesnt anyone have a solution to this? There seem to be quite some people having this problem and it feels like a really stupid error that should not be in an OS that is so popular and developed...

---

### Post by Sargan on 2008-02-07
Anyone?

Why is it broken?

---

### Post by Sargan on 2008-02-11
I also tried 32 bit version but it cannot install either.... I gets a bit further but a las, not installation come up...

What is wrong with ubuntu?

---

### Post by erginemr on 2008-02-19
All those who experience "signal out of range" at bootup, please follow this howto:

[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

### Post by erginemr on 2008-02-19
On the other hand, if you lose the screen not on an already installed system, but during the installation from Ubuntu Live CD, try either:

1. pressing F4 at the Ubuntu logo and selecting a lower resolution.

2. installing from Ubuntu Alternate CD, which uses a text-base (but still very user-friendly) installer.

---

