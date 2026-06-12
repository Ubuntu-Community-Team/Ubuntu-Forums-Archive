---
title: "[SOLVED] major graphics issue after kernel update"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by gmxgeek on 2008-08-17
I have recently upgraded my kernel to x.x.x.21
As soon as i rebooted, it went into low graphics mode.

I thought it would be no problem, but my graphics card (nvidia 8600GT) does not show up at all under hardware drivers, and EnvyNG doesn't fix it either.
I am currently only able to run on 800x600 res.

I have tried booting back into x.x.x.19, but to no avail. Any ideas?

---

### Post by Pumalite on 2008-08-17
How did you install your video driver in your previous kernel?

---

### Post by gmxgeek on 2008-08-17
I used EnvyNG. Also, my sound is broken, but i prefer gfx over sound in terms of urgency

---

### Post by Pumalite on 2008-08-17
Have you tried envyng again? You can also go into Recovery Mode and use the command 'xfix'

---

### Post by gmxgeek on 2008-08-17
Have tried envyng again, but it doesn't really work. I get more resolution options, but none above 640x480. Will try xfix

---

### Post by gmxgeek on 2008-08-17
Okay, so now graphics are up and running again. Thank you very much. Any idea on what to do about sound?

EDIT:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

---

### Post by Pumalite on 2008-08-17
Post:
lshw -C sound

---

### Post by gmxgeek on 2008-08-17
fieldsm@GATZ:~$ sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

---

### Post by Pumalite on 2008-08-17
Bad news. Your new kernel is not recognizing your card and not loading the module. Try opening all your repos except src and do a:
sudo apt-get update
sudo apt-get dist-upgrade
Reboot
Then post again:
lshw -C sound

---

### Post by gmxgeek on 2008-08-17
all my repos are open, except for backports..

---

### Post by Pumalite on 2008-08-17
Backports are essential.

---

### Post by gmxgeek on 2008-08-17
ok. I will open them up then

---

### Post by gmxgeek on 2008-08-17
*-multimedia UNCLAIMED  
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2


Rebooted, and am now in low graphics mode again :(
Will run xfix once more

---

### Post by gmxgeek on 2008-08-17
Ok, i have good res now, but still no sound, and also, i get a GLIB error on shutdown about a bad key or something.

---

