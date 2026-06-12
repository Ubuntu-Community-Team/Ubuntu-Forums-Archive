---
title: "Lubuntu 14.04 flashing screen."
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by voodoo_child on 2014-07-12
Hi,
I have done a clean install of Lubuntu 14.04 i386 (alternate) on my [IBM X21.]("http://www.thinkwiki.org/wiki/Category:X21") Previously I ran Lubuntu 10.04 and 12.04 with no problems. 

I didn't bother to try the 14.04 LiveCD because I only have 384MB ram. I verified the ISO download and disc burn. 

On boot it displays the Lubuntu splash screen as normal, but when it gets to the desktop environment it shows a blank wallpaper (with some white boxes and a cursor) for a split second, then flashes to black, then tries to draw the desktop again, flashes to black, and so forth. 


Please advise the troubleshooting procedure. I believe the problem to be video related. Thanks

---

### Post by slooksterpsv on 2014-07-12
I'd try booting and appending nomodeset to the grub command. When you turn on the computers press and hold SHIFT and it should show the GRUB boot options. Press e to edit, go down to the line that has "quiet" in it and add to the end of that line  nomodeset

Now try booting. I've seen another thread with a Compaq Armada where lubuntu doesn't work but LXLE does - [http://lxle.net/](http://lxle.net/)

Check out LXLE; Lubuntu may be modified in such a way to where too old of graphical components don't work, but the LXLE spin may have mods where it will work with older hardware like yours.

---

### Post by voodoo_child on 2014-07-12
Hi,thanks for the reply.

Adding nomodeset did not seem to have any effect. 

I will try LXLE if I cannot get this working.
---on second glance,  LXLE seem to be using 12.04 for their latest 32-bit version but I was hoping for something more recent. I already had Lubuntu 12.04 working.

---

### Post by slooksterpsv on 2014-07-13
Dang, yeah waiting for 32-bit, I tried contacting them, but a 32-bit revisited is all. Maybe the 32-bit will be able here in a few weeks. I would hope so.

---

