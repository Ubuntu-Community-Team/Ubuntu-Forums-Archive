---
title: "Upgrade to 7.04: Failed To Start The X Server"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Muffy on 2007-04-19
I've just completed the upgrade from 6.10 via System > Administration > Update Manager > Upgrade. Everything went pretty smoothly until the reboot where I get this error: "Failed to start the X server." Upon viewing the diagnostic file, I see this:

```
[R200Setup] X version mismatch - detected X.org 7.2.0.0, required X.org 7.1.0.0
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```

After this I can view a detailed report, then an alert that states "The X server is now disabled. Restart GDM when it is configured correctly." I hit OK, and nothing happens.  After a reboot I still can't find a way to login to Ubuntu. 

How can I fix this?

---

### Post by Muffy on 2007-04-19
OK I seem to have fixed the problem. This is what I did:

After encountering the error I entered the command line interface (Ctrl + Alt + F1).

I logged in.

I typed: sudo nano /etc/X11/xorg.conf

I scrolled down to the heading "Device". There were two Device entries. The fist one was my ATI card using the device "vesa" and the second one I was unsure of, but it was using the device "fglrx" which I recognised from my original error message. I changed "fglrx" to "vesa", hit Ctrl+O (save) and Ctrl+X (exit), restarted my computer and problem solved! 

Now being that I'm somewhat of a n00b I'm not sure if this will have any other effects on the permormance of my PC. So if anyone knows what I've done and thinks I've done it wrong, please let me know!

---

### Post by corefile on 2007-04-19
> **Muffy said:**
> OK I seem to have fixed the problem. This is what I did:

After encountering the error I entered the command line interface (Ctrl + Alt + F1).

I logged in.

I typed: sudo nano /etc/X11/xorg.conf

I scrolled down to the heading "Device". There were two Device entries. The fist one was my ATI card using the device "vesa" and the second one I was unsure of, but it was using the device "fglrx" which I recognised from my original error message. I changed "fglrx" to "vesa", hit Ctrl+O (save) and Ctrl+X (exit), restarted my computer and problem solved! 

Now being that I'm somewhat of a n00b I'm not sure if this will have any other effects on the permormance of my PC. So if anyone knows what I've done and thinks I've done it wrong, please let me know!

Do you have an ATI video card? If so you are gonna want to use the fglrx drivers.

---

### Post by Muffy on 2007-04-20
> **corefile said:**
> Do you have an ATI video card? If so you are gonna want to use the fglrx drivers.

Yeah I do. *eek!*
How can I fix the fglrx?

---

### Post by jgcamp99 on 2007-04-20
You'll have to install it just like you did for Edgy Eft.

---

### Post by jnewm on 2007-04-25
I'm a total noob, and had the same problem after installing Feisty.  Only difference is that my driver is "Radeon" for my ATI Radeon 9000.

Is the fglrx driver better than the proprietary driver?  Cause the ATI driver was working well for me in Edgy (I think).  I'd certainly prefer a non-proprietary driver if it would be relatively similar in speed/quality (I don't do anything bigger than trying to watch a movie now and again).

Also, if the fglrx driver is as good/better, I assume I should just start my xorg.conf on a clean slate, since it's all crazy now.  (When I originally loaded Edgy, everything worked just fine).   How can I tell Feisty just to redo my xorg.conf automatically like when I first installed Edgy?

Thanks so much!

---

