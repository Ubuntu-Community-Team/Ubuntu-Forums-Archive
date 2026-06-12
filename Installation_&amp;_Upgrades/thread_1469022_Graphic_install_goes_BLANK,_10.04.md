---
title: "Graphic install goes BLANK, 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by stolpiller on 2010-05-01
Hello

I'm having problems installing 10.04 on a IBM Thinkpad R51. It boots fine, loads the graphics... saying "UBUNTU", and below are some dots red/white moving... then it all goes BLANK... silent.. nothing happens (probably waiting for user imput?)

I've tried getting out of "normal" install by hitting ESC key, and selecting noapic and noa..p..l something?

No improvements.

Any Ideas, thanks in advance!

---

### Post by stolpiller on 2010-05-02
This must be a BUG. Maybe it should be moved to Bug section?

---

### Post by yoghurt on 2010-05-02
Erm...it seems to me it's nothing uncommon (unfortunately). I've seen several posts about the same thing on these forums in the last couple of days.

Here's what I found (and yes, I'm suffering from the same problem as well):

1) Upgraded Karmic to Lucid, restarted
2) In Grub, selected latest kernel, after a while screen goes blank and apparently loses ALL signals from graphics card (I have a Samsung screen which switches automatically between digital and analog input if it has no signal - that's why I think there is no signal)
3) In Grub, booted to LinuxMint, downloaded iso file, burned on a CD and went to re-install Ubuntu (luckily I keep my important files separated from system)
4) Same thing; installer didn't even start; didn't matter if I picked "straight install" or "live cd"
5) Found on these forums to start the installer with parameters "nomodeset" (press F6 at the initial CD screen)
6) Installed Ubuntu fine (in low graphics mode, but what the heck)
7) Went to Grub, picked Ubuntu, bang - blank screen
8) Pressed "e" next time in Grub, deleted the "quite splash" and replaced it with "nomodeset" - this keeps Ubuntu in low graphics mode
9) Booted up, logged in, downloaded latest NVIDIA driver
10) Exited X (ctrl+alt+f1), stopped GDM (had to do it the "old" way; "sudo /etc/init.d/gdm stop", as "sudo gdm stop" didn't work)
11) Installed driver, NVIDIA installer updated xorg.conf, wanted to start GDM again, but it wouldn't start. Had to use "sudo /etc/init.d/gdm start", X failed giving me at least low-graphics mode.
12) Now I'm going to try the "restricted drivers" that shipped with Lucid

My graphics card is NVIDIA GeForce 9600, up until now there were no problems at all with Ubuntu and nvidia cards (that I know of).

[EDIT] OK, I'm using Ubuntu Lucid in "proper" resolution. I hope the steps above might help someone.

---

### Post by stolpiller on 2010-05-02
I'm making a fresh install, on a computer that has only XP. The strange thing is that i see all the graphics in the beginning (UBUNTU logo and progress dots).

So unless there is a workaround i'm stuck. I will absolutely try "nomodeset" option.
Thanks yoghurt

---

### Post by yoghurt on 2010-05-02
My pleasure - if it works for you.

You can see the logo & dots because that's a low-res graphics.

---

### Post by stolpiller on 2010-05-07
I gave up, new bugs came along, and i'm suprised as this laptop is 4 years old. Switching to Vectorlinux insted.. 
Maybe will give ubuntu a new try, when it's ready

---

### Post by Daemoniq on 2010-05-10
I suffered this problem when upgrading my Thinkpad R51 from 9.1 to Lucid 10.04

The solution was to enter the GRUB2 menu by holding down the shift key just after the BIOS had finished during boot.

I then selected a previous kernel, and got a Recovery Menu, at which time I chose "Run in failsafe graphic mode".

I then followed workaround F here -
[http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

