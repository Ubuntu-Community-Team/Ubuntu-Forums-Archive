---
title: "enabling usb kb &amp; mouse support broke my gutsy 64"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by mangoes on 2008-02-09
Hi all,

I'm a complete noob (2 wks with ubuntu) , please help me.

My usb keyboard & mouse did not work with GRUB, but worked ok once ubuntu was loaded.

So during startup I enabled usb keyboard & mouse support in BIOS (legacy usb support was already enabled). This resulted in two things:

a) GRUB recognized my keyboard (I could switch between OS)
b) If I choose ubuntu as os,  one of these happens
      1) The computer keeps rebooting while kernel is being loaded  (when it says 'kernel alive..')  
      2) The computer hangs while kernel is being loaded(when it says 'kernel alive..').

After the last time it happened,  ubuntu loaded for a long time (5 minutes)  after I disabled the keyboard and mouse support.  Then in the middle of  a session, the screen went blank and hung.  
(well actually, blanking and hanging has happened a few times but that issue would be for another thread)

Then after I restarted the computer,  things went back to 'normal'  (fast loading of ubuntu, but cant use keyboard with grub).

I also tried a fresh install with the usb kb&mouse support pre-enabled.  The live cd session wouldnt load.  

 I guess this is not a grub issue,  but  about conflct between usb keyboard support and gutsy.


My specs are:
- Core2 Quad 2.4Ghz
- Gigabyte p35c-ds3r
-nvidia geoforce 8400gs (restricted driver not enabled)
-4gig ram
- gutsy 64 and xp pro
- logitech usb keyboard and mouse with receiver station (not sure what model)

I need this machine to run lots of fortran codes and write my thesis so please help, my proposal defense is due soon!  Thanks in advance

---

### Post by mangoes on 2008-02-10
I don't know if this is related,

When I access my windows xp partition via running vmware in ubuntu,  my mouse cursor movement is restricted to the virtual windows 

i.e.  in order to release the cursor back into ubuntu  i have to 'turn off computer'  (which actually just turn off the winxp virtual machine, not the computer it self)  .

---

### Post by mangoes on 2008-02-10
sorry the vmware stuff was a false lead. I pressed ctrl+alt to release cursor. (you can see i'm a super noob)

---

