---
title: "error: no such device (+ a bunch of numbers)"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by apollo_el on 2010-08-11
Hello to all fellow "Ubunters",

  This is my first post here. 

  I decided to install Kubuntu on my external hdd (connected to my laptop). Laptop has Win 7 and the external hdd used to have FC13 (no installation problems there). After the installation finished, it asked me to reboot, I did, and I got :

[B]"error: no such device (+ a bunch of numbers)"
and
grub rescue. [/B]

I have seen here similar topics and read most of them. I fixed this by re-installing and under *"Advanced"* (**i had omitted to do that earlier**)..... I chose for the  installation of the **GRUB boot loader the location: /sdb1** ,which is the /boot  partition shown below. The point is that I'd like to have a separate /boot partition and install GRUB there. I assumed that this would fix things up, afterall it made sense to me.  Now, however, I get:

[B]"error: file not found
and grub rescue"[/B]

, when I boot from the external hdd (configured this in the Bios).  Also, I have no problems booting to WIN7, now, b/c I did the **fixboot** and** fixmbr** procedure.


SO......

My goal is simple: to have Kubuntu installed on my external hdd (sdb), like I used to have FC# (various versions) and no matter to which computer i connect it to boot from the external hdd to Linux...so this is **NOT a dual-boot case.**..forget about Windows on the laptop. I just want Linux on a separate external hdd. More specific, for Linux I usually have:

sdb1: /boot partition (about 500MB)
sdb2: / (about 13GB)
sdb3: swap partition (1.5*RAM=6GB)
sdb5: separate /data partition (about 40GB)

It's a small 60GB external hdd. 

I don't understand why I am having this issue with Kubuntu; afterall I never had these probs with FC .I'm not an expert in Linux, but I have a few years experience with it, and still prefer to keep things simple...at least i try.


Could some1 plz guide me through? I'm a bit confused, after dealing with this for 2 days now. 

Thank you for reading this.

---

### Post by apollo_el on 2010-08-12
OK. Just a pointer to all those current+future readers. Decided to forget about the above-mentioned /boot partition, so I did it the old-fashioned way with just a / (root partition) + swap+ /data (partition). This way the installation works with no errors, whatsoever. Its a bummer (k)-ubuntu seems to have this bug (??????)

---

### Post by dabl on 2010-08-12
The booting problem was probably due to an "auto" boot option in /etc/fstab, for a device/partition that was not connected during booting.

FYI, today there are very few reasons to make a separate partition for "/boot" -- people who need it know why they do.

---

