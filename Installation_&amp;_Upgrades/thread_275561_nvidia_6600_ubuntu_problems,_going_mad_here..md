---
title: "nvidia 6600 ubuntu problems, going mad here."
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by chrisjentys on 2006-10-11
Hi, im hoping someone can help me out here.

im trying to install Ubuntu on the following hardware;

Gigabyte 3d1 dual 6600GT pci-e(The card with 2 gpus on one bit of silicon)
Gigabyte K8nxp-sli mobo
1 gig ram
amd 64 3500+

sata raid array, though Ive dissabled this (in bios) and am tring to install to a old 10gig ide drive.

The first thing I tried was an install of the x64 version of ubuntu from a live cd. the system just hangs part way through loading X. I tried 32 bit versions too with the same result. Apparently its a gfx driver issue.

I read up on this and tried using the alternate installer and then changing the xserver config to use vesa/vga but I cant find a configuration that works. Now ive read somewhere that vesa doesnt work with pci-e cards but Im not getting anywhere with the vga options either. 

I really want to switch to linux and get rid of windows but every time i try its an uphill struggle.

Please help me exorcise M$ from my PC!

Thanks in advance.

Chris.

---

### Post by whizbaby on 2006-10-11
You could try to install a server version and setup X later (you still can install paackages and browse the web with the progs *w3m* or *links*).
I think your problem is that the free *nv* driver doesn't work properly with your card and the proprietary *nvidia* driver (nvidia-glx) is in a repository not enabled in the standard install (because it's proprietary). So you would have to enable universe and multiverse in the server install and install X (e.g. with **sudo apt-get install ubuntu-desktop**) and the nvidia driver ([https://help.ubuntu.com/community/Latest_Nvidia_Dapper)](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)).
EDIT:
Here you can find some answers and guides
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

---

### Post by Phlee on 2006-10-12
Did you try removing 1 Video card from your SLi stack?

I had the same problems with my 6800's.  It would hang before X would run.  Come to find out, it was a conflict with the video cards.

Get Ubuntu running on a single card.  Install Nvidia drivers, and install the second.

Cheers

---

### Post by Coelocanth on 2006-10-12
> **Phlee said:**
> Did you try removing 1 Video card from your SLi stack?

I had the same problems with my 6800's.  It would hang before X would run.  Come to find out, it was a conflict with the video cards.

Get Ubuntu running on a single card.  Install Nvidia drivers, and install the second.

Cheers

It's not a two-card SLI set-up. It's a single card with dual graphics cores.

---

### Post by redbull_monsta on 2006-10-12
Have you tried to install with no frame buffering?

I cant remember the option as im sat at work but normally 'nofb' F1 after booting from cd/dvd should show you the options....

Regards

redbull_monsta

---

### Post by fokuslee on 2007-01-03
the only solution is to buy 2 cards for sli 
gv-3d1 is unsupported from the kernel level 
as u can see from lspci -t 
also do a search for gv-3d1 you will see my post
im sorry but sli is not gonna work with your current card 
i had the same card and i swapped them for two 7600gt 
aye good luck

---

