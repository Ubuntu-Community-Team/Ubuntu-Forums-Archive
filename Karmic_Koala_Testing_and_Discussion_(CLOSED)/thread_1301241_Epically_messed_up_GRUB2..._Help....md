---
title: "Epically messed up GRUB2... Help..."
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ugriffin on 2009-10-25
Hey. I freshly installed Karmic on my *main* PC. First boot ran ok, GRUB2 worked ok... no problems. Installed my drivers and my usual apps, and ran sudo update-grub cuz the thing wasn't detecting my Windows partition.


Guess what?

Rebooted, and now I get a single line of complete gibberish like this: "#"$"=aj" and yeah, error messages are a little luxury in this situation. Ironically, if I pop in a livecd and press ENTER it loads it.

I've tried using the Alternate CD (Karmic) to rescue the system, specifically, installing GRUB to both hd0 and hd5 and running update-grub2.


What on earth is wrong? Little help would be REALLY nice. Or should I just ditch Karmic and GRUB2 and everything?


Remember... it worked the first time. So GRUB2 is compatible. This is most probably an Ubuntu bug or something... trouble is, my system is so messed up it's a little hard to find out what went wrong :(


Please... any help? I'll gladly attach any configuration files of ANYTHING you ask, and I'll also follow instructions from a (Jaunty) LiveCD or a Karmic root terminal from the LiveCD rescue option.


Thanks... :(

---

### Post by ugriffin on 2009-10-25
update...


ran update-grub and then grub-install from an Alternate CD rescue terminal. Still get the same gibberish.

---

### Post by drs305 on 2009-10-25
> **ugriffin said:**
> 
I've tried using the Alternate CD (Karmic) to rescue the system, specifically, installing GRUB to both hd0 and hd5 and running update-grub2.

Remember... it worked the first time. So GRUB2 is compatible. This is most probably an Ubuntu bug or something... trouble is, my system is so messed up it's a little hard to find out what went wrong :(


Please... any help? I'll gladly attach any configuration files of ANYTHING you ask, and I'll also follow instructions from a (Jaunty) LiveCD or a Karmic root terminal from the LiveCD rescue option.



I can't tell you what happened. You don't get any Grub 2 menu? Since you know G2 can work I'd just reinstall it via the LiveCD. Here are the instructions:

[Grub2 - Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by ugriffin on 2009-10-25
> **drs305 said:**
> I can't tell you what happened. You don't get any Grub 2 menu? Since you know G2 can work I'd just reinstall it via the LiveCD. Here are the instructions:

[Grub2 - Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

errm... my second post says that I just tried that. I'll try one more time with the --recheck option, just in case. Doubt it will work, though.


EDIT: Yep, no diffrence. As a side note, I'd like to keep GRUB 2, if possible.

---

### Post by drs305 on 2009-10-25
You were doing the full-up "chroot" into your normal system partition and all and it still returned the same results?

---

### Post by ronacc on 2009-10-25
boot with your live cd , mount your karmic / (or boot if you have that ) and see if /boot/grub/grub.cfg exists , look at the boot line and make sure it is pointing at the right place .

---

### Post by ugriffin on 2009-10-25
I used a rescue option from the terminal that basically mounts your root as root and then gives you a command line. It's a diffrent approach, but it works like it should: to give you a command line that affects your system, and not the livecd.


Additionally, update-grub wouldn't work from a livecd command line. :)

---

### Post by ugriffin on 2009-10-25
Solved.


Link to the solution:


[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

---

