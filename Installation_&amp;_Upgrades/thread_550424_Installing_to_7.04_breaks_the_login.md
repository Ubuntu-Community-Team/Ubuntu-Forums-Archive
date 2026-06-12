---
title: "Installing to 7.04 breaks the login"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by jyoutsu on 2007-09-13
Hi, I recently installed Ubuntu 6.10 from a CD I had, not Feisty because I don't have the CD or a CD burner (anymore)

Everything was working fine, besides 3D acceleration, so I decided to upgrade to Feisty.  Eventually everything installed, I rebooted, and there was no login screen.  Nothing responded, although the caps lock and all those on the keyboard would toggle.  So I rebooted again into recovery mode and tried startx, went to the same screen. (Note that I also had no changes to the xorg.conf, although I did reconfigure it)

Also, I tried "gnome-session", not quite sure what it'd do (I'm a noob, if you can't tell) and I don't have the whole error message, but something like "Server cannot start on display",  then no display number afterwards.  I'm not sure what to do now besides reinstall, which I'd rather not do (I spent about two days doing nothing but upgrading and installing programs I needed)

Also, I'm posting on a 6.10 LiveCD now, and I'm not sure if this is the right forum (or whether this is a known problem, I couldn't find anything before I registered to post)

If anyone can think of more information I can send tell me, I don't know what all would help.  And again, I can't access (don't know how, anyway) the main drive because I'm on a LiveCD.

Edit: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/95874](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/95874)
After searching for a long time I found this.  I'm going to try the vesa drivers, althoguh ATI should've worked.

Edit 2: Vesa drivers worked, but ati and fglrx no longer work.  Am I to assume they need to be reinstalled? (I'll try anyway when I get home)

---

