---
title: "Touchpad doesnt work with ubuntu; Help !"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by West201 on 2010-08-03
I just installed ubuntu v10.04 yesterday as a dual boot; but the touchpad hasn't worked at all with ubuntu. I had to TAB to select my options to install it. The mouse is just frozzen. The mouse work perfectly with Windows 7.. Im obviously not computer literate just wanted linux because coworker recommended it over Micosoft. 
 
Computer Specs: Sony laptop, 4gb ram, 2.10 GHz, 500gb HD. 
 
a million thanks for helping :KS

---

### Post by West201 on 2010-08-04
**I just  installed ubuntu v10.04 yesterday as a dual boot; but the touchpad  hasn't worked at all with ubuntu. I had to TAB to select my options to  install it. The mouse is just frozen. The mouse work perfectly with  Windows 7.. I'm obviously not computer literate just wanted linux because  coworker recommended it over Microsoft. **
 
**Computer Specs: Sony laptop, 4gb ram, 2.10 GHz, 500gb HD. **
 
**a million thanks for helping :KS**

---

### Post by lechien73 on 2010-08-04
There's a blog post here: [http://uri.tl/s](http://uri.tl/s) which details how to install Ubuntu 10.04 on a Sony Vaio, and have the touchpad working.

Hope it helps.

---

### Post by corrytonapple on 2010-08-04
Get a external mouse and go to **System>Administration>Hardware Drivers**. Install drivers for your trackpad and restart.

---

### Post by Iowan on 2010-08-25
Threads merged, duplicate removed, formatting normalized.
Please review the Code of Conduct:> # Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.
[COLOR="Silver"]# Typos and other errors can cause miscommunication between users on the forums, please preview your text before posting.[/COLOR]
# Please do not cross post, or post the same thing in multiple locations.

---

### Post by West201 on 2011-01-08
I just got the touchpad to work by editing 
/etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"

sudo update-grub

reboot

---

### Post by corrytonapple on 2011-01-08
That is great to here! ;)  I will note that as a fix for anyone else with a not-working touchpad.

---

