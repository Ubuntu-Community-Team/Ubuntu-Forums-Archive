---
title: "Black Screen on Macbook Pro 6,2 After Installing 12.04LTS - Tried Everything Already"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by jart16 on 2013-07-31
I am tri-booting Mac OS 10.6.8 (Snow Leopard), Windows 8, and Ubuntu. I installed via a USB drive. The install and the LiveCD trial went flawlessly, and I can boot into GRUB. However, as soon as I press Enter on the installed Ubuntu, it brings me to a black screen. I left it there for about an hour, and it was still black. No words or anything. The video card is an nVidia 330M. I tried 13.04, and that worked, but it wasn't 100% compatible, so I much prefer the LTS. So far, I have tried:

Failsafe Graphics
Reinstalling
Putting nomodeset and no splash in GRUB
The custom Mac LiveCD (wouldn't boot from the USB drive)
Adjusting my brightness (believe it or not, that's a common solution)
Switching graphics mode through GRUB (got a garbled mess, but I think Unity was running in there somewhere because my backlit keyboard lit up)
Entering --quiet splash nomodeset and quiet splash nomodeset (brought me to the splash screen with orange dots, then kicked me back out to a totally black screen)
Pressing Esc during the splash screen (gave me a bunch of checks, all came back [OK], but kicked me to the black screen again)
Keep in mind, I'm kind of a beginner. I know much more than the average beginner, but I wouldn't call myself intermediate just yet.

One more thing: the black screen I'm getting is NOT backlit, and there is NO blinking cursor. It looks as if I turned the computer off, but the fans are still running and I think the hard drive is still doing something)

---

### Post by yeats on 2013-07-31
You might want to look in the Xorg logs (/var/log/Xorg.0.log) for lines containing "(EE)".  They should point to the error(s).

---

### Post by jart16 on 2013-08-01
> **yeats said:**
> You might want to look in the Xorg logs (/var/log/Xorg.0.log) for lines containing "(EE)".  They should point to the error(s).

(EE) Failed to load module "nv" (module does not exist, 0) 

I looked up a fix, but how do I apply it via recovery root or LiveUSB? These solutions assume that you can get into Gnome in the first place

---

### Post by maxbar on 2014-03-31
Could you please post what you did to fix the issue? It's been quite a few months since your post, so I'd imagine that you have gotten this resolved?

Thanks!

---

