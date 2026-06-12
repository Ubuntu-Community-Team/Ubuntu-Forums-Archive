---
title: "Stucks at un-graphical login screen"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Hyuuga on 2006-09-18
"ubuntu 6.06 LTS ubuntu tty1

ubuntu login:_"

these are the last two lines i get when i'm starting my freshly installed ubuntu dapper on my desktop.
I can't type anything (i've tried typing in the password and then pressing return/enter without result) and it never goes past that screen.

what the hell have i done wrong? i've reinstalled two times.

---

### Post by Chemroydal Tissue on 2006-09-18
You may have installed the server version. Try logging in (username/password - note that you won't see yr password, but it will be accepted as long as it is typed correctly), then type:```
sudo apt-get install ubuntu-desktop
```That should do the trick - I've never done this, myself, though, so I don't know whether or not you'll have to reboot.

---

### Post by Hyuuga on 2006-09-18
> **Chemroydal Tissue said:**
> You may have installed the server version. Try logging in (username/password - note that you won't see yr password, but it will be accepted as long as it is typed correctly), then type:```
sudo apt-get install ubuntu-desktop
```That should do the trick - I've never done this, myself, though, so I don't know whether or not you'll have to reboot.

> **Hyuuga said:**
> 
I can't type anything (i've tried typing in the password and then pressing return/enter without result)

did you read this part of my post? I can't type ANYTHING!
is it possible to install it normally with a server CD? i see the iso (downloaded through another computer) is named "server", i must have missed a link. I'll download it over again (got homework to do in the meantime anyway) but it's sad to waste a cd-r... sorry again for the trouble.

---

### Post by taurus on 2006-09-18
If you install the server version, then you don't get window manager.  So if you want to use Gnome, install the desktop CD (LiveCD).  Otherwise, at that prompt, type in your username first, then return key, and then your password!!!  :rolleyes:

---

### Post by encompass on 2006-09-18
For increased security you will not see yourself typing in your password.  Can you see yourself typing your username?
And your server install is not bad at all... it can do everything the otherone can, just in more complicated steps.

---

### Post by marccantlin on 2006-09-18
Is there a how to somewhere on how to set up the server... you know, so it has a desktop environment, and turns on the wifi card and all that jazz? I have learned a lot by starting out this way and am looking for some info on this.

---

### Post by Tomosaur on 2006-09-18
sudo apt-get install ubuntu-desktop

should sort out your graphical needs.

---

### Post by marccantlin on 2006-09-19
Am I correct in understanding that will install a gnome desktop?  Does it only install the X11 underpinnings and allow me to choose some other window manager later?

I did find quite a bit of useful information regarding setting up wifi cards through the searches... so thank you to everyone who posts answers to all of these silly quesitions on forums.  I think I could set one up on anything now.

---

