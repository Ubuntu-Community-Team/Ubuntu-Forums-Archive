---
title: "hang in Prepare Disk Space on Presario laptop"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by tomLA14 on 2007-03-14
tried to install Ubuntu 6.06 LTS on my Compaq Presario v6000t laptop...it stops at "Prepare Disk Space".

[LIST]
[*]Using the automatic parition I first set it to use half of my NTFS partition, 35 GB. It gave an error about could not create enough space.
[*]Then I tried smaller and larger sizes and it just hung, running for 8 hours.
[*]Then I tried Manually Edit Partition table and set it to cut down the big NTFS partition by half, and create new parititons linux-swap and ext3, both Primary.
[*]    Immediately got an "Error while resizing/moving /dev/sda1"
[/LIST]


Details:
Presario V6000t RD863AV#ABA        the $499 special
Intel Celeron M cpu 430 1.73 Ghz
502 MB ram
Pn - EZ855AV
OS Windows Vista Home Basic

By the way, seemed to run nicely from the CD...much quicker than Vista.

---

### Post by Kateikyoushi on 2007-03-14
Try to run a checkdisk first then defrag the partition few times, if hibernation or wap is located near the end of the drive you could disable them temporarily til you resize.

---

### Post by gus sett on 2007-03-14
greetings, just curious why .06 instead of .10

> **tomLA14 said:**
> tried to install Ubuntu 6.06 LTS on my Compaq Presario v6000t laptop...it stops at "Prepare Disk Space".

[LIST]
[*]Using the automatic parition I first set it to use half of my NTFS partition, 35 GB. It gave an error about could not create enough space.
[*]Then I tried smaller and larger sizes and it just hung, running for 8 hours.
[*]Then I tried Manually Edit Partition table and set it to cut down the big NTFS partition by half, and create new parititons linux-swap and ext3, both Primary.
[*]    Immediately got an "Error while resizing/moving /dev/sda1"
[/LIST]


Details:
Presario V6000t RD863AV#ABA        the $499 special
Intel Celeron M cpu 430 1.73 Ghz
502 MB ram
Pn - EZ855AV
OS Windows Vista Home Basic

By the way, seemed to run nicely from the CD...much quicker than Vista.

---

### Post by tomLA14 on 2007-03-15
I chose 6.06 instead of 6.10 because I assumed it would be more stable. I don't want to deal with a lot of issues just to get it working. But maybe 6.10 would be better at supporting the hardware in a new laptop like mine.

---

### Post by gus sett on 2007-03-29
Now there's a can-do spirit.  With 7.XX just around the corner,
6.10 would be similar to getting a new Honda in its 3rd yr
of availability...:idea:

---

