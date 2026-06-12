---
title: "Fatal Error Causing Boot Process to Stall"
date: 2005-01-02
forum: Installation &amp; Upgrades
---

### Post by BillF on 2005-01-02
Being new to this; I have run into a snag during the boot process after loading Ubuntu on my laptop computer.  During the boot process all seems to go well until this message pops up.

Modprobe: Fatal error inserting floppy (/lib/modules/2.6.8.1-3-386/kernel/drive re/block/floppy.ko; no such device

Once that message appears the boot process stops. When I installed Ubuntu I had my Zip and Jump drive plugged into the usb socket, there is no floppy drive with this computer.

Thanks for the help!

Bill

---

### Post by cr4z3d on 2005-02-28
```

modprobe: FATAL: Error inserting floppy
 (/lib/modules/2.6.8.1-3-386/kernel/drivers/floppy.ko): No such device

```
 i have that same problem.. i wish someone knew how to fix it.. i really want to learn linux and i didn't like mandrake or redhat so i came here.

---

### Post by sandman55 on 2005-03-02
Hi guys I'm a realy green noob and have the same problem I found this [LINK](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors) which says dont worry about it I have a further problem when I install ubuntu with out updates It seems ok but when I install with updates Im stuck on a DOS screen and when I log in still a DOS screen. Oh well I'll keep on looking

---

### Post by delltony on 2005-03-02
[QUOTE=BillF]Being new to this; I have run into a snag during the boot process after loading Ubuntu on my laptop computer.  During the boot process all seems to go well until this message pops up.

Modprobe: Fatal error inserting floppy (/lib/modules/2.6.8.1-3-386/kernel/drive re/block/floppy.ko; no such device

Once that message appears the boot process stops. When I installed Ubuntu I had my Zip and Jump drive plugged into the usb socket, there is no floppy drive with this computer.

Thanks for the help!

Bill[/QUOTE]

Are you able to get to a # prompt at all? Are you running warty or hoary?  
1) if your able to get to a # prompt then try the following sudo modprobe -r floppy
    this should remove the floppy module that appears to be causing the problem
    you can later modprobe floppy to add it back if needed.
2) If your not given a # prompt then put the warty install cd and run thru the process until you get to the partition drives part. what this will do is allow the system to detect yoru drives and so forth. at this point hit control alt f2 and you should be taken to a virtual #  just simply login with your username and pass as you normally would then do step 1.
 3) after this is done then type sudo shutdown now -r  
      this will force your system to reboot and you should be fine hopefully.

---

