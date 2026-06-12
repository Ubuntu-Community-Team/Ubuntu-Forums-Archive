---
title: "DM without DE for PERFORMANCE"
date: 2018-03-16
forum: Installation &amp; Upgrades
---

### Post by mattzab on 2018-03-16
Hello,

I don't know which forum this question belongs in...


I've installed Ubuntu, just the core, and now I'm at the point sure I have a terminal. I have networking and apt available.
I want to be able to launch individual programs from CLI. Say I boot into the system and get to my terminal prompt, I run 'gedit'

I'd like that to just launch gedit full screen. I've installed gdm, but I think there's more to this that I'll need to accomplish this. What else do I need to install, or start, to do this?

Edit: I don't want to install a DE and all that comes with. I'd like to get as much performance as possible. So, no DE or WM in this scenario. Make sense?

Extra info:
My use case is, running Ubuntu on a Citibank in a Chroot, within a chrome tab. I'm able to do this no problem when using xiwi, but that can only run as a tab rather than a window. I want to be able to launch chrome shell in a stand alone window, then enter terminal, and from there just open individual programs like gedit, gimp, android studio, etc.


Thanks!

---

### Post by kerry_s on 2018-03-16
most how to's are old. i did find this 1 which is a month old.
[https://git.devuan.org/dev1fanboy/Upgrade-Install-Devuan/wikis/Minimal-xorg-install](https://git.devuan.org/dev1fanboy/Upgrade-Install-Devuan/wikis/Minimal-xorg-install)

---

### Post by Irihapeti on 2018-03-16
I've done this sort of thing with current versions of Ubuntu; in fact, I've done it without GDM or equivalent.

If you have Xorg installed, once you get to the login prompt, you should be able to run
startx
and you'll get an xterm instance in the top left-hand corner of your screen.

If you then run gedit from the command line, you'll get a graphical window that you won't be able to move around with a mouse. It's been a while since I've done this, so I don't recall if the window is full-screen or smaller.

Personally, I prefer to install a lightweight window manager such as Openbox - there are a number of other alternatives - which gives me the choice of having more than one window open at a time and being able to resize / shift them around.

---

### Post by mattzab on 2018-03-16
Startx was what I thought I should do, but I'm getting an error. I'll post the output soon.

---

