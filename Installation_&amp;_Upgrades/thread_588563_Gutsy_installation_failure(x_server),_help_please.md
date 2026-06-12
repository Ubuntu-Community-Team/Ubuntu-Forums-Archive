---
title: "Gutsy installation failure(x server), help please?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ohyea on 2007-10-23
Ok so I am currently running windows XP and want to dual boot with 7.10. So I get the iso and burn the cd no problem. I restart the computer with cd drive having priority and the linux installation screen loads. I hit start linux/install and it begins doing its thing. After four OKs I get the following error:

/etc/gdm/failsafeXServer: line 47
Warning: Could not retrieve EDID because get-edid is not installed

I have been told to type sudo dpkg-reconfigure -phigh xserver-xorg into the command prompt but the only command prompt I can get to is the boot prompt which doesn't recognize the command 'sudo'. If anyone could please point me in the correct direction with how to solve this problem that would be awesome. Thanks!

Specs:
Dell Dimension 3000
ATI Radeon 9250
1 gig RAM

---

### Post by Phrellex on 2007-10-23
I am getting the same error through updating from Fiesty Fawn. Its really irritating and I am unsure how to fix it. X Server can not start and all I am given is a command line, which can login to my user profile. ----------- Oh it is not the case now, I tried the fix somebody told you and it accually worked. -------

---

### Post by ohyea on 2007-10-23
So does anyone know how I might solve this?

---

### Post by ohyea on 2007-10-25
So I've been working this a bit and finally found my way to a command prompt. So when my error comes up (x server could be started blah blah) if you hit Ctrl-Alt-F1 you will be taken to a command prompt screen. There I tried typing in:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and I get a warning about the file being overwritten and everything but it looks good. So where should I go from there? I don't believe I can restart because I haven't installed the kernel and thus the new file won't be saved so is there a way to install or get the GUI from there? Thanks for any help!

---

