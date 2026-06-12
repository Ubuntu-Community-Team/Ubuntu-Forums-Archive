---
title: "Accidently installed Ubuntu onto Windows"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by WhaaChuTalkinBout on 2013-03-21
So the other day i tried installing Ubuntu onto a SSD via Pen Drive Linux Universal Installer. I created it and put it onto the SSD and put it back into my laptop and when i booted it up it said 'BOOTMGR is missing'. I restarted my dekstop and it turned out i accidently installed Ubuntu onto my Windows and i cannot access it via dual-boot but i can access my file. How can i uninstall Ubuntu from here and no i dont own a recovery disk for windows. Please help
Thanks

---

### Post by VeeDubb on 2013-03-21
Hopefully someone else will have a more useful reply than I do, but I think you're out of luck.  You can't "uninstall" ubuntu.  Ubuntu is an operating system that would normally replace windows unless you set up a dual boot system.  If you just told it to use the entire disk, that means that everything is gone.  The one shred of hope is that you said you can access your files.  In all likelihood, you're going to have to get a hold of windows disk and re-install windows.

---

### Post by fantab on 2013-03-21
If you want to recover your Windows files/data then don't use you HDD.

Boot from Ubuntu LiveUSB and opt to "TRY UBUNTU". Once you have the Ubuntu desktop ready open Terminal (Ctrl+ALT+T) and run the following command:
```
$ sudo fdisk -l
```

...and post the output here.

Meanwhile [Read Here]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Mark Phelps on 2013-03-21
What does "but i can access my file" mean? Can you see the Windows installation and confirm that the files are still there?

IF so, how do you do this?

If Windows is still there but you can't boot into it, that can be repaired.  IF Windows is gone, then your only hope is to connect this drive to another Windows PC and use some Windows data recovery apps to get your files back.

---

### Post by WhaaChuTalkinBout on 2013-03-22
If i go into the HDD there is a windows file that has all my folders and documents from windows, all my game folders and program files.

---

### Post by WhaaChuTalkinBout on 2013-03-22
ubuntu@ubuntu:~$ $sudo fdisk - l
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

---

### Post by fantab on 2013-03-22
you just have to type: **sudo fdisk -l**

---

### Post by Mark Phelps on 2013-03-22
> **WhaaChuTalkinBout said:**
> If i go into the HDD there is a windows file that has all my folders and documents from windows, all my game folders and program files.

That's very unusual as that stuff is generally spread across lots of different directories, not contained in a single file.

What is the name of this file?

---

