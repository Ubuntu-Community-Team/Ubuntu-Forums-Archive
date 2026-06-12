---
title: "Upgrade from Breezy OK, but hangs on boot"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by brihas on 2006-06-30
I've managed to upgrade from Beezy and all looked fine until I rebooted. Now it hangs on the boot Kubuntu screen. It goes through all the mounting etc. and the last message I see is "anacron" before it briefly goes to a text only screen followed by the Kubuntu logo screen, where it stays indefinitely.

Any thoughts on how to troubleshoot this?

Thanks
brihas

---

### Post by Scunizi on 2006-06-30
I'm not sure if this will help or not, but I've found booting into gnome with a usb memory stick will make the system hang on boot.  After removing it all is well.

---

### Post by brihas on 2006-07-01
Thanks, but it does not seem to be a USB memory stick issue.

I decided to leave it on the Kubuntu screen for a while, and finally the computer came back to life and now it says:
Restarting Common Unix Printing System:cupsd - OK
Restarting sytem log... - OK

Now it is frozen again at this point, and has been for quite a while.

One thing I did notice in the earlier boot messages is that the "Starting PCMCIA services" Failed. But as this is a desktop computer is that an issue?

---

### Post by brihas on 2006-07-01
I just tried booting with the "Recovery Mode" option from Grub and I get a root prompt. Trying "startx" shows me that my NVIDIA drivers are not loading OK. It looks like the upgrade process un-installed them so I re-installed via "sudo apt-get install nvidia-glx", then "startx" works OK.

Just rebooted and now all is working OK :-)

---

