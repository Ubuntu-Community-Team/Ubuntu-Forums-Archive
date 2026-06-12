---
title: "Installation on P1 Laptop not working"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Manyak on 2008-10-04
I've been trying for a while to get Ubuntu (actually, many different distros) to install on this laptop. But nothing is working.

When selecting to install, these are the two errors I get:

ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
PCI: Fatal: No config space access function found


After displaying those for a few seconds, it goes to the loading bar, and then to the ash shell with "(initramfs)" as the prompt.

The laptop specs are:
Toshiba 205CDS
100MHz Pentium 1
40MB RAM
250GB Hard Drive
800x600x32 graphics

Also, I doubt this is relevant but just in case - it's BIOS can't boot directly from the CD - I have to use a floppy as a boot loader and force it to.

I already tried using acpi=off, acpi=force, and noacpi, and none of them worked.

Help would be appreciated!

---

### Post by wolfen69 on 2008-10-04
> ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
can normally be fixed with a bios update. however, i doubt a computer that old will have an update past 2000 that is needed.

secondly, the laptops' specs are too low to run any modern OS. the only distro i know that might run on it, is [DamnSmallLinux]("http://www.damnsmalllinux.org/")

to run any os even resembling anything modern, you will need 300mhz. and 128mb ram.

---

### Post by oilchangeguy on 2008-10-04
> **Manyak said:**
> I've been trying for a while to get Ubuntu (actually, many different distros) to install on this laptop. But nothing is working.

When selecting to install, these are the two errors I get:

ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
PCI: Fatal: No config space access function found


After displaying those for a few seconds, it goes to the loading bar, and then to the ash shell with "(initramfs)" as the prompt.

The laptop specs are:
Toshiba 205CDS
100MHz Pentium 1
40MB RAM
250GB Hard Drive
800x600x32 graphics

Also, I doubt this is relevant but just in case - it's BIOS can't boot directly from the CD - I have to use a floppy as a boot loader and force it to.

I already tried using acpi=off, acpi=force, and noacpi, and none of them worked.

Help would be appreciated!


also there's no way this computer has a 250gb hard drive. if it does the bios probably only see's no more than 8gb. modern operating systems are NOT meant to give life to antiques. this computer is too under powered to be of much use on today's internet.

---

### Post by snowpine on 2008-10-04
I don't personally know of any distro that will run on that computer, but this thread might help you: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by Braytok on 2008-10-04
I have been battling the same problem this week on Pentium Pro system.

[http://ubuntuforums.org/showthread.php?t=936396]("http://ubuntuforums.org/showthread.php?t=936396")

You may find some useful tip there. I never got any distro to run on the Pentium Pro box but I did have success on a 233Mhz system using Puppy Linux.

[http://www.puppylinux.org/]("http://www.puppylinux.org/")

For the Pentium Pro system I ended up using FreeBSD. 

[http://www.freebsd.org/]("http://www.freebsd.org/")

---

### Post by Manyak on 2008-10-04
> **wolfen69 said:**
> can normally be fixed with a bios update. however, i doubt a computer that old will have an update past 2000 that is needed.

secondly, the laptops' specs are too low to run any modern OS. the only distro i know that might run on it, is [DamnSmallLinux]("http://www.damnsmalllinux.org/")

to run any os even resembling anything modern, you will need 300mhz. and 128mb ram.

Yeah, there's no BIOS update for the laptop.

And I don't care if it runs slow, I just need to figure out what's causing this error. I've tried 15 different Linux distros and none of them want to boot.

> **oilchangeguy said:**
> also there's no way this computer has a 250gb hard drive. if it does the bios probably only see's no more than 8gb. modern operating systems are NOT meant to give life to antiques. this computer is too under powered to be of much use on today's internet.

It does have a 250 GB hard drive, and XP is currently installed on it and working fine.

> **snowpine said:**
> I don't personally know of any distro that will run on that computer, but this thread might help you: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

Nice list. I already tried a bunch, like DSL and Meanpup and what not, but I'll give a few more a try.


> **Braytok said:**
> I have been battling the same problem this week on Pentium Pro system.

[http://ubuntuforums.org/showthread.php?t=936396]("http://ubuntuforums.org/showthread.php?t=936396")

You may find some useful tip there. I never got any distro to run on the Pentium Pro box but I did have success on a 233Mhz system using Puppy Linux.

[http://www.puppylinux.org/]("http://www.puppylinux.org/")

For the Pentium Pro system I ended up using FreeBSD. 

[http://www.freebsd.org/]("http://www.freebsd.org/")

Thanks. Already tried Puppy Linux and it didn't work though. :(



I guess I'll try a couple more distros, I just really wanted a *full* distro - so to speak.

---

### Post by TuxPrincess on 2008-10-22
To be honest if its throwing errors because of your bios it maybe because the linux kernel itself doesn't support your bios so it may not matter which distro you use.

I'd be interested to know how you go on installing and running linux on a legacy laptop.

Good luck.

---

