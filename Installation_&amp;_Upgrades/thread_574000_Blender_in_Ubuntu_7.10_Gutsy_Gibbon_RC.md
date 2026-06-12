---
title: "Blender in Ubuntu 7.10 Gutsy Gibbon RC"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by ragingmon on 2007-10-12
Just downloaded Ubuntu Gutsy Release Candidate. Just this day.
And I did a fresh install of Blender.

and I got this 

```
rage@ragingmon:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Segmentation fault (core dumped)
rage@ragingmon:~$
```

any help about this?

---

### Post by Kilz on 2007-10-12
> **ragingmon said:**
> Just downloaded Ubuntu Gutsy Release Candidate. Just this day.
And I did a fresh install of Blender.

and I got this 

```
rage@ragingmon:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Segmentation fault (core dumped)
rage@ragingmon:~$
```

any help about this?

Did you file a bug report on this in launchpad?

---

### Post by ragingmon on 2007-10-12
I'll file one now..

Thanks for reminding me. :D

---

### Post by rebegin on 2007-10-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/blender/+bug/151985](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/151985) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i got the same.
i upgraded from feisty because of the better external monitor support, and than blender totaly crashed the whole system. no terminals, no X restarting, no ctrl-alt-del working...afterwards i tryed the gutsy gibbon RC live CD and could successfully install blender on that, now i installed gutsy from that live cd and blender crashed with this messabe as above but fortunately the system doesn't freeze.
so if you really have to work with blender try to launch it from the live cd until you got this fixed.

---

### Post by rebegin on 2007-10-13
[https://bugs.launchpad.net/ubuntu/+source/blender/+bug/152197](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/152197)
the crash notifier created a compele crash report to me and i couldn't link your's to mine report. that one might contain more information too.

---

### Post by rebegin on 2007-10-15
blender still not running.
i've got some other error messages:

```

$ gdb blender
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB. Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
"/usr/bin/blender": not in executable format: File format not recognized
(gdb) run
Starting program: /usr/bin/blender-bin blender
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
...
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1224852816 (LWP 6343)]
(no debugging symbols found)
...
(no debugging symbols found)
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1224852816 (LWP 6343)]
0xb6cf57c5 in ?? () from /usr/lib/dri/r200_dri.so
(gdb)

```

---

### Post by ArtInvent on 2007-10-20
Gutsy is now in official release. I have two completely different computers with both nVidia and ATI graphics. Blender 2.44 or 2.45 works in neither with similar error messages.

On top of that, Google Sketchup was (finally YES!) working perfectly in Wine 0.9.47 under Feisty and now  in Gutsy won't even start. Going back to Wine 0.9.46 it will start but has the same UI blank spaces that plagued it before.

I thought this might be connected to Compiz Fusion so I turned off all desktop effects. No luck. 

So Gutsy breaks both of these wonderful 3D apps for me at least. Warning to anyone who uses 3D - Gutsy is not ready yet. Luckily I made a clone of my entire install before upgrading and can easily go back to Feisty. Good idea for anyone wanting to try Gutsy

---

