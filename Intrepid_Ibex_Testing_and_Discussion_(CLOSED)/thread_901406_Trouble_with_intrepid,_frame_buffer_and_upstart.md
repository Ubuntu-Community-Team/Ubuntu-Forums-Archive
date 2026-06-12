---
title: "Trouble with intrepid, frame buffer and upstart?"
date: 2008-08-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AvitarX on 2008-08-26
I am having some trouble after recently upgrading to intrepid.

I don't believe this is a bug, so much as a configuration issue I may have created.

I have been using Linux for a long while (Since before the parts giving me trouble were mainstream), and usually can fix these thing/find someone's post where it is fixed, so if this is the wrong venue I apologize.

I think the trouble I am having is related to upstart not working correctly (I was able to pretty much fix it by adding stuff to /etc/rc.local).

My troubles are:
when booting normally I have no virtual consoles visible, gdm does not start, and I get no IP address.

When in recovery mode, then continue normal boot I virtual consoles with no frame buffer, gdm does not start and I get no IP  address.

When booting with ```
vga=795
``` and ```
splash
``` removed from grub I get no gdm or IP, and obviously no frame buffer.

even when the virtual console is blank (blinking white underscore in the top left position, nothing else) I can log in, run ```
sudo gdm
``` and get started with X, then run ```
sudo dhclint
``` and get in IP.

Also perhaps related is that I have Geforce 6600 card, it says in-use, but not enabled.

This is an upgrade from Hardy.

Thank you to anyone who can perhaps point me in the correct direction.

PS
I have tried re-installing many packages, and purging some and re-installing them.

---

### Post by Nullack on 2008-08-26
Thats all bugged on Intrepid right now. Dont run custom vesa modes on the framebuffer and I recommend turning off usplash until some fixes come through for new testing. Have a look on launchpad for the bugs.

---

### Post by AvitarX on 2008-08-26
Sorry to be dense, but could you nudge me in the correct direction at launchpad, or where to get errors?

I have no fails in boot, and can't seem to find a search that turns up the isue in launchpad, or the internet at large.

---

### Post by Nullack on 2008-08-26
Here ya go mate:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/243682](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/243682)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

---

