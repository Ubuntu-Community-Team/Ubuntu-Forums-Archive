---
title: "Hardy No fonts in X"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by thwint on 2007-12-04
I'm running Hardy since Gutsy was finally released. So far there was no problem because I really carefully upgraded.

Before upgrading essential packages on my base installation i upgrade it in a virtual machine to see if everything is working fine.

Now I did the same again and run an upgrade again on my system. Since this upgrade I can't see any fonts when starting X.

On the console fonts are displayed as usual. As soon as I start with the logon manager no fonts and images are shown.
Logging into my system I can't see the username. I can see a cursor moving when I type, but it seems, that I'm using a white font on white background. After logging in, I can click on menus but cant see any fonts or images. 

My transparent Eterm, which I integrated into my desktop shows the fonts, but when starting a gnome-terminal from within an Eterm the gnome-terminal becomes useless (no font visible).

Is there anything I missed with my last upgrade? And even more important is there a way to get the fonts back?

In the log files I can't find anything about missing fonts...

---

### Post by briandu on 2007-12-04
May i suggest the following:
On boot go to Safe Terminal (NOT GNome/KDE) and then fire off the following:

sudo apt-get install fontconfig

sudo apt-get install defoma

sudo apt-get install msttcorefonts

and this should ensure a minimum set of fonts are installed on your PC  -- note there are quite a few dependencies that will be d/loaded.

Good luck

---

### Post by thwint on 2007-12-04
This didn't help anything. It only installed the msttcorefonts. After restarting gdm I still have no visible font.

---

### Post by briandu on 2007-12-04
Well now we know your font files are installed for sure

OK so it seems that you xserver is acting up 



SO first goto /etc/X11
sudo cp xorg.conf xorg.conf.20071204

then fire off 

sudo dpkg-reconfigure -phigh xserver-xorg

this will ensure the xserver is basically matched to your video.

---

### Post by thwint on 2007-12-04
I already created a new xorg.conf several times. So I did the same again without any changes.

even if I start X from the command line I can't see any fonts. Everything seems to work, but as I can't read anything it is difficult to test many things.

---

### Post by briandu on 2007-12-04
I am afraid yo have got me there. For some reason the gdm does not pick up the fonts. not sure why. Can help you from here :confused:

---

### Post by thwint on 2007-12-04
I think it is not only limited to gdm. 
To try out more options I started X from the command line (startx) which doesn't use gdm and I installed kdm

No matter what I used to start X the result was the same: No visible font.

I try to find out which packages have been installed this morning.

---

### Post by thwint on 2007-12-04
I attached an extract of the term.log file in /var/log/apt.

basically the upgrade removed the old gutsy xorg packages and installed the new hardy packages.

---

### Post by PmDematagoda on 2007-12-04
The upgrade may not have gone well for you, my Hardy clean install works rather well enough.

---

### Post by thwint on 2007-12-05
I opened a bug report
[https://bugs.launchpad.net/ubuntu/+bug/173920](https://bugs.launchpad.net/ubuntu/+bug/173920)

In the mean time I found a workaround by disabling splash in the grub config.

---

