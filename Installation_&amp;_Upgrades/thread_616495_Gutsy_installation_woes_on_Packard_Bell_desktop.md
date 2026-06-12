---
title: "Gutsy installation woes on Packard Bell desktop"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by GeneralSunTzu on 2007-11-18
Hello,

I have done my homework (searched all forums) and cannot find anything useful.

I installed Gutsy on a Packard Bell desktop (most people try it on laptops) PC with 256 MB RAM.

The HW specs of the machine are here:
[http://support.packardbell.com/nl/item/index.php?i=spec_nova&psn=4682887003](http://support.packardbell.com/nl/item/index.php?i=spec_nova&psn=4682887003)
With the live Gutsy CD it did not work. 

I proceeded therefore, as usual in these cases, to use the alternate CD, with the standard method, i.e.:
a. check CD for defects [OK];
b. format the whole HD (60 GB) so that I have three partitions, /[6 GB], swap (2 GB), and /home [whatever free space was left];
c. install the system from the CD;
d. boot from the freshly installed system and update everything.

So far so good. I cannot see the bottom status bar, probably the wrong resolution beingthe cause, and the sys asks me whether I want to install the nVIDIA restricted drivers and a restricted modem driver. 
I see no reason not to. Big mistake!
I do and I screw up so powerfully that I have to re-install the whole shabang...

Now, I wonder how I can do the following:

1. identify the correct nVIDIA driver, as the recommended one is obviously wrong;
2. identify the right resolution for the screen;
3. have a plan "B" if I screw up again, rather than re-install everything from scratch.

Packard Bell is a very Linux-hostile manufacturer, with all sort of nasty stuff (blocked BIOS, hidden Win XP "recovery" partition on the disk) to prevent you from Linuxifying any of his machines.

His technical documentation standard is also beneath contempt, as watching what they have the cheek to call the specs, with the S/N identifying precisely the PC, I still am unable to tell which nVIDIA card it has, what's the resolution of the monitor etc.

Could any gentle soul point me at Ubuntu commands I may use to try to identify the card, so that afterwards I can pick up the right driver, and/or how can I tell the resolution of the screen?

Thank you so very much.

---

### Post by wjp.reg on 2007-11-18
did you try the ```
lspci
```command to list your hardware?

If it is an nvidia card, it will most likely be a "legacy" version.

---

