---
title: "Driver needed for WD 2TB"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by KLStringer on 2010-04-02
[LEFT]I'm trying to set up a Dell PowerVault 745n with Ubuntu server 9.10 on a Western Digital 2TB Caviar Green HDD (GPT formatted if that matters)  that isn't auto-detected and I'm prompted to choose a driver for it. I've went through all the different options that I'm given and none of them work.

Not sure what I need to do to detect the drive.
[/LEFT]

---

### Post by KLStringer on 2010-04-02
Still looking for help if, anyone can point me in the right direction it would be much appreciated all my searches haven't turned up anything.

---

### Post by srs5694 on 2010-04-02
Drivers are not required for internal hard disks in Linux; rather, drivers are needed for hard disk *controllers,* which are typically part of the motherboard but can be plug-in cards. If Linux can see other hard disks on the computer but not this one, then chances are something is wrong with the hard disk or a cable or connector. If Linux can't see any hard disks on this motherboard or other controller, then you should investigate Linux support for the motherboard chipset or disk controller card. If the disk is an external device, then you may need support for USB, FireWire, or whatever connecting standard you're using. Post more hardware details if you continue to have problems.

Also, a heads-up: The most recent WD Caviar Green drives use "Advanced Format" technology, which requires special care when partitioning. See [this page](file:///home/rodsmith/homepage/gdisk/advice.html) for details, and particularly the "Partition Alignment Issues" section. If you get it wrong, there can be some pretty serious performance degradation, depending on what filesystem you use.

---

### Post by KLStringer on 2010-04-02
We started thinking the same thing because no matter what HDD we put in there it never detects it regardless of size or format. All of the drive slots are connected to a SATA card going to look into that as maybe the problem.

Thanks for the reply

---

