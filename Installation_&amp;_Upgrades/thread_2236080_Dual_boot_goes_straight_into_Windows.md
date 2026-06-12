---
title: "Dual boot goes straight into Windows"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by Nemo103 on 2014-07-24
Hi, 

I've had a dual boot system for a few years now, Ubuntu and Windows 7. The Windows half stopped working (Windows Explorer crashed within the first few seconds, so I couldn't actually start any programs...) at least a year ago, and I decided I wanted to use it again, so used the built-in recovery tools. When I rebooted it went into GRUB rescue and I couldn't manage to boot anything. 

I used a LiveUSB to run boot-repair - [paste.ubuntu.com/7843982]("http://paste.ubuntu.com/7843982") 

With the USB removed, Windows then booted fine and works as well as we might expect. The problem is there's no option for me to boot into Ubuntu instead. 

I ran boot-repair again - [paste.ubuntu.com/7846526]("http://paste.ubuntu.com/7846526") - and the problem persists. 

What do I do now? Sorry if the answer to this is really obvious to those of you who understand the workings of these things. 

Thanks, 

Alistair

---

### Post by yancek on 2014-07-24
Using the Recovery CD/DVD for windows usually set to factory defaults.  You don't have any Linux partitions, sda1,sda2,sda3 are windows (ntfs) and sda4 is an Extended partition and the only thing in there is a logical swap partition.  The only references I see to Linux/Ubuntu/Grub are on your flash drive, sdb.  You will need to shrink a windows partition from windows to create space on which to install Ubuntu.

---

### Post by Nemo103 on 2014-07-24
Oh, so the Windows recovery tool erased all the partitions, not just its own. That explains it. 

Thanks for your help!

---

