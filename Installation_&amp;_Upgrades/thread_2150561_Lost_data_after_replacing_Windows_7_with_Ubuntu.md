---
title: "Lost data after replacing Windows 7 with Ubuntu"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by sinnerz2000 on 2013-06-01
I had windows 7 before with 2 partitions, while installing Ubuntu I selected replace windows 7 with Ubuntu and after installation I see that it has formatted my whole hdd and not only the partition in which windows 7 was there. Have I lost all my data forever? Please advise.

---

### Post by sandyd on 2013-06-01
moved to own thread

---

### Post by sinnerz2000 on 2013-06-01
Please move this in a bigger thread, I won't get any replies if its a new thread.

---

### Post by ahallubuntu on 2013-06-01
~

---

### Post by fantab on 2013-06-02
> **ahallubuntu said:**
> Open a terminal in Ubuntu (Crtl - Alt - t) and type this:

```
sudo fdisk -l
```

What's the output?

If you don't see any partitions labeled "HPFS/NTFS/exFAT" - then yes, I'd guess your data is gone.

Do ths from Ubuntu install Disk. Boot with it, "Try Ubuntu" after loading the desktop, open Terminal [ctrl+alt+T] and run the above command.
Stop using your HDD, if you want rescue your DATA.

If you have access to another Windows machine then:
1. Remove the HDD from the computer
2. Plug it in a PC with Windows.
3 Download and Install [**'Mini Tool**]("http://www.minitool-partitionrecovery.com/")' partition/data recovery tool
4. Let it do its thing then see what Data you can rescue. Check the file size, if its zero then the data is lost.
5. If you find data that can be recovered then you may have to buy the Licence to recover it.

If you think your DATA is not worth the $ but want to rescue it if you can use a 'free' tool, then try: **[TESTDISK]("http://www.cgsecurity.org/wiki/TestDisk")**.

---

