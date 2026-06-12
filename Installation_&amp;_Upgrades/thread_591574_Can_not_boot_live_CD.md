---
title: "Can not boot live CD"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by rnawky on 2007-10-25
When I boot with the Ubuntu 7.10 32 Bit CD in, all goes well until I encounter the same error over and over.

The console gets spammed with
SQUASHFS: error: Unable to read fragment cache block

and
Buffer I/O Error on device sr0, logical block #####

along with other random addresses.

I am able to boot fine with a SuSE DVD

I guess ill try Ubuntu Alternative install CD unless someone has some insight as to whats going on.

---

### Post by snickers295 on 2007-10-25
i think your cd is bad.
what speed did you burn it at?
don't burn it at anything higher then 4x.
and i would suggest you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") before you burn.

---

### Post by rnawky on 2007-10-25
> **snickers295 said:**
> i think your cd is bad.
what speed did you burn it at?
don't burn it at anything higher then 4x.
and i would suggest you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") before you burn.

I burned it at 24X but I had nero check the disk after burning it. 

I also initiated a fore re-check of the torrent file in utorrent.

I'll try burning it at 4X and see where that gets me.

EDIT: Slowest my laptop can burn is 8X

---

### Post by snickers295 on 2007-10-25
> **rnawky said:**
> I burned it at 24X but I had nero check the disk after burning it. 

I also initiated a fore re-check of the torrent file in utorrent.

I'll try burning it at 4X and see where that gets me.

EDIT: Slowest my laptop can burn is 8X
if 8x is slowest then do it.

---

### Post by rnawky on 2007-10-25
> **snickers295 said:**
> if 8x is slowest then do it.

Just tried burning it again, as well as the alternative CD.

Regular version yields the same error.

The Alternative version runs into this problem.

Installation step failed.
An installation ste failed. You can try to run the failing item again from the menu, or skip it and choose something else. The falling step: Select and install software.

Then the console says

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/a/acpi/acpi_0.09-3ubuntu1_i386.deb Hash Sum mismatch
0 upgraded 730 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/467MB of archives.
After unpacking 1715MB of additional disk space will be used.
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
taslsel: aptitude failed (100)
main-menu[3312]: WARNING**: Configuring 'pkgsel' failed with error code 1
main-menu[3312]: WARNING**: Menu item 'pkgsel' failed.

---

### Post by snickers295 on 2007-10-25
> **rnawky said:**
> Just tried burning it again, as well as the alternative CD.

Regular version yields the same error.

The Alternative version runs into this problem.

Installation step failed.
An installation ste failed. You can try to run the failing item again from the menu, or skip it and choose something else. The falling step: Select and install software.

Then the console says

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/a/acpi/acpi_0.09-3ubuntu1_i386.deb **[SIZE=4]Hash Sum mismatch[/SIZE]**
0 upgraded 730 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/467MB of archives.
After unpacking 1715MB of additional disk space will be used.
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
taslsel: aptitude failed (100)
main-menu[3312]: WARNING**: Configuring 'pkgsel' failed with error code 1
main-menu[3312]: WARNING**: Menu item 'pkgsel' failed.
download the alternate cd again then do a [md5sum.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by rnawky on 2007-10-25
> **snickers295 said:**
> download the alternate cd again then do a [md5sum.]("https://help.ubuntu.com/community/HowToMD5SUM")

I did

I checked the MD5 sum of the ISO, then I had nero varify the CD after it was written, then I did a CD check from the actual installer on the target computer, All came back OK.

However I did some searching and found other people with this same error and solved it by installing apci from the terminal after it fails and re-running the install software stage.

So, It wasn't me, it's a problem with the iso's

---

### Post by snickers295 on 2007-10-26
ya that make sense because the 7.4 livecd kept coming up with "job control tty turned off" or something like that on everyones computers so i guess this is another installer error.
did you get it installed.

---

