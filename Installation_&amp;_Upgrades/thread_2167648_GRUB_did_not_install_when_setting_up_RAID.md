---
title: "GRUB did not install when setting up RAID"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by jason13 on 2013-08-14
I've been using a thumb drive installation ever since my HD crashed last year. I replaced it with two 3.0 TB drives with the intent of setting up a RAID1. Each time I try to install Ubuntu 12.04 the bootloader fails to install. I now have a real need of a better installation of Ubuntu. The system installed but I can't boot into it, and attempts to install GRUB to another device and have it recognize 12.04 have also failed. I've been trying off and on for a while now but nothing has worked. Any help you can provide is appreciated.

---

### Post by lukeiamyourfather on 2013-08-14
Why RAID 1? Is it mission critical that the machine not go down? If you don't already have an established backup routine I'd use the second disk for backup instead of RAID 1.

---

### Post by jason13 on 2013-08-14
But if I'm using RAID1 backup is a no brainer event, right? Can you suggest a method of backup that I might be able to apply to after installing the system on one drive? I'm mostly concerned about my /home folder.

---

### Post by lukeiamyourfather on 2013-08-14
Stop. RAID 1 is not backup. End of story. If you delete a folder accidentally it will be deleted from both drives simultaneously. If you get malware that destroys files or infects them it will happen to the files on both drives simultaneously. The only thing RAID 1 is good for is keeping a machine running if a hard disk dies, that's it. If you want backup look at a utility like Duplicity, or you can run backups with rsync and cron if you prefer to use the terminal. If your goal is to not lose files important to you then setup the second drive for backup, not RAID 1 (or any other RAID level for that matter).

---

### Post by jason13 on 2013-08-14
How do these methods work. I've used a backup program from WD (not recommended) and while it held my data, it was a pain to use. I want data duplicity without the headache of manual backups.

---

### Post by lukeiamyourfather on 2013-08-14
Sorry, I said Duplicity but I meant Deja-Dup which is the default backup utility in Ubuntu that has a GUI and scheduling (it's a GUI for Duplicity basically). Another backup utility with a GUI is Bacula.

---

