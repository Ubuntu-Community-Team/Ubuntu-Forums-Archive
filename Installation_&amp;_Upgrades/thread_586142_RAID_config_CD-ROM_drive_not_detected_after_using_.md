---
title: "RAID config: CD-ROM drive not detected after using mdadm (fiesty alt-CD install)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by dariusq2km on 2007-10-22
Hello software-raid gurus, 

Just hoping for a brief explanation of what happens to ATA device files (eg. hda) in /dev after RAID is configured using mdadm, and perhaps why my CD-ROM drive isn't being detected anymore after making a simple RAID-1 config. I've looked at the software raid howto but no mention of things such as /dev/.static/dev ... more below).

:some details:
After installing Fiesty using the alternate-install CD, and using mdadm to make a simple raid-1 config, the CD-ROM drive was not visible after reboot. 

It should be on hdd ( secondary-slave; it is when the Fiesty Desktop live CD is booted) but /var/log/dmesg shows no indication of detecting the CD-ROM drive at all during startup. 

The CD-ROM drive is alone on the second interface and jumpered as device-1 (slave). Note that there is no physical device-0 (master) on the second IDE interface at all. 

Looking around after startup, most of the usual ATA block device names have moved from /dev to /dev/.static/dev. This must be part of linux's software-raid config, I guess.

Later I tried jumpering the CD-ROM drive as device-1 (master). It is then detected and works normally. 

Is this something to do with SCSI device numbering perhaps (after mdadm config, the ATA devices are being refered to as /dev/sd[ab] and the CD-ROM as /dev/scd0 ).

Sincere thanks!

---

### Post by bruban on 2007-10-22
Sorry no idea on the disappearing CD.

In reading your post it sounds like you have both members of your raid array hanging off the same IDE / ATA controller. If that is the case you will probable get better performance by moving one of your disks over to your secondary IDE controller. 

If I have mis-read your post...my apologies.

---

### Post by dariusq2km on 2007-10-23
Bruban, Thanks for your reply. You are right about the raid drives being on the same controller. I had the same concerns about performance and rearranged things to minimise the potential for contention, but I'm not sure how important this would be to performance unless the raid driver can serialize asynchronous writes to each disc in a raid-1 volume (that might require a locking scheme to ensure updates were serialised). Any idea if the raid driver (md?) is sophiticated enough with its raid-1 implementation to manage parallel writes (i guess i'm assuming that at least some parts of the dirver are preemptable)?

Cheers!

---

### Post by bruban on 2007-10-23
Sorry, I can't answer that question. A quick search of the net should point you in the right direction.

As an aside, I've been running software RAID 1 via mdadm for around 2 to 3 years now with no problem, or noticeable performance degradation (devices on different controllers).

Bruce

---

