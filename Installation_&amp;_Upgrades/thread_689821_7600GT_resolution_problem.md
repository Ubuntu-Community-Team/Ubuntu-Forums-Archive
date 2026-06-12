---
title: "7600GT resolution problem"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by keplenk on 2008-02-06
Hi all,

I might say, Ubuntu rocks!

I'm very noob at Ubuntu and I am really trying to learn.  I did watch/read some basics tutorials before I installed.

So far, I've installed Ubuntu 7.10 successfully (thank goodness, it supports AHCI).  I installed the Restricted Drivers for Nvidia.

After installing it and restarting the PC, I now have 3D .. I tried to play with some Visual Effects in appearance at it was fine.

However, when I try to change the resolution of my PC, I noticed that its limited.  The maximum resolution it gives me as an option to click is 1024x780 only .... I know for a fact that my Video card and monitor can support up to 1280x1024 60hz << I've tried it in Windows XP

*I also noticed that BEFORE I installed the restricted drivers for Nvidia, I can choose higher resolution, ofcourse 3D is disabled.

Could this be a faulty driver installation? What can I do to maximize my resolution in Ubuntu.

Specs:

E2180 running at 2.0 stock speed
GA-P35-DS3L rev 2.0 F5 bios
Inno3D 7600GT 256mb/256bit ddr3
Samsung DVDrw - SATA
80gb WD SATA hdd
80gb maxtor IDE hdd
2 x 1gb A-DATA Vitesta 1.8v
Antec EA380
17' SyncMaster 793df CRT flat monitor (damn those brown lines!!)

Thank you so much!!

---

### Post by bwtranch on 2008-02-06
Overclocked?

---

### Post by keplenk on 2008-02-06
No sir, its not overclocked :) and never overclocked .. yet

All hardware is running @ stock speed.

:D

Thanks for your reply.

---

### Post by overdrank on 2008-02-06
> **keplenk said:**
> Hi all,

I might say, Ubuntu rocks!

I'm very noob at Ubuntu and I am really trying to learn.  I did watch/read some basics tutorials before I installed.

So far, I've installed Ubuntu 7.10 successfully (thank goodness, it supports AHCI).  I installed the Restricted Drivers for Nvidia.

After installing it and restarting the PC, I now have 3D .. I tried to play with some Visual Effects in appearance at it was fine.

However, when I try to change the resolution of my PC, I noticed that its limited.  The maximum resolution it gives me as an option to click is 1024x780 only .... I know for a fact that my Video card and monitor can support up to 1280x1024 60hz << I've tried it in Windows XP

*I also noticed that BEFORE I installed the restricted drivers for Nvidia, I can choose higher resolution, ofcourse 3D is disabled.

Could this be a faulty driver installation? What can I do to maximize my resolution in Ubuntu.

Specs:

E2180 running at 2.0 stock speed
GA-P35-DS3L rev 2.0 F5 bios
Inno3D 7600GT 256mb/256bit ddr3
Samsung DVDrw - SATA
80gb WD SATA hdd
80gb maxtor IDE hdd
2 x 1gb A-DATA Vitesta 1.8v
Antec EA380
17' SyncMaster 793df CRT flat monitor (damn those brown lines!!)

Thank you so much!!

HI and you can try to adjust the resolution using nvidia-settings ```
gksudo nvidia-settings
```

---

### Post by keplenk on 2008-02-06
Wow, that was fast and easy.

It worked :)

Thank you so much. :D

---

### Post by keplenk on 2008-02-06
Hi again :(

I thought that it was fixed.  Well you can actually change the resolution by 

doing code:

gksudo nvidia-settings

However, when I reboot the PC, it comes back to 1024x768 resolution and I have to do gksudo again to change it back to the resolution it wants.

Is there a way to change the resolution and hold that resolution?

Thank you.

---

### Post by bwtranch on 2008-02-06
I would look at the file /etc/X11/xorg.conf

Use an editor like gedit or nano. Be careful with this one!!!

---

### Post by keplenk on 2008-02-06
> **bwtranch said:**
> I would look at the file /etc/X11/xorg.conf

Use an editor like gedit or nano. Be careful with this one!!!

Hi,

I've actually checked at it.  Do I have to change something in there?  I'm really a noob in Linux, sorry :(

I've looked at the resolution at the bottom of the file and noticed that all resolution is set correctly.

Everytime I reboot, it goes back to the 1024x768 resolution.  It doesnt hold the resolution before I restarted.

Thanks again :D

---

### Post by keplenk on 2008-02-06
Hi,

I made some progress and I didn't do anything.  For some reason, I tried to reboot and viola, resolution is held.

I didn't do anything.  I just opened xorg.conf using gedit .. browsed it down.  Didn't touch a thing .. and restarted, its now fine.

One last problem though, when I set my resolution to 1280x960 .. the only option for refresh rate is 51hz, nothing else.  When I try this in windows (using the 1280x960 reso), I can use 60hz.

Is there a way to force or configure this setup so I can choose 60hz?

Could this be that nvidia autodetects the right refresh rate for each resolution?

I was just hoping that I could choose 60, because this monitor can handle 60hz at 1280x960 in Windows XP.

THank you so much.

---

### Post by crjackson on 2008-02-06
Okay, I was having issues with my 7900GTO and here's what I found. Go the to terminal and type gksudo nvidia-settings to bring up your settings manager.

Then adjust your resolution AND refresh rate.  Then at the bottom of the applet, there is an option to save the settings to the xorg.conf file.  I did that and it worked fine.

HOWEVER

Afterwards if you uses the Ubuntu screen resolution applet it will give you false information about your refresh.  You can use your monitors menu options to report the ACTUAL refresh, and you can use the nvidia-settings applet an it will tell you the ACTUAL refresh rate.

The Ubuntu applet is not accurate.

---

