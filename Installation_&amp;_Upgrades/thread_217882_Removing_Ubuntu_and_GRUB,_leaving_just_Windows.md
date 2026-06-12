---
title: "Removing Ubuntu and GRUB, leaving just Windows"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by zeeR on 2006-07-17
I need to remove ubuntu because my computer is going to be fixed, and i want it to go just with windows, on the entire disk. Right now, i have windows on a 50GB partition, and ubuntu on the rest (30GB), dual booting. What should i do to uninstall ubuntu, make the windows partition the only one, with 80GB, and making it boot straight into windows, without grub?

I thought of running ubuntu's live cd and running Gparted, but i'm afraid that may bring boot problems...When i remove Ubuntu, will the computer automatically boot into windows?:-k

---

### Post by Jagot on 2006-07-17
To get rid of GRUB so the computer just boots into Windows you need to boot with the Windows disk and navigate to the recovery console.  When you are at the command prompt type:

```
fixmbr
```

With regards to getting rid of the Ubuntu partition, you could just use GParted from the Live CD to delete the partition and create a new NTFS partition or leave it blank.  According to the GParted site, it can expand NTFS partitions, but I've never tried it and don't know if it will wipe your disk.

---

### Post by mmcmonster on 2006-07-17
Sorry to see you leave the Ubuntu world.  Hope you enjoyed the experience.

Were you just not using Ubuntu for some reason?  I noticed that if you are just playing around with a linux distribution, a 10GB partition is usually enough.  And in the days of large hard drives, most people can afford 10GB off the top of an 80GB drive. :-)

Anyway, hopefully you were able to experience the great community here.  I've never seen a better forum for ***any*** OS.

---

### Post by zeeR on 2006-07-17
> **mmcmonster said:**
> Sorry to see you leave the Ubuntu world.  Hope you enjoyed the experience.


I'm not leaving!! Ubuntu impressed me so much, i found myself using it over windows, and i installed it on my other computer,a desktop, where i keep using it. It's a relatively old computer, and it really impressed me to see it running linux so fast and stable.:o  The problem now is that my laptop (Acer Aspire 1690) isn't well, i think the motherboard isn't working well,so acer is going to repair it.I'm just restoring the disk to how it came in first place,cause i'm afraid they complain about the partitions and dual boot,and even blame the problem on that...:-| Do you think they will? Or can i just let the laptop go as it is,with the partitions and both OS's?

Anyway, as soon as it returns, i will, without a doubt, reinstall Ubuntu on a 10/15GB partition, and use it as my main OS again..:)

---

### Post by mmcmonster on 2006-07-17
Heh. ;-)

You probably did the right thing.  Better to keep only what the tech guys expect on the machine and restore when you get it back. :rolleyes:

---

