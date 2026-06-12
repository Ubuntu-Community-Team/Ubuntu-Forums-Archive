---
title: "Minimal install with a fully functioning desktop"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by ubrox on 2012-01-06
Hello,

Here is something I tried many times and finally came here for help.

**Objective**: Install Ubuntu (or few other flavors) with minimal footprint and flab. This is for a VirtualBox guest.

**Summary:**
VirtualBox v4.1.8
Host: Mac OS X Lion
Guest: Ubuntu 11.10 32-bit

**Here is what I did already:**

I installed base system and rebooted. Did a number of different combinations of manual installs of other packages. Never did I succeed with a functioning desktop. I think I almost got there once but probably the lack of functionality with unity threw me off or I was too tired.  

**What do I need:**

What do I do after base system install to get to a fully functioning desktop (preferably Ubuntu, but open to XFCE)? 
I dont need any calendar, IM, unity, office, graphics utils, etc. 

All I need would be a terminal, PDF viewer (evince or related), Chrome, and VB guest utilities. 

Thank you for your help.

Bonus question: Should I leave the vb guest package that installs with Oneiric or should I install the version that comes with VB? I am using VB v4.1.8

---

### Post by snowpine on 2012-01-06
Here's a great tutorial to build a minimal Ubuntu system:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Regarding guest additions, I have always used the "Install Guest Additions" feature of VirtualBox itself. :)

---

### Post by ubrox on 2012-01-06
Thanks snowpine, Thats link is great. The procedure listed there is very similar to what I did so far. 

I should add a clarification - I would like to have the ubuntu look & feel and preferably gnome instead of icewm. I am open to XFCE if I can find instructions on how to get a smooth look & feel and more importantly, good looking fonts. By default, XFCE on my installs has very jagged and ugly fonts. I usually change it to what I like but it still doesnt look good.

I am not looking for beauty but I need usability because I work on terminals and browsers a LOT. I dont want to stress my eyes. Also, if I am going to look at it for a long time, might as well look at something beautiful. :)

---

### Post by snowpine on 2012-01-06
Ubuntu fonts:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Regarding the Psychocats tutorial, icewm is just used as an example; you can substitute the desktop environment of your choice. :)

---

### Post by ubrox on 2012-01-06
> **snowpine said:**
> Ubuntu fonts:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Regarding the Psychocats tutorial, icewm is just used as an example; you can substitute the desktop environment of your choice. :)

So, thats where I have the problem. I try to install gnome, but it messes up. I think I got XFCE working fine. I dont want to install the *-desktop meta packages as they will install everything that I dont need. 

If there is a way to get a working gnome desktop and ubuntu artwork and look, while skipping the bluetooth, office etc .. that would be great

---

### Post by snowpine on 2012-01-06
For a minimal Gnome I think you want to install **gnome-core** instead of **ubuntu-desktop**.

Bluetooth is a dependency of the Gnome desktop, nothing to worry about. gnome-core will not install an office suite.

---

### Post by ubrox on 2012-01-06
I tried gnome-core and I think it worked. I need to revisit it. I was either too tired or exhausted from multiple installs that I got mislead by a non-working unity 3D. 

Do you know how to install lightdm without unity?

---

### Post by snowpine on 2012-01-06
I've never used lightdm, sorry.

---

