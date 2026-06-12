---
title: "wont boot after install"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by broecher on 2012-10-06
hi, i am trying to install ubuntu server 12.04.1 and the installation seems to go fine. when the cd ejects and it reboots, i get the bios and then it goes black. i tried again and went into the boot menu and made sure it was trying to boot on the hard drive and it was.

when i installed i used the entire disk, and i told to install the grub boot loader (not sure if thats the right name) when it asked.

This is the 3rd time i've tried...

This same computer did allow me to install ubuntu 9.04 server successfully.

i am reading [_[COLOR="DeepSkyBlue"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1922913&highlight=black+screen+bios") post and i followed the directions to boot in recovery. i noticed that when it asked where to open the shell, it listed sda1, sda2, and sda5. is this what i should have? i thought since i installed to the entire disk there should be only 1 sda, plus another for swap maybe. i had no errors running:

```
su
grub-install /dev/sda
update-grub
```

i don't quite understand the directions in the linked post about raid, but i don't see that in my bios setup.

Any suggestions?

---

### Post by will1982 on 2012-10-06
Maybe try installing oneiric server if you can.

*Might* be a bug in 12.04.'

Don't know much about the subject, just a random guess

---

### Post by broecher on 2012-10-06
yeah i would have liked to just stick with 9.4 but i want the LTS, and i had some other problems with it.

---

### Post by broecher on 2012-10-07
ok here is what i learned so far.
I  installed 10.04 server, and it worked! from there, i did an upgrade. it looked like it was going to work, until the reboot. then it went black after bios again!!

BUT, i tried to log on from another computer and was able to...

I guess there is some reason that 12.04 will not send any signal to the monitor and that is probably what was going on with the fresh 12.04 installs i tried...

---

### Post by Bashing-om on 2012-10-07
broecher; Hi !

 The black screen can be indicative of graphics issues.
Try to boot with the "nomodeset"option:
bios screen clears-> depress any key==>boot options menu,
f6 selects the "nomodeset" option, f10 continues to boot.

[INDENT]hth <==BDQ

[/INDENT]

---

