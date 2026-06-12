---
title: "Boot problems with no definitive answer"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by crazymouse on 2008-08-27
Alright, a lot of people seem to have problems booting to their hard drives, but I'm not sure that they have had the same situation as I have. I've searched the forums, and it seems like the threads who have a very similar situation are unanswered, so I thought I would try and ask myself. Here goes:

I'm installing Hardy on my machine. I had to choose Safe Graphics mode to get it to boot into LiveCD (just FYI, I dont' think that really has any bearing on the siutation). My machine is an Asus M2N-E, with 2 SATA drives, and one IDE cdrom. On the first drive, sda, I have one primary partition, which is ext3, mounted to /, boot flagged.

The second drive simply has a partition I've set aside for storage.

Installation went rather smoothly, and it asked me to remove the disk and press enter. I did, and when the computer restarted, it gave me the dreadful "Disk boot failure, please insert system disk and press enter" message. My boot order is correct, ie: Cd, HD, Rem, USB. I have even tried removing all options besides harddrive.

I tried fixing grub as instructed by another post via the liveCD. That didn't make any difference.

For the information of those who might support me, I tried using the liveCD's Boot From First Hard Drive option, only to be faced with the error, "isolinux: disk error 01, AX = 0201, drive 80."

If anyone has any suggestions, please keep me informed. Thank you.

---

### Post by VMC on 2008-08-27
Can you reboot using the livecd and from a terminal type:

```
fdisk -l
```

Then we can get a picture of how Linux sees your hard drives. It sounds like a BIOS issue, but usually that would say no operating system.

---

