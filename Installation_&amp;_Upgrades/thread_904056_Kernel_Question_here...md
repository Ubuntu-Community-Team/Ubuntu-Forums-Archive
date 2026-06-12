---
title: "Kernel Question here.."
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by bhart007 on 2008-08-28
Hi all.. just xferred over from PCLOS Gnome.  I loved PCLOS but the lack of support both in number of devs and on the forums was too much to bear any longer.  I used PCLOS Gnome for about 7 months so I'm not a total noob.

Anyway I'm wondering, on a fresh install of Hardy, have there been any issues associated with upgrading the kernel from 2.6.24.21-generic to the RT version?  Forgive me if this has already been asked.. I didnt notice a kernel specific topic area.

Thanks!

---

### Post by cariboo on 2008-08-29
You can use Synaptic Package Manager to install other kernels, or you can install Ubuntu Studio and get the real time kernel by default.

Jim

---

### Post by Thelasko on 2008-08-29
```
sudo aptitude update
sudo aptitude install linux-rt
```
I think it's much easier than installing UbuntuStudio.

---

### Post by bhart007 on 2008-08-29
So let me get this straight.. you just choose to download and install a different kernel thru Synaptic.. which will be configured, make'd and everything.  Then be added as a choice in grub?  Holy crap!

---

### Post by Shazaam on 2008-08-29
> **bhart007 said:**
> So let me get this straight.. you just choose to download and install a different kernel thru Synaptic.. which will be configured, make'd and everything.  Then be added as a choice in grub?  Holy crap!

Yep. If it's available in Synaptic or the update Manager it is that easy. Welcome to Ubuntu.

---

### Post by bhart007 on 2008-08-29
Niiice.  Well I guess honestly it's almost the same as it was in PCLOS.. except for the added support of more than 1 other kernel. SWEET!

---

