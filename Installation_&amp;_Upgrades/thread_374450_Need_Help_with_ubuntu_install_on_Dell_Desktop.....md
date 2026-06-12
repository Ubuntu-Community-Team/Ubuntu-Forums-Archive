---
title: "Need Help with ubuntu install on Dell Desktop...."
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by n8dude on 2007-03-02
I am been trying to install Ubuntu 6.10 on my friends Dell Dimension 2100 (old, but compatible)
and I cant get it to boot into linux.I pop in my install CD and the machine boots into Windows. I dont know if anyone else has a problem like this, but I need a fix for it. 
System Specs:
Intel Celeron 1.5ghz
512mb ram
40gb HD
Intel Integrated Graphics
thats all the stuff that matters, but I just dont get why its not wanting to boot into Ubuntu.
Thank you for your help.

---

### Post by taurus on 2007-03-02
Get into the BIOS and make sure you the bootloader to boot from the CD-ROM first instead of a harddrive.  Then, make sure you burn the ISO file as an image file, not a data file.  In other words, if you pop that CD into the drive while in XP, you should see a bunch of files and directories on it instead of one big file that you've downloaded.

---

### Post by n8dude on 2007-03-02
i have burned the ISO to a cd already, and when i turn the machine on it doesnt show  "press escape to enter bios" or anything like that. it just goes its own merry way and boots into windows. i popped a XP disc in that i had laying around (sorry) and it didnt work either, it just doesnt want to boot from cd's

---

### Post by torgrot on 2007-03-02
Try hitting F12 that should give you a menu on a Dell to pick the boot device.  Select CD-ROM and it should boot the LiveCD.

---

### Post by taurus on 2007-03-02
With Dell, you need to press F2 (Del or F12) when the machine first boot.  That would get you into the BIOS.  Otherwise, please look at the manual that comes with the machine to see which key you have to press to get into the BIOS.  As of right now, you have it boot from the harddrive first so that's why it doesn't even look at the CD-ROM.

---

### Post by n8dude on 2007-03-02
Ty taurus, worked like a charm! I dont work with Dells much so I didnt know about that. Ty sooo much!

---

### Post by n8dude on 2007-03-02
ugh, I have another problem. When it boots into ubuntu, it hangs at the install portion. Could you shed any light on this?

---

### Post by taurus on 2007-03-02
Do you currently have XP on that 40GB harddrive?  Maybe you want to boot into XP first (reboot and remove the LiveCD from the drive) and defrag the harddrive three times before you plan to resize it with the Ubuntu LiveCD.

---

### Post by n8dude on 2007-03-02
Defrag it? im trying to nuke windows from the system. would that make a difference?

---

### Post by taurus on 2007-03-02
If you want to nuke XP, then no need to defrag it.  Does the LiveCD boot up at all?

Perhaps you should consider using the alternate CD to install Ubuntu on that Dell instead.

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by n8dude on 2007-03-02
yeah it boots in but when i try to install it it hangs when its trying to scrub the HD, ill DL that release right away tho, ty

---

### Post by n8dude on 2007-03-02
ok, now it works properly. Ty guys for your help :guitar:

---

