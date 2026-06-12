---
title: "Upgrade problem for Laptop"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Q2299 on 2010-08-09
I have installed UBUNTU 8.10 in my laptop.
Lots of trouble to get the wireless working. Now that is fine.
Next problem... NOT ABLE TO UPDATE WITH UPDATE MANAGER.
The message we get is:
"Please insert the disk labeled:
Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)
in drive /cdrom/"

Then after I insert the same disk I used to install UBUNTU... I get this message....
"This medium contains software intended to be automatically started. Would you like to run it?
The software will run directly from the medium "Ubuntu-Netbook 10.04 i386". You should never run software that you don't trust.

If in doubt, press Cancel."

What is the solution to this any ideas?

---

### Post by snowpine on 2010-08-09
It looks like you are actually running 10.04 (not 8.10, which is no longer supported).

Assuming you have an internet connection, all you need to do is go System, Administration, Software Sources and uncheck the Ubuntu CD-ROM. 

Now, try updating again. It should skip the CD-ROM and go onto the Web to get the latest updates.

---

