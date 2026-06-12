---
title: "Live CD will not boot"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by xixel on 2007-01-20
I've searched the forums already, and only found related topics to kernel upgrades and laptop specific model issues

This is a desktop, AMD64 Dual Core 4200+, mother board is a DFI LanParty UT NF4

The boot menu comes up, I boot from cd...  and right away, I get

invalid compressed format (err=2)

I've tried i386 ISO, and the amd64, I've checked the sums of both before I burned, and I verified the data both times I burned.

ubuntu-6.10-desktop-amd64.iso
ubuntu-6.10-desktop-i386.iso

I need some ideas - would like to install Ubuntu on this box.

thanks in advance for your time

---

### Post by an.echte.trilingue on 2007-01-20
Have you tried the alternate install CD?  It tends to work better across a wider variety of hardware...

Take care,
-mat

---

### Post by xixel on 2007-01-20
Same result with ubuntu-6.06.1-desktop-i386.iso, only with err=1 instead of 2

Downloading 6.10 alternate now..

---

### Post by mid_night gypsy on 2007-01-20
xixel,
 You could try the livecd with a boot options.At boot menu press F6 and append (type) (ide=nodma)     Once
and if it works (booted up) open a terminal and type a hdparm command like this,(sudo hdparm -d1 /dev/hda) ( hda = your harddrive your's maybe diffident).Ohh,press enter if that works you can gedit /etc/hdparm.conf. good luck,gypsy

---

### Post by xixel on 2007-01-20
6.10 alternate, same thing, 6.10 alternate with ide=nodma, I get a CRC error. halts in same place

Could this be my burner now? the data has been verified each disc I burn.

---

### Post by mid_night gypsy on 2007-01-20
xixel,
 I have been googling for 'bout hour to no glory.Every thing I have found points to a bad burn.So,how did you burn the  iso?Did you burn it from windows?Have ever had linux OSes on this box.What I tryin' to say is the more info the more better.
                                                                                    Still Tryn' gypsy[LEFT][/LEFT][CENTER][/CENTER]

---

### Post by xixel on 2007-01-20
Thank you for your time, since we narrowed it down to my burner.. I started looking into it, and forgot I had been using my burner with an IDE>SATA Adapter, Thinking this might cause problems.. I disconnected one of my hard-drives and connected the drive directly with IDE, and it works! but.. 

onto the next problem, lol.. my LCD's go out of range, I have 2, Viewsonic VP2030b's on an XFX 7600 GT, Dual DVI card..  I'm just starting to search around the forums now for answers

---

