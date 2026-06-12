---
title: "[SOLVED] Intrepid on eee using usb stick? (with no external CD-drive)"
date: 2008-08-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tahina on 2008-08-25
Hi!


**Update, Aug 27:**Now it installs just fine. I took the current live-CD image of today, used isotostick.sh (see the link below) and this time it worked from start to finish. Not tried it much yet. Sound is working. Wireless is not (and it doesn't suggest anything proprietary). I'll look into that. Update, Aug 28: Now, with 2.6.27 kernel wireless works too.**/Update** 

Tried installing alternate cd version of Ubuntu 8.10 (intrepid ibex) alpha 4 on an Asus eee pc 701 using [these instructions]("https://help.ubuntu.com/community/Installation/FromUSBStick#Automatic%20Approaches") involving isotostick.sh (I'm aware of the fact that the instructions aren't about installing 8.10 alpha).

It didn't work, because the installer wants to find a cd-rom,.


Is there a preferred way to install intrepid ibex alphas on the eee?

Can I get it to work by changing something somewhere, so it doesn't require loading module for CD-ROM drive or can I choose something from /dev/... to make the installer continue?

Or should I install hardy and then upgrade?

---

### Post by jfernyhough on 2008-08-25
Use the LiveCD image. :)

---

### Post by Teg_Navanis on 2008-08-25
Yep, just mount the iso file at the right place, using

```
mount file.iso /cdrom -t iso9660 -o loop
```

for example.

---

### Post by tahina on 2008-08-25
@jfern: I got stuck at the first screen when using the live image on a usb stick, which is why I went with the alternate. Maybe I'll try that again.

@teg: You don't mean I can mount the image from within my mandriva install (which is what is currently on the eee hd (ssd)) and install from there, do you? (Forgive my ignorance)

---

### Post by Teg_Navanis on 2008-08-25
Sorry, I misunderstood your problem and assumed that you were talking about the isotostick.sh script calling for a cd-rom, not the actual Ubuntu installation. I have a machine without cd-rom drive myself and used the LiveCD there after having the same problem with the Alternate CD. 

On second thought, mounting the iso file might still work for you. Of course, not while you're running Mandriva, but from the Alternate CD. Is there a way to drop to a console, mount the image (which shouldn't be on any partition you plan to format) as a cd-rom, and then continue the installation? Might be worth a try.

---

### Post by rogerdean on 2008-08-26
Hi there

For getting almost any iso onto a stick, your answer is this nifty program
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

As for using Ubuntu on the eee, you should definitely check out this re-spin of Ubuntu
[http://www.ubuntu-eee.com/index.php5?title=Main_Page](http://www.ubuntu-eee.com/index.php5?title=Main_Page)

It's designed just for the eee, with drivers, fixes, a fast-booting kernel etc. Version 8.04 is stable right now, but he's about to release 8.04.1 with some very cool stuff included. It's not quite ready yet though...

Good luck!

---

### Post by TheMono on 2008-08-26
yeah, alternate CD's don't play nice with working from USB drives. I had to install from a live CD on the USB stick to get it on to my eee, which meant installing hardy then dist-upgrading.

---

### Post by tahina on 2008-08-27
Thanks for all the replies so far.

The reason I want intrepid is that I'm assuming ubuntu will want to have support for the eee out of the box in intrepid. Mandriva 2008.1 has that, but I'm more comfortable with apt and stuff.

And since I want intrepid and expect it to have (now or in the near future) support for the eee, I don't want to use a customized hardy respin.

(I've tried one respin before, the netbookremix of eeebuntu. Sometimes the eee would freeze up. Maybe I didn't set it up properly, forgot to run some script or something.)

I haven't done anything more with project intrepid-on-eee-with-usb-stick yet. When I get the opportunity, I'll try it with a newer live-CD image (the last time I tried a live-CD image it got stuck at the first screen). If that doesn't work, I'll go the hardy > dist-upgrade route.

---

### Post by tahina on 2008-08-27
Marked [Solved]. Now installation works just fine with an intrepid daily (of today) live-CD image on a USB stick.

---

