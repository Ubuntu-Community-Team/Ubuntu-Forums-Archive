---
title: "Edgy Upgrade Boot Freeze on Splash Screen"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by WoodyMahan on 2006-12-05
OK so I didn't upgrade using the official method.  I changed the repo's and ran the upgrade that way.  Everything seemed to be going fine, but after the install completed and requested a restart, my Ubuntu boot freezes on the splash screen.

I am running Ubuntu as a virtual machine on my Vista computer.  This is kind of my test machine that I use to play with stuff before I load on my live Ubuntu Laptop. (VMware Server)

How do I get the machine to boot directly to a command line, and then where do I start troubleshooting?  I'm 99% sure that I have an x-server issue, just not sure what to fix first.

---

### Post by WoodyMahan on 2006-12-05
Bump

---

### Post by yiannos on 2006-12-08
Same problem here.

Clean install Kubuntu Edgy on a vm. It boots only if I select recovery mode and then press Ctrl-D

---

### Post by yiannos on 2006-12-08
OK I dont know if what I did was correct (I would appreciate any insight on this) but it now works fine.

I edited /boot/grub/menu.lst and removed any entries named 'splash' and/or 'quiet'.

The system now boots without freeze every time.

Yiannos

---

### Post by WoodyMahan on 2006-12-15
I just re-formatted and installed Lin as the base OS and installed WIndows as the Virtual (been wanting to do this anyway).  Had no reason not to.  This string can be closed.

---

