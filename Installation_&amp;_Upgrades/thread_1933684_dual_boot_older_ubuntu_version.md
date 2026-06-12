---
title: "dual boot older ubuntu version"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by SailorBill01 on 2012-02-29
I have installed ubuntu 11.10 with Wubi and it is too slow with my old computer [2.2ghz, 1gb RAM, integrated graphics]. I am using 10.04 on a USB drive and it is very fast but dosen't save my settings. 

Is there a method to either use Wubi to dual-boot install 10.04 or a method to save my settings on the USB drive. I need simple solutions, just dual booting was big! I need to keep Windows XP for my son's homework:( Thanks, Bill

---

### Post by Bucky Ball on 2012-02-29
Wubi is NOT a dual-boot. It is a Wubi install; Ubuntu running inside Windows, just like another Windows program. Ubuntu on a separate partition to Windows (side-by-side) or on another hard drive or on a USB key *is* a dual-boot. ;)

You can't shrink your Windows partitions (or a data partition) and leave some free space on your hard drive to install 10.04 LTS? You can also install 10.04 LTS to the USB as a persistent install but you'll need to google to find out how.

BTW, 10.04 LTS is the current LTS release, the most stable release (LTS releases are intended for reliability, stability, production machines and servers) and supported until April 2013. :)

PS: What software does your son need for his homework??? Unless it's something very exotic, well ...

---

### Post by bcbc on 2012-02-29
You can get the 10.04 wubi.exe from here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

It doesn't run under Windows, just the installer/uninstaller (wubi.exe). Ubuntu runs native but uses a virtual disk (common misconception).

---

### Post by SailorBill01 on 2012-02-29
Nothing exotic, Word and Excel!

---

### Post by SailorBill01 on 2012-02-29
> **bcbc said:**
> You can get the 10.04 wubi.exe from here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

It doesn't run under Windows, just the installer/uninstaller (wubi.exe). Ubuntu runs native but uses a virtual disk (common misconception).
Thanks
Do I download only the wubi.exe file from [[http://releases.ubuntu.com/10.04/]](http://releases.ubuntu.com/10.04/]) page or do I have download a .iso file also? I ask because the [wubi.exe] file has a 2012 date.
Bill

---

### Post by bcbc on 2012-02-29
> **SailorBill01 said:**
> Thanks
Do I download only the wubi.exe file from [[http://releases.ubuntu.com/10.04/]](http://releases.ubuntu.com/10.04/]) page or do I have download a .iso file also? I ask because the [wubi.exe] file has a 2012 date.
Bill

You can run the wubi.exe standalone (it will download the ISO itself) or you can download the _Desktop CD_ ISO you want yourself from the same site and save it in the same folder as Wubi.exe before running.

The reason the date is recent is that the 4th update to 10.04 was recently released (10.04.4).

---

### Post by Bucky Ball on 2012-02-29
Keep in mind that Wubi is not considered a permanent solution; more to test and try Ubuntu for awhile (rather than from the LiveCD) before either installing or discarding. It can also be problematic so I'd backup anything valuable before attempting. ;)

PS: OpenOffice can read and write Word and Excel files (and output OOffice files as Word or Excel files for use on a Win machine).

---

### Post by bcbc on 2012-03-01
+1 Wubi is not a permanent solution. You don't need to worry about Windows, but I'd back up data you store in Ubuntu (i.e. on the virtual disk). Hard shutdowns can lead to corruption of the virtual disk.

I've been running a wubi install continuously so that I can see for myself how buggy it is - and it's not. Two consecutive development releases on the same wubi install (which is risky anyway), multiple resizes of the virtual disk, etc. etc. and it's still going strong. Yet there is this perception amongst many that Wubi breaks very easily.

---

### Post by Bucky Ball on 2012-03-01
bcbc, which release are you using. 10.04 LTS? This Wubi *should* be rock solid by now.

---

### Post by bcbc on 2012-03-01
I'm using 12.04. I haven't tried 10.04 for a while but will have to probably install it soon to test the upgrade.

Most of wubi's bugs are in the installer now (wubi.exe). It doesn't get a lot of developer attention.

---

