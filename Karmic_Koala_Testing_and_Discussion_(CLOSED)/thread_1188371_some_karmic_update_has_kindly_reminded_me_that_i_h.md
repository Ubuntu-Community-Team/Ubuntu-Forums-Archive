---
title: "some karmic update has kindly reminded me that i have a floppy drive"
date: 2009-06-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ccw on 2009-06-15
After this weekend updates, my floppy drive (that I never use) is constantly spinning (making a clicking noise every 2 seconds).

What could it possibly be? udev, nautilus? What package should I report against?

---

### Post by Martje_001 on 2009-06-15
Remove your floppy drive :P

/joking of course

---

### Post by cecilpierce on 2009-06-15
mine run to, couldnt find out anything on it so i just disabled it in the bios. guess no one has floppys !

---

### Post by knarf on 2009-06-15
This seems to be caused a bug in devkit-disks-daemon, search launchpad for more info. A good workaround is to remove the floppy module by blacklisting it - just add ```
blacklist floppy
``` to */etc/modprobe.d/blacklist.conf*

This of course means you can not use your floppy. As the bug reminded you of the presence of this relic in your machine I assume this is no great loss...

---

### Post by ccw on 2009-06-15
> **knarf said:**
> This seems to be caused a bug in devkit-disks-daemon, search launchpad for more info. A good workaround is to remove the floppy module by blacklisting it - just add ```
blacklist floppy
``` to */etc/modprobe.d/blacklist.conf*

This of course means you can not use your floppy. As the bug reminded you of the presence of this relic in your machine I assume this is no great loss...

Devicekit?
[https://launchpad.net/ubuntu/+source/devicekit](https://launchpad.net/ubuntu/+source/devicekit)

Are you sure? The last update was weeks ago, I would have noticed that before today.

---

### Post by ktp on 2009-06-15
my floppy is missing so must have missed this =)

---

### Post by Foaming Draught on 2009-06-15
[This is how I fixed it]("http://ubuntuforums.org/showpost.php?p=7451603&postcount=22")

---

### Post by linux6994 on 2009-06-16
I do not have a floppy. I get delay and io errors during recovery boot since the floppy is not there. I have blacklisted it and it is still being looked for.

---

### Post by dagrump on 2009-06-16
I unplugged mine. Had just grabbed a floppydisk (hush, I know!!), just wanted something for the heads to slam on. 
Rebooted, & went to find a drink, wandered into a Fracking A:\ prompt. This old fool stood there dumbfounded. Wasn't sure what had befallen me, after a few seconds I figured it out. But, I was sure SCARED, there for a second.

---

### Post by knarf on 2009-06-16
This was what was bothering me: [#384579: Linux thinks there&#8217;s a floppy drive when there&#8217;s not. Probing slows down bootup by almost a minute.]("https://bugs.launchpad.net/linux/+bug/384579") Blacklisting the floppy made the continuous probing disappear and got rid of the >30 second delay on boot. I'm on a Thinkpad T23 which might play some tricks with its removable floppy drive so this problem might be confined to machines which 'fake' the presence of floppy drives. I do know that blacklisting the driver solved all problems for me.

---

### Post by ccw on 2009-06-16
> **Foaming Draught said:**
> [This is how I fixed it]("http://ubuntuforums.org/showpost.php?p=7451603&postcount=22")

So its gvfs? I want to report a bug.

Dell Optiplex 755, btw.

---

