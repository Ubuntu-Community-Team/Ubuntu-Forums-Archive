---
title: "New HP Pavilion 8.04 install errors"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by FawnOfFeist on 2008-09-03
When I first installed the 64 bit 8.04 ubuntu I got an error that network devices could not be found.  Everything else installed without issue.

When I try to boot the first time it hangs at the splash screen, and then I get an error "udevd-event[1536]: run_program: '/sbin/modprobe' abnormal exit"   and it goes to busybox built in shell.

Anyone have any ideas what may be causing this, or what I can do to troubleshoot it?

Hardware is HP Pavilion dv5-1004nr.  AMD Turion 64 x2 ultra, SATA drive, 4Gb ram.

---

### Post by Sef on 2008-09-04
How many hard drives to you have?  Here's an old [Edgy Eft bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63402").

If you have a mixture of SATA and PATA hard drives, then try disabling the PATA hard drive.

---

### Post by FawnOfFeist on 2008-09-04
Only the single hard drive in this laptop.  It came with Vista installed, but I repartitioned it.  Now has one partition for vista, one for recovery, and then the Ubuntu partitions.

---

### Post by FawnOfFeist on 2008-09-05
Anyone else have any ideas to try for this? I can't get anything I try to work

---

### Post by falcon61102 on 2008-09-05
A number of people have been having trouble with errors like this lately.  You can try adding one of or a combo of the following to your menu.lst, add them to the end of the kernal line.  To test these, boot up and when you reach the GRUB, select Ubuntu then press "e" for edit then you can enter these.  There doesn't seem to be a single fix for everyone, it's all dependant on your hardware.
```
all_generic_ide 
floppy=off 
irqpoll
```

Also, some have found that if they change their BIOS settings for their HD from EIDE or IDE to SATA or RAID this seems to resolve the problem as well.

Here is further on this issue:
[http://ubuntuforums.org/showthread.php?t=765195&highlight=apci](http://ubuntuforums.org/showthread.php?t=765195&highlight=apci)

---

### Post by FawnOfFeist on 2008-09-06
I tried those three, but no luck.  Tried them in different combos as well, but still no dice.  BIOS has no settings for that unfortunately.

Going to keep searching and check out that article, but if anyone else has any ideas....

---

### Post by sujitkale on 2008-09-06
i have installed xp sp3 on my desktop.
my partition str is xp - data - ubuntu
i installed ubuntu 8.04.1
when you run cd of ubuntu on xp it gives u option to install ubuntu as application under xp 
u will have to give a partition for that and you r done
partition may be ntfs or fat doesn't matter
after reboot u will get boot menu with windows first and then ubuntu.
the drive on which ubuntu is installed is accesible through xp

---

### Post by FawnOfFeist on 2008-09-06
Not really interested in installing Ubuntu through Windows.  I want a true dual-boot.  There must be something I am missing for this install.

Who will be the one with the magic answer?

---

### Post by FawnOfFeist on 2008-09-08
> **FawnOfFeist said:**
> When I first installed the 64 bit 8.04 ubuntu I got an error that network devices could not be found.  Everything else installed without issue.

When I try to boot the first time it hangs at the splash screen, and then I get an error "udevd-event[1536]: run_program: '/sbin/modprobe' abnormal exit"   and it goes to busybox built in shell.

Anyone have any ideas what may be causing this, or what I can do to troubleshoot it?

Hardware is HP Pavilion dv5-1004nr.  AMD Turion 64 x2 ultra, SATA drive, 4Gb ram.

Still need a resolution to this issue.

---

