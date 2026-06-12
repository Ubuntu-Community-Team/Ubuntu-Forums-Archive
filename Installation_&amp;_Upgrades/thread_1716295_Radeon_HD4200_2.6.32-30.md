---
title: "Radeon HD4200 2.6.32-30"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by tracyapotter on 2011-03-28
I am running Kubuntu 10.04 LTS and have had no problems with my ATI card up to kernel 2.6.32-29.  Upon update/upgrade to 2.6.32-30 the FGLRX driver will not load graphics and I can only get the text system login.  If I reboot to -29 everything works great.

Where do I start?

---

### Post by Sean Moran on 2011-03-28
> **tracyapotter said:**
> I am running Kubuntu 10.04 LTS and have had no problems with my ATI card up to kernel 2.6.32-29.  Upon update/upgrade to 2.6.32-30 the FGLRX driver will not load graphics and I can only get the text system login.  If I reboot to -29 everything works great.

Where do I start?
After logging into the text interface, (and prefix with 'sudo' if you're not root, do you get any readable error messages by entering the following two commands:

xinit
startx

Others might know better ways to sort this out, but that's the best I can think to try to determine what might have stuffed up your X-Windows configuration.

---

### Post by Dutch70 on 2011-03-28
You might want to try to log-in to 2.6.32-30 & update your system from there. You should be able to log-in to it by hitting cntl+alt+F7, then  log in and type "sudo startx" without the quotes. Then...
```
sudo apt-get update && sudo apt-get upgrade
```

Reboot and try to log in to 2.6.32-30 again.

Otherwise, if you can't find a better solution, you probably already know this, but you can go to synaptic, search for linux-image-2 and remove 2.6.32-30, be sure not to remove the wrong one.

---

