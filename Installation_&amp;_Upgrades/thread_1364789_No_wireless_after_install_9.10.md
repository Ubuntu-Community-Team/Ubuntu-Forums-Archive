---
title: "No wireless after install 9.10"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Prof4Jesus on 2009-12-26
I have a Gateway model 6000 laptop that is running dual boot with Ubuntu & Win XP.  I did a fresh install to upgrade to Ubuntu 9.10.  My internet is not working at all-including hard wiring to the ethernet cord.  I've tried everything I know, help is appreciated.

---

### Post by XIIIth on 2009-12-27
Hi,
Type in lspci in the terminal. That will bring up all the devices on you laptop. Find you wireless card.
I am using a broadcom and if you too happen to use the same then follow this
System--> Administration-->Synaptic Package manager

type in broadcom
mark bcmwl-kernel-source for installation and apply changes.
Reboot your system.
The wireless gets activated.

you will have to mess around a bit with the settings once its done. But thats just typing in the passwords etall.
Hope it helps

regards,
xiii

---

### Post by Prof4Jesus on 2009-12-27
I've been offline, thanks for the reply.  I do have the issue of NO internet at all.  I didn't realize that until I tried to plug in the eth cord.  I have access to another computer still running 9.04.  Is it possible to download what I need and save to flash drive and load to the other computer?

---

### Post by Ginsu543 on 2009-12-28
It might be helpful if you posted your result of the lspci command. While it is fairly common for the wireless networking to not work out of the box, it is more troubling that your wired networking does not work either.

If all else fails, you might consider backing up your important data and installing 9.10 fresh, rather than upgrading from 9.04. Sometimes the upgrade process doesn't take care of everything it should.

---

### Post by Prof4Jesus on 2009-12-28
Thanks everyone who replied to this thread.  Problem resolved by FIRST plugging in the ether cord for internet, then reinstalling 9.10.  Ubuntu found and established all internet connections.  I think the key is to have the internet connected during installation..duh.  Appreciate all the help.

---

### Post by Ginsu543 on 2009-12-28
Good to hear you got it all working!

---

