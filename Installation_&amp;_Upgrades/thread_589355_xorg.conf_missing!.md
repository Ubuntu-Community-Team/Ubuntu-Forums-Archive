---
title: "xorg.conf missing!"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by nzstef on 2007-10-24
Hi everyone!
A couple of days ago I upgraded to 7.10 Gutsy on my laptop. It's been working fine until I wanted to try out the Compiz feature. So far I've been running Beryl kinda smoothly, but since Compiz worked  even better on my computer (running on an ATI X700 card) I decided to get rid of Beryl. After deleting Beryl my xserver-xorg went missing and I started with a screen res of 640x480 - I then reinstalled xserver, got my res back to normal but the graphics are still running reeeaalllyyyy slow. The restricted driver for ATI is disabled and my xorg.conf file keeps on getting deleted when I restart X so I have no idea on how to enable the restricted driver! Now I do not have a backup of xorg.conf  and reinstalling xserver doesnt help anything. I'm still a newbie so any help would be appreciated:) Thanks

---

### Post by deadrabbit on 2007-10-29
I'm experiencing a similar thing:

I updated to 7.10, no problem - everything looked fine, and my 1680 x 1050 screen resolution worked. I tried to enable desktop effects, and that didn't work. So I checked my restricted drivers - I found that my nvidia card was disabled. Then I went to /etc/X11/ to back up my xorg.conf before I attempted to install new nvidia drivers - there was no xorg.conf file in the folder! The only file was xorg.conf.nvidia, which I backed up anyway. I attempted upgrading, and now my top video mode is 800x600, and I can't figure out how to roll back. Anyone have any ideas?

Thanks

---

### Post by taurus on 2007-10-29
From a terminal, do

```
sudo cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
sudo nano -w /etc/X11/xorg.conf
```
Scroll down until you get to the Driver and replace whatever it is with "**nv**".  Save it and reboot.

---

### Post by dburnett77 on 2007-10-29
OKeeDOkey, easy.

Next time, don't forget to save, before deleting.

---

### Post by deadrabbit on 2007-10-29
> **dburnett77 said:**
> OKeeDOkey, easy.

Next time, don't forget to save, before deleting.

That's the weird thing though, I didn't delete the xorg.conf file - the OS must have deleted it during the upgrade. I don't know why it was working without it. Anyway, changing "nvidia" to "nv" fixed it - thanks Taurus! I still can't use my nvidia drivers without making it mess up again, but I don't need it - I'm getting a new computer soon anyway.

---

