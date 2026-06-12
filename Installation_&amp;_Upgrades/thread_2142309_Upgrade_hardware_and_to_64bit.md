---
title: "Upgrade hardware and to 64bit"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by Gillingham on 2013-05-05
HI all

Can I check a few points.  I'm about to upgrade my hardware to an i5 processor with 8GB of Ram and change to a 64bit operating system.  I will be sticking with 12.04 unless there is a compelling reason to change 

Can I run the new hard ware with my existing 32 bit installation for a bit and expect it to work for a short period of time.  uname -a gives
```
Linux david-desktop 3.2.0-41-generic-pae #66-Ubuntu SMP Thu Apr 25 03:50:20 UTC 2013 i686 i686 i386 GNU/Linux
```

Secondly, is a fresh install still the recomended way to "convert" from 32 to 64bit.


David

---

### Post by fantab on 2013-05-05
After any major Hardware change, it is recommended that you REINSTALL any OS. OS during installation configures the install to suit your Hardware so changing Hardware may and will cause issues. RAM change is generally OK but when you change the processor it is not. So, REINSTALL Ubuntu 12.04 64bit.

BACK UP YOUR DATA.

---

### Post by sanderj on 2013-05-05
> **Gillingham said:**
> 

Secondly, is a fresh install still the recomended way to "convert" from 32 to 64bit.


No; a fresh install is the *only* way. You cannot "convert" from 32 to 64bit.

---

### Post by Cheesemill on 2013-05-05
> **fantab said:**
> After any major Hardware change, it is recommended that you REINSTALL any OS. OS during installation configures the install to suit your Hardware so changing Hardware may and will cause issues. RAM change is generally OK but when you change the processor it is not. So, REINSTALL Ubuntu 12.04 64bit.

BACK UP YOUR DATA.

I'm not sure where you got that idea from, I switch installed OS's between different hardware all the time. Unlike Windows which sets up specific drivers when you first install, the Linux kernel probes for all available hardware and loads the correct drivers each time you boot (all hardware drivers are already built into the kernel). This is one of the reasons why it's possible to have a Live CD.

---

### Post by fantab on 2013-05-05
> **Cheesemill said:**
> I'm not sure where you got that idea from, I switch installed OS's between different hardware all the time. Unlike Windows which sets up specific drivers when you first install, the Linux kernel probes for all available hardware and loads the correct drivers each time you boot (all hardware drivers are already built into the kernel). This is one of the reasons why it's possible to have a Live CD.

Personal experience. However I must admit it didn't happen with Ubuntu. But on the same machine after Hardware change ARCH did not boot. I had to load an additional module into the kernel after chrooting into it from Ubuntu. I know about Windows.

We updated my bros' mobo a few months back, both his Mint and Windows would not boot. We had to reinstall. Now, looking back, I wonder why Linux Mint did not boot.

But anyways, thanks Cheesemill for sharing your experience.


@Gillingham: It may be possible to run your installed version of Ubuntu with the Upgraded Hardware. But the only way to upgrade from 32bit OS to 64bit is to install 64bit ubuntu.

---

### Post by oldfred on 2013-05-05
The issue is usually proprietary drivers. If you have none then it works. But many of us install nVidia or AMD video or other and then if new system is not the same it will need updating first with correct drivers. 

You want to backup or reuse the existing /home if you want to preserve settings and export a list of installed packages if you have installed a lot of apps. My backup assumes I will do a new install and I include some extra documentation of system as part of my backup like a new run of bootinfoscript, hardware info and a new list of installed apps.

       Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
[/URL] Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)


If you have 10 to 25GB on your hard drive, just do another full install of the 64 bit version to see it you have any issues. But often the new systems now use UEFI which is a big change. Drives need to be gpt partitioned and system installed with UEFI.

---

### Post by gordintoronto on 2013-05-05
oldfred +1!

---

### Post by fantab on 2013-05-06
> **oldfred said:**
> The issue is usually proprietary drivers. If you have none then it works. But many of us install nVidia or AMD video or other and then if new system is not the same it will need updating first with correct drivers. 
...
...often the new systems now use UEFI which is a big change. Drives need to be gpt partitioned and system installed with UEFI.

That is it, I think. My bro's new mobo had both UEFI and proprietory graphics while the older mobo had Intel graphics and legacy BIOS.

Thank you oldfred.

---

### Post by Gillingham on 2013-05-06
Thank you for the help.
David

---

