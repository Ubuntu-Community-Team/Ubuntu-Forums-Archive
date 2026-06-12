---
title: "oneiric gnomeshell does not respond"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by Crempel on 2011-10-13
I have done some searching but could not find any reference to this problem:
Unity works well, after installing gnomeshell and the gnome-tweak-tool gnome classic also works. Gnome (gnomeshell) also appears but does not respond to any mouse clicks or keyboard input; it is simply frozen.
Has anyone encountered this problem (and maybe know a fix)? All this happened today with Oneiric amd64.:(
Thanks in advance.

---

### Post by dave2001 on 2011-10-13
When you say "gnome shell" what packages did you install? I'm using the gnome shell on top of gnome 3 (which is what Unity runs on as well) and it's working fine. In order to get it i used the terminal command:

~$ sudo apt-get install gnome-session-fallback

I then had to do a complete reboot in order for it to change... just a relog would not switch the desktop properly.

---

### Post by Crempel on 2011-10-13
> **dave2001 said:**
> When you say "gnome shell" what packages did you install? I'm using the gnome shell on top of gnome 3 (which is what Unity runs on as well) and it's working fine. In order to get it i used the terminal command:

~$ sudo apt-get install gnome-session-fallback

I then had to do a complete reboot in order for it to change... just a relog would not switch the desktop properly.

Using Oneiric(=Gnome 3) I installed
gnome-shell
gnome-session-fallback
gnome-tweak-tool
The correct Gnomeshell desktop appears but is frozen. Unity and gnome classic work without problems. Maybe it's my graphic card (Nvidia 72oo), I don't know.:confused: I'm actually quite happy with Unity, have been since Natty, but I was curious to check out the Gnome 3.2 shell.
Anyway, thanks for your help.

---

### Post by dave2001 on 2011-10-14
hmm if your running unity ok, then i'd think your graphics card and driver combo should be able to handle gnome shell fine too. But it might be worth looking into if you're really itching to try gnome 3 shell out. I'm rather stumped on where else to look for a problem.

---

### Post by HydrocloricAcid on 2011-10-16
Got the same thing. tried all of the above.

I have a " nVidia Corporation G72M [GeForce Go 7400]" video card.

it maybe re4lated to your video card.From this **[COLOR="Blue"][link]("https://bbs.archlinux.org/viewtopic.php?id=116503")[/COLOR]** the guy there has the same card as me with the same problem. 

If it's a driver issue your card is close enough to mine to have the same problem.
I'll have to try the noveau driveer and see what difference it makes.

---

### Post by Crempel on 2011-10-16
> **HydrocloricAcid said:**
> Got the same thing. tried all of the above.

I have a " nVidia Corporation G72M [GeForce Go 7400]" video card.

it maybe re4lated to your video card.From this **[COLOR=Blue][link]("https://bbs.archlinux.org/viewtopic.php?id=116503")[/COLOR]** the guy there has the same card as me with the same problem. 

If it's a driver issue your card is close enough to mine to have the same problem.
I'll have to try the noveau driveer and see what difference it makes.

Quite funny, I reinstalled the operating system as Lubuntu, than via Synaptic installed gnome-shell plus a few other gnome related files and it works! Got the gnome shell to play around with (so far quite interesting); but why did it not work before?

By the way, my Aussie wife congratulates you Kiwis on your victory today!;)

---

### Post by jabz on 2011-10-16
I just had the same problem and discovered... I was logged out but it did not show on the screen. It had just appeared as If nothing works anymore. I will monitor this further...

---

### Post by Crempel on 2011-11-19
The problem occurred using the beta 2 release, I have how installed the final and gnome-shell and it works without any hiccups.:D

---

