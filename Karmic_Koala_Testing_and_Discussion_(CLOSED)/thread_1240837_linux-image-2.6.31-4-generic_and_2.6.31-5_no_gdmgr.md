---
title: "linux-image-2.6.31-4-generic and 2.6.31-5: no gdm/graphical session (nvidia)"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2009-08-15
Hi all,

I am using karmic alpha 4 with all the latest updates installed. When kernels 2.6.31-4 and 2.6.31-5 are loaded, I am presented with a command line instead of the GDM login screen. I think it has something to do with the nvidia drivers, I am using version 180 and I have a nVidia GeForce 6200.
I already filed a bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406339](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406339)), but as there is no reaction yet, I hoped someone here would know a solution to this.
It works perfectly with older kernel versions, however.

Cheers,

Ruben

---

### Post by philinux on 2009-08-15
Not seeing this here.

---

### Post by plun on 2009-08-15
You can try to reinstall the driver from command line

```
sudo apt-get install --reinstall nvidia-glx-180
```

---

### Post by martinpm24 on 2009-08-15
did you try to change the config to use driver nv, to discard that the problem is nvidia?

sudo nano /etc/X11/xorg.conf

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nv"
EndSection

---

### Post by rubenverweij on 2009-08-15
Thanks for your replies.
I have tried both suggestions, first reinstalled the nvidia driver, then used nv instead of nvidia.
With the nv driver, I got a message from my monitor stating "Input signal out of range". This has probably something to do with my dual monitor setup in twinview. Maybe I can get an image with one monitor unplugged, I will try that now and then post back again.
Thanks again for your help.

---

### Post by phenest on 2009-08-15
> **rubenverweij said:**
> With the nv driver, I got a message from my monitor stating "Input signal out of range".

That usually means you have set the resolution too high for the monitor.

---

### Post by rubenverweij on 2009-08-15
Yes, as I was saying, I have two monitors in TwinView mode, so the resolution is 2560x1024 instead of 1280x1024. I have unplugged one monitor, with the nv driver and 2.6.31-5 it works on one display. I was unable to configure the second screen however. But I think we can conclude that the problem is with the nvidia driver. Does anyone has a suggestion on how to solve this? :)

---

### Post by dabl on 2009-08-15
I noticed I had to reinstall the nVidia driver yesterday, after a big dist-upgrade.  There must have been some revision to the kernel -- I saw kernel 2.6.31-5 references during the upgrade.  I took the "opportunity" to try the new 190.18.03 Open GL beta driver, and it seems to be working just fine.

---

### Post by rubenverweij on 2009-08-15
Thanks dabl for that! 
I tried to install the latest nvidia driver and in the process found out that linux-headers and linux-headers-generic weren't installed for some reason. That fixed the problem.

---

