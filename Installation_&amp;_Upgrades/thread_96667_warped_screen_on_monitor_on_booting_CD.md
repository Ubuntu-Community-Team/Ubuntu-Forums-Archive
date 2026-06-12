---
title: "warped screen on monitor on booting CD"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by softgun on 2005-11-29
Hi everyone,

This is my first post. I want to use Ubuntu and tried to install to my PC running Mepis. When I booted with the CD, the screen gives a hourglass look, and I was a bit concerned and stopped the installation. I have a Phillips monitor and the graphics are from the Intel graphics on the motherboard.

When the install screen starts I presume it is using VGA, but anyone know what resolution it is set to? Either it is not getting the monitor right or it is setting the refresh rates wrong.

What can I do? Install anyway and then change the xorg.conf file?

Thanks for all replies.

---

### Post by Topsiho on 2005-11-29
I am not sure that I get it right:

1. You are installing Mepis, which is not the same as Ubuntu.
So this is the wrong forum to ask about a Mepis install.

2. You get an hour glass when booting. This means I think that you must have some patience and wait. I was about to ask what made you think that your monitor settings were not right? But you have to get your answers somewhere else: google for    Mepis forum    and you will find people there to help you :)

Greetz and success with your Mepis,

On second reading of your post I get that you have Mepis on it but want to install Ubuntu (on top or next to it?).

When installing Ubuntu you have to have room to put it into, but whether you have Windows or another operating system or nothing is not relevant until it has to be detected by Grub when installing Grub.

See when you start the install, with I think F1, which options you get.

Topsiho

Topsiho

---

### Post by wrtrdood on 2005-11-29
No he said an "hourglass look".  This is the displayed raster of the monitor squeezing in the middle of both sides and it does look a bit odd.  This is known as pincushion and is usually easily adjustable through the monitor's controls.  I have one that does the same thing, usually because the resolution changed to something higher. Some monitors are intelligent enough to save the change you make through the use of the OSD controls so that the next time you use this resolution, it will remember the settings.  You probably have not used that particular resolution before and that's why you're seeing this symptom.  It will not harm the monitor and there's no reason not to continue the install.  If you have to adjust the display using knobs (as I do) then you'll have an opposite effect if you go back to the other resolution.

Changing the xorg.conf file will not change the symptom since it's a hardware issue.  You could certainly limit the resolution to one that does not appear this way, however.

---

### Post by bwog on 2005-11-29
I think wrtrdood is right. When the pincushion is not very severe and you can read the screen well, you can just continue to install.

The resolution of the install screen is not important. After installation, you install video drivers and can select resolutions that are right for your card and monitor. Perhaps the pincushion effect will be gone then.

---

### Post by softgun on 2005-11-30
Thanks!

I will go ahead and install. I feel Ubuntu is a very promising distro and that is why I am going to replace Mepis with it.

---

### Post by teaker1s on 2005-11-30
should your display look odd or you get only text login use
sudo dpkg-reconfigure xserver-xorg to adjust settings:KS :KS

---

### Post by Topsiho on 2005-12-01
[QUOTE=wrtrdood]No he said an "hourglass look".  This is the displayed raster of the monitor squeezing in the middle of both sides and it does look a bit odd.  This is known as pincushion and is usually easily adjustable through the monitor's controls.  I have one that does the same thing, usually because the resolution changed to something higher. Some monitors are intelligent enough to save the change you make through the use of the OSD controls so that the next time you use this resolution, it will remember the settings.  You probably have not used that particular resolution before and that's why you're seeing this symptom.  It will not harm the monitor and there's no reason not to continue the install.  If you have to adjust the display using knobs (as I do) then you'll have an opposite effect if you go back to the other resolution.

Changing the xorg.conf file will not change the symptom since it's a hardware issue.  You could certainly limit the resolution to one that does not appear this way, however.[/QUOTE]


I guess you are right, sorry for my misunderstanding. The word "hourglass" made me jump to a wong conclusion.

Topsiho (one time is quite enough :) )

---

### Post by wrtrdood on 2006-01-24
No biggie.  It's just that I've adjusted my fair share of monitors (27" and down) and understand these descriptions better than most.  :)

---

