---
title: "Dual boot problem (fiesty fawn &amp; XP)"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by siriusblack711 on 2007-10-09
hi guys,
new here and lovin it.
ok i have an windows XP OS system. I then installed ubuntu (fiesty) on my computer about 6 months back. i was dual booting successfully without any problems.then XP started giving me malware problems and my bro decided to recover the system.a complete recovery not the system restore point.so everything in my XP partition was wiped clean and windows was back to its original factory state.however the dual boot screen doesn't show up on boot up anymore.any solution to get back the linux partiton and ways to avoid this mistake if i decide to reinstall ubuntu?

---

### Post by rsambuca on 2007-10-09
Are you sure that Ubuntu isn't still there?  I have used the recovery XP discs before, and they didn't touch the ubuntu partition.  You just have to restore the grub from any live CD.

---

### Post by siriusblack711 on 2007-10-09
i actually reformatted the linux partition.so i have to reinstall anyway.but i'm not too familiar with the GRUB. i know its basic purpose but i just installed ubuntu and it basically did everything for me on the next reboot-ie the automatic dual boot.now i don't know if that is GRub or not?but on a new install how would i use GRUB to avoid this scenario?

---

### Post by be4truth on 2007-10-09
If you use "a complete recovery not the system restore point.so everything in my XP partition was wiped clean" can you find out if your Ubuntu is still alive?
Go to XP/ControlPanel/Administration/Computer Management/Disk Management and see if the Ubunut partition is still there.
If yes boot with your ubuntu CD (option to boot from 1st harddrive) into ubuntu. Then open a terminal 

if you have one IDE harddrive
```
grub-install /dev/hda
``` 

if you have a SATA drive
```
grub-install /dev/sda
```

Check wehter hda or sda are your drives. If you have doubts come back to the forum.

If the recovery was complete Gutsy Gobbon comes out on 18th October:lolflag:

---

### Post by siriusblack711 on 2007-10-09
thanks guys,
just reinstalled ubuntu dual booted and works like a charm....again!tanks a lot

---

### Post by be4truth on 2007-10-10
Why do ask questions in the forum and then not even wait for answers? I spent at least 5 mins to help. I could have done something else in this time. 
Cheers

---

### Post by siriusblack711 on 2007-10-10
you guys did help now if something like this happens i will just boot up from the live cd to restore grub.:guitar:

---

