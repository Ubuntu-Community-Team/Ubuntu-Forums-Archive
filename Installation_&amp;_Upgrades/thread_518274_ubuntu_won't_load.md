---
title: "ubuntu won't load"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by ksglp on 2007-08-05
hi, posted in response this in response to a thread on wubi, but since i wasn't using wubi, i was using the cd, thought it might be better off over here

when i start up my computer, it gets to the first ubuntu screen, doesn't load, and after a while shows this message,


boot
loading,please wait...
check root=booting cat /proc/cmdline or missing module ,devices cat /prod/modules 
alert! doent exit dropping to a shell
busybox.......
/bin/sh :cant access tty job control truned off 
(initramfas)_ 

anyone know what's up? the guy who'd posted before me in the other thread i was talking about had the same problem but hadn't received a response since he posted in April, and there were a few in there with the same problem, o i thought it might be something you guys feel is worth having a go at,

all your help's much appreciated,

Jordan

---

### Post by merlinus on 2007-08-05
Post system specs.

-merlin

---

### Post by ksglp on 2007-08-05
any idea how to find that out without a workable OS?

i've searched online but it's nowhere to be found, there's just numbers really on the cimputer, and they don't come up with anything in google,

it has only got 64mb RAM, will that be the problem, the installation was all successful, but would this affect the operating system's ability to load?

---

### Post by Pumalite on 2007-08-05
64 MB RAM, maybe integrated video. Better go with Alternate Xubuntu: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
And if that doesn't work, maybe DamnSmallLinux: [http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)
Good luck.

---

### Post by ksglp on 2007-08-05
thing is, it's been running XP fine for years, that 64.0 Mb comes up at the start, is it definitely true? 

I can't see my computer being able to run XP but not Ubuntu, or am i wrong?

---

### Post by Pumalite on 2007-08-05
The facts are as I stated. Sorry.

---

### Post by merlinus on 2007-08-05
Go into your BIOS.  On bootup, watch the screen to see what key to press for setup (or something like that).  You should be able to find most of system specs there.

-merlin

---

### Post by ksglp on 2007-08-05
well i just downloaded and ran DamnSmallLinux fine, but it is absolutely awful, and i can't install my USB wifi thingymajig because i don't know what the hell any of the menus are even talking about, is that a sign of things to come from ubuntu?, if i ever can install it. It looked very cheap and nasty, i'm sure a lot of work has gone into it, but that cannot be the best OS my computer can run, it just can't

i checked my bios first but i couldn't find anything in there, will check again in a bit after i've seen if the alternate iso can get me onto ubuntu,

cheers for all your help, i feel i may be back shortly

---

### Post by Pumalite on 2007-08-05
DamnSmallLinux is not from Ubuntu.

---

### Post by ksglp on 2007-08-05
just downloaded the alternate xubuntu, 

when i tried to install that it said my CPU did not support long mode or something like that, so i'm currently downloading non-alternate xubuntu, is that worth a go?

maybe my computer's just too good for alternate xubuntu, but just not good enough for ubuntu?

---

### Post by Pumalite on 2007-08-05
Something like that.

---

### Post by ksglp on 2007-08-05
OK, here's how the installation of the 5th different version of ubuntu i have attempted went,

normal xubuntu

got to the install menu, didn't get very far after i'd hit install...

[34.407447] crc error
[34.408562] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (104.1)
[34.408612]

it's getting quite annoying now, but i do really want this OS, most would have given up by now i'm sure, can anyone please help me here?

cheers,

Jordan

---

### Post by Pumalite on 2007-08-05
[http://www.computerhope.com/issues/ch000430.htm](http://www.computerhope.com/issues/ch000430.htm)

[http://www.softwarepatch.com/tips/cyclic-redundancy.html](http://www.softwarepatch.com/tips/cyclic-redundancy.html)

[http://www.geocities.com/SiliconValley/Pines/8659/crc.htm](http://www.geocities.com/SiliconValley/Pines/8659/crc.htm)

[http://www.geocities.com/capecanaveral/launchpad/3632/crcguide.htm](http://www.geocities.com/capecanaveral/launchpad/3632/crcguide.htm)

---

