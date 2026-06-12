---
title: "Installation freezes"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by bearNeedsCookies on 2009-12-21
I'm attempting to install 9.10 onto my Asus S5200N (1.5GHz, 512MB RAM) but the installation freezes either on the Time Zone selection, or the select partition to install stage.

In both cases the mouse cursor can be moved staying in its waiting state (but not animating), and no keyboard action does anything.

I've attempted to install from the Live CD from both running the install from the boot menu, and by running it after starting a Live CD desktop session.

I've checked the disc for errors, and last night created a bootable USB version of the Live CD which had the same symptoms.

In one of the attempts where I started a Live CD desktop session, I started to flick through the menus and experienced a similar lockup, but I've not tested extensively on that side.  This makes me think it could be related to issues such as:
[http://ubuntuforums.org/showthread.php?t=1349113](http://ubuntuforums.org/showthread.php?t=1349113)
[http://ubuntuforums.org/showthread.php?t=1304287](http://ubuntuforums.org/showthread.php?t=1304287)

I've previously had 8.10 running on the machine, but was going for a clean install.

Does anyone have any suggestions on how to figure out what is going on?

---

### Post by bynge on 2009-12-21
Hi,

Several people have reported installation freeze for 9.10.
I had the same problem too. Here is what I suggest. I am no expert, just give it a try.

When you boot from liveCD, in the first menu there is an option "MemTest..." . GO for it. It will report some errors in your RAM and correct it if possible. Just run it till the count stops and then press "c" and restart the test(press 7). Make sure your RAM is free of bad memory locations. (Error Count should be Zero)

Now start your installation again. Good luck

---

### Post by bearNeedsCookies on 2009-12-21
I went through the memtest twice as suggested, no errors came up.

I've jumped into the live session a few times, freezes up after around a minute of playing around each time.

Any more ideas on how to diagnose this?

---

### Post by tenach on 2009-12-22
Mine freezes before I get to the cd menu, just after it shows the isolinux loading stuff.  The md5sum matches the one in the wiki.

---

### Post by bearNeedsCookies on 2010-02-03
Finally gotten around to downloading the alternative installation disc, gonna give it a try this week and see how far I get.

---

