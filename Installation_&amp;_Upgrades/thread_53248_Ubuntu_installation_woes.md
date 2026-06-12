---
title: "Ubuntu installation woes"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by Velox Letum on 2005-07-30
On initial installation it begins to load the kernel, decompresses, runs etc.

But then I either get this:

/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/mnt/ (etc.)
: Too many open files
Kernel panic -  not syncing: Attempted to kill init!

Or, my more common error:

Starting systems: logd (etc)
Segmentation fault (over and over again)

which is sometimes accompanied by
/build/buildd/cdebconf-0.74ubuntu10/src/debconf.c:132 (main): Cannot initialize debconf configuration database

This server is a AMD K6-2 500mhz with 786mb of SDRAM.

---

### Post by varunus on 2005-07-31
Have you tried the ubuntu live CD or Knoppix on this computer?

---

### Post by geekdreams on 2005-08-11
I've run into this problem as well on a Compaq Presario 1245 (AMD K6-2 333Mhz, 32MB RAM). It enters Low Memory Mode, walks through a few of the setup screens, but always freezes after several "Loading additional components..." screens. After a while I get the "Segmentation fault" error over and over again with no other information.

I read that [K6 chips had faulty FPUs](http://michael.bacarella.com/projects/amdmyths/) but booting with "linux no387" didn't work either.

What would running the LiveCD do in terms of troubleshooting the installation?

---

