---
title: "Boot Record Disappeared ?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by anjanesh on 2010-04-11
I had upgraded to 10.04 a while ago which was working fine.
I now made an update and on reboot, I get

```
PXE-E61: Mediaa test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.

No bootable device - insert boot disk and press any key
```

How did my boot record disappear ?
How I reinsert it ?

---

### Post by wilee-nilee on 2010-04-11
With just this little bit of information I would check all connections to make sure nothing is unplugged, If that does nothing then see if the computer will boot a live Linux CD. If it will boot the live CD it is easy to put grub back in it's place. So you are running Lucid which is grub2 here is a link, step 11 is the one to look at.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

This method is done with a live CD.

---

### Post by anjanesh on 2010-04-11
Just tried a 8.04 live CD - it works. I was able to locate the internal HDD from nautilus.

---

### Post by wilee-nilee on 2010-04-11
> **anjanesh said:**
> Just tried a 8.04 live CD - it works. I was able to locate the internal HDD from nautilus.

Now I am not sure hopefully we will get the real geeks in on this, but I think if it is just a need for reinstalling grub2 you need a 9.10 or beyond live CD. I think it might help altogether if you can to post this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you can back up anything of importance from using the live cd to access the 10.04 partition you might consider this before proceeding.

I am just trying to error on the side of protecting your install at the least.

Does the 10.04 partition show up in home on the sidebar mountable? from the Hardy Live CD.

---

### Post by anjanesh on 2010-04-11
Sorry - I dont think it located the internal HDD - its just filesystem which is probably the Live CD's filesystem.
So, no, I couldnt locate the external HDD in live CD.

I went to BIOS > Boot

```
Boot Menu Type : Normal
Boot Device Priority : <CD/DVD-ROM Drive>
                       <Hard Disk Drive>
                       <Floppy Drive>
                       <Ethernet>
Hard Driver Order    : No Hard Disk Drive
CD/DVD ROM Drive Order : <PT-TSSTcorp CDDV>
Removable Drive Order : No Removable Drive
Boot to Optical Devices : <Enable>
Boot to Removable Devices : <Enable>
Boot to Network : <Enable>
USB Boot : <Enable>
```

**Hard Driver Order    : No Hard Disk Drive** !!!

---

### Post by wilee-nilee on 2010-04-11
I am not familiar with how everything is hooked up inside a computer. I usually see people at this point suggest checking connections, as it seems to be a hardware problem, but I could be wrong. Things sometimes fail at times, that make it seem, like software problems.

The boot script is run from a live CD, the Hardy CD should be okay for this so try that it will show what is now there.

You can also open gparted in Hardy and see if the HD is showing if it is take a screen shot and post that as well, this is extra, the bootscript is the best way to look inside.

---

### Post by anjanesh on 2010-04-11
> I usually see people at this point suggest checking connections, as it  seems to be a hardware problem, but I could be wrong. You're right. I just opened the chasis, the power cable to the HDD is burnt pretty badly ! One part just came off !

[IMG]http://img138.imageshack.us/img138/9822/dsc02947ws.jpg[/IMG]

---

### Post by wilee-nilee on 2010-04-11
> **anjanesh said:**
> You're right. I just opened the chasis, the power cable to the HDD is burnt pretty badly ! One part just came off !

[IMG]http://img138.imageshack.us/img138/9822/dsc02947ws.jpg[/IMG]

Wow, hopefully everything will work when you get that fixed, you were smart to check this possibility.

---

### Post by anjanesh on 2010-04-11
I did have the computer switched on the whole night tough - this happened today morning.
I don't understand how this could've happened in the first place as it can't be a voltage fluctuation problem as I have a [Delta 1kVA UPS]("http://way-india.com/N_Series.html").

---

