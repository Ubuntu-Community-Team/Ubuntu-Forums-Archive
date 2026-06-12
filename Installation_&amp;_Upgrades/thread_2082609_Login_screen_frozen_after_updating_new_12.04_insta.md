---
title: "Login screen frozen after updating new 12.04 install"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by kprudge on 2012-11-10
Hello - I am brand new to Ubuntu, having installed 12.04 from CD upon purchasing a new laptop a couple days ago.  I had just started researching a problem I was having with speakers/sound when I saw that I had several recommended updates available to install.

After running the updates, my speakers were recognized, but my screen froze at the login prompt.  The mouse pointer could move but not click.  The cursor was in the text box but didn't blink.

I was able to work around it with this: 
```
sudo stop lightdm
startx
```

Then I started troubleshooting other suggestions I found online.  I did not have luck getting into the file to enter nomodeset to /etc/default/grub.  I got the error (gksudo:2669): Gtk-WARNING **: cannot open display:

Under 'Additional Drivers' I activated ATI/AMD proprietary FGLRX graphics driver.  Upon reboot, I got a solid purple screen and the caps lock light on my keyboard flashing.  Holding down the power button to shut down was all I could do.

In System Recovery, I was able to revert back to build 3.2.0-29 (from 3.2.0-32).  Just as it was at the start, I can now log in but have no sound.

My first question is whether I should be downloading any recommended update that appears or do I need to research and decide on each one?

Also, if I re-update, is my best option to try to get nomodeset into the grub file?  Or should I just accept stopping lightdm as a workaround?

I am obviously very much a novice - I don't even know if I am expressing this correctly - but I am looking forward to learning more.  Thank you for your patience and help!

---

### Post by mörgæs on 2012-11-11
Hi, welcome to the fora.

First, please begin with a complete hardware description.

---

