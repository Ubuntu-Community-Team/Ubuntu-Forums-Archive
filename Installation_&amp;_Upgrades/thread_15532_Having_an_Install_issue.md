---
title: "Having an Install issue"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by pailhead on 2005-02-15
I'm trying to install Ubuntu on a machine I rebuilt.  It doesn't seem to want to install, I can setup the language, keyboard etc... but when it comes to installing components it has an issue.  It seems to hang and then crash to a screen:

```
[!!]Load Installer Components from CD-ROM[!!]
Installation step failed
An installation step failed. You can try to run failing item again
from menu, or skip it and choose something else. The failing step
is:
Load Installer Components from CD-ROM
```

My system specs are

Soyo K7V Dragon Plus!
AMD Athlon XP 2000+
1GB PC2100
nVidia geForce ti2100
10GB HD

I've switched out the CD-ROM with 3 different models and each one gives me the same results.  I've disabled UDMA on that IDE port and nutt'n.  Same result.  I haven't had a problem before, I've installed Ubuntu on a Toshiba 6100 Satallite Pro and an old HP Pavilion 466Mhz both with no problems.  I also tried installing Fedora Core 3 just to see if it was a problem with the CD and FC gives me an error as well....

Has anyone run into this before?

Thanks...

---

### Post by pailhead on 2005-02-15
bump... anyone seen this issue before?

---

### Post by az on 2005-02-15
I had some issues with my cdrom drive in an olde laptop.  It had a lot of trouble with burned disks, but not with pressed cds.

I would be able to install from a slowly burned CD once in a while -  I would have to let the thing coold down for a few hours before trying again...  Otherwise I would get similar errors to what you describe.

Lots of people have had such issues.  I do not know if thenewer kernel make some asumptions about hardware, but it seems that reading cds during the installation is not always easy.

Does your box boot an older linux distro - like Debian Woody?  I have never had any problems with the 2.4.18-bf-2.4 kernel.  Boot with the bf24 option.  You can then dist-upgrade to Warty...

---

### Post by pailhead on 2005-02-15
[QUOTE=azz]I had some issues with my cdrom drive in an olde laptop.  It had a lot of trouble with burned disks, but not with pressed cds.

I would be able to install from a slowly burned CD once in a while -  I would have to let the thing coold down for a few hours before trying again...  Otherwise I would get similar errors to what you describe.

Lots of people have had such issues.  I do not know if thenewer kernel make some asumptions about hardware, but it seems that reading cds during the installation is not always easy.

Does your box boot an older linux distro - like Debian Woody?  I have never had any problems with the 2.4.18-bf-2.4 kernel.  Boot with the bf24 option.  You can then dist-upgrade to Warty...[/QUOTE]

Ok I'll try that tonight.  Yeah these CD's are the pressed ones.   I built this box for Linux and I'm hoping I can get it on there.. :)

Thanks....

-Jason

---

### Post by pailhead on 2005-02-15
[QUOTE=azz]I had some issues with my cdrom drive in an olde laptop.  It had a lot of trouble with burned disks, but not with pressed cds.

I would be able to install from a slowly burned CD once in a while -  I would have to let the thing coold down for a few hours before trying again...  Otherwise I would get similar errors to what you describe.

Lots of people have had such issues.  I do not know if thenewer kernel make some asumptions about hardware, but it seems that reading cds during the installation is not always easy.

Does your box boot an older linux distro - like Debian Woody?  I have never had any problems with the 2.4.18-bf-2.4 kernel.  Boot with the bf24 option.  You can then dist-upgrade to Warty...[/QUOTE]
 Ok so how do I install it using the bf24 option.. do I run linux bf24 when the initial install screen shows?

---

