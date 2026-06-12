---
title: "Cleaning Grub2 Bootloader Menu"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by A4orce84 on 2009-11-27
Hey Everyone,

I recently updated my Ubuntu and now I have a few extra entries to some old Ubuntu versions in my Grub 2 bootloader.

I tried searching to see if there was an easy way to clean out the "old" entries, and just have the latest one's show up. 

However, I haven't found a definite step-by-step guide on cleaning up Grub2. If anyone could help me out, I would greatly appreciate it!

Thanks.

---

### Post by darkod on 2009-11-27
If the old OSs are already removed, running:
sudo update-grub

would update it. If you want to adjust further, this may be a start:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by A4orce84 on 2009-11-27
Well it wasn't necessarily an "old OS" just an old version of Ubuntu 9.10.

So my boot loader has:

Ubuntu, Linux 2.6.31-15-generic
"  "  (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
"  "  (recovery mode)
etc
etc


Both 14-generic and 15-generic work, but I only want to use (and HAVE) the latest 15-generic version.

Is there an easy way to uninstall or delete the old version and then update my grub2 loader?

Thanks guys!

--Asif

---

### Post by darkod on 2009-11-27
Look in /etc/grub.d/10_linux, you will need to use sudo gedit. After doing changes to the file run update-grub. Before making changes to 10_linux probably good idea to make a backup copy.

---

### Post by A4orce84 on 2009-11-27
I tried following the directions in this post:

[http://ubuntuforums.org/showthread.php?t=1338836&highlight=2.6.31-15-generic](http://ubuntuforums.org/showthread.php?t=1338836&highlight=2.6.31-15-generic)


But am not seeing my kernal where I can uninstall it?

Anyone can help me out please?

---

### Post by sisco311 on 2009-11-27
> **A4orce84 said:**
> Well it wasn't necessarily an "old OS" just an old version of Ubuntu 9.10.

So my boot loader has:

Ubuntu, Linux 2.6.31-15-generic
"  "  (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
"  "  (recovery mode)
etc
etc


Both 14-generic and 15-generic work, but I only want to use (and HAVE) the latest 15-generic version.

Is there an easy way to uninstall or delete the old version and then update my grub2 loader?

Thanks guys!

--Asif

Just uninstall the old kernel via Synaptic. Search for the kernel version (i.e. 2.6.31-14) and remove the linux-image-<version>-generic and linux-header-<version> packages.

[thread=1195275]Grub2 Basics[/thread]* 7. Removing Entries from Grub 2*


*Many users keep one previous kernel on the machine which previously ran without problems.*

---

### Post by A4orce84 on 2009-11-27
Thanks sisco311!

Got it working and reclaimed some of my disk space.

Appreciate it guys! =)

--Asif

---

