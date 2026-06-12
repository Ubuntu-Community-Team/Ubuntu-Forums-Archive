---
title: "Help with Installing Highpoint 2310 RAID drivers"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Krogoth255 on 2010-01-25
I am having some difficulty installing Highpoint 2310 drivers for Ubutnu 9.10 AMD64.

I had followed the directions on Highpoint's website. For some reason, when I run "sudo sh install.sh" it saids. 

```
The disk you insert is for linux kernel 2.6
Please reboot the system to use the new driver module.

```

I reboot the system and attempt to see if the drivers were present, but I could not find them.

FYI, RAID already has a NTFS partition on it. Would that have any effect?

Any suggestions or help will be greatly appreciated.

---

### Post by pirateghost on 2010-01-25
> **Krogoth255 said:**
> I am having some difficulty installing Highpoint 2310 drivers for Ubutnu 9.10 AMD64.

I had followed the directions on Highpoint's website. For some reason, when I run "sudo sh install.sh" it saids. 

```
The disk you insert is for linux kernel 2.6
Please reboot the system to use the new driver module.

```I reboot the system and attempt to see if the drivers were present, but I could not find them.

FYI, RAID already has a NTFS partition on it. Would that have any effect?

Any suggestions or help will be greatly appreciated.


i had the same problem.  i grabbed the source version and compiled myself. it was easier

---

### Post by Krogoth255 on 2010-01-25
Thanks, compiling from the source did the trick.

:)

---

### Post by Lostdrifter0001 on 2010-01-28
Krogoth255 could you please tell me how you compiled your drivers. I have a 2320 raid card and I need to do the same but i cant seem to get it to work

---

