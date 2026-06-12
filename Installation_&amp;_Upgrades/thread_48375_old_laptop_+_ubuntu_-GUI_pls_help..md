---
title: "old laptop + ubuntu -GUI pls help."
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2005-07-12
hi, gear: 32mb of ram, 400mhz processor,
installation: kubuntu  , on boot: server acpi=off (server is same as minimum packages in ubuntu)
EDIT: laptop :gateway solo 2500
goes ok, till point:
main-menu[xxx]: DEBUG:Executin /l9ib/mani-menu.d/10casper
init: ^MProcess ' /sbin/debian-installer' pix(xxx) exited. Schedulin it for restart.
init: ^MStartin pid xxx, console /dev/vc/1: '/sin/debian-installer'

it repeats those lines, then re-boots, then i'm back into old crappy w98 ! like nothing happened.

my aim was to install ubuntu (no GUI ) minimum, on whole hard drive. 
 ANY ideas? please help!

thank you

---

### Post by az on 2005-07-12
Did you try without acpi=off?

Also, the installer can install with 32 megs of ram, but that is the minimum.  I have noticed that it needs more ram on some systems and cannot install with 32 megs.

Can you boot from a floppy, or something and create a swap partition?  The installer will find it and mount it, which should solve your problem.

Also, do not use improper language.  I hate editing other's posts.

---

### Post by fastluck on 2005-07-12
Which gateway do you have?

---

### Post by [pl]ice on 2005-07-13
azz,
 sorry form my language;   yes i put acpi=off, otherwise errors with 129 degrees temp. overheating kept poping out.
   no, i haven't tried to make a swap partition, i'm not sure how to do it, but will give it a go.
i used knoppix on that laptop, it went through to GUI (very slow), so i'm bit suprised it needs 32megs + ; but again, will try to buy some.

thanks!!

fastluck ::   gateway solo 2500 32 megs of ram and 400 MHz  processor.

I will try to get some more ram.

thanks.

---

### Post by [pl]ice on 2005-07-14
i created ~370 mbs of swap partition, using p.magic, and still didn't work ... will try to get some ram, thanks

---

