---
title: "Disk spinup every half hour"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ctrlER on 2009-09-22
Hi.

I'm trying to make a hard disk drive that's only used for backups stay in standby but there is something that is spinning the drive up every 30 minutes (exactly) or whenever I login to Gnome.

The drive stays awake for a few seconds and then gets spun down again (even though I set hdparm -S 12 (1 minute)).

Further more, every time the drive is spun up I get the following messages in dmesg:

```
[189046.000060] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[189046.000075] ata1.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
[189046.000077]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[189046.000082] ata1.00: status: { DRDY }
[189046.448025] ata1: soft resetting link
[189046.629893] ata1.00: configured for UDMA/100
[189046.629927] ata1: EH complete
[190844.988581] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[190844.988595] ata1.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
[190844.988597]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[190844.988603] ata1.00: status: { DRDY }
[190846.444029] ata1: soft resetting link
[190846.625872] ata1.00: configured for UDMA/100
[190846.625904] ata1: EH complete

```

As you can see, this shows two occurrences of the problem, and they're ~ 1800 seconds (30 minutes) apart: 190844.988581-189046.000060 = 1798.988521
I thought it could be smartd but I disabled smartd and the problem persists.

Should I post a bug report?
I don't know exactly against to post the but because I don't know what is causing this.

---

### Post by ctrlER on 2009-09-23
I've filled a bug: [https://bugs.launchpad.net/ubuntu/+bug/435190](https://bugs.launchpad.net/ubuntu/+bug/435190)

and attached is the dmesg output with echo 1 > /proc/sys/vm/block_dump.

Could it be kjournald2 that is causing the spin ups?

The disk in question is /dev/sda and apparently there is no write actions to the disk at the time of spin up.
I don't know how to check if there is any read actions.
Can someone help me?

---

### Post by ctrlER on 2009-09-25
I figured out it's devkit-disks-daemon that is doing the spinning up. Now I have to find out how to change its behavior so it doesn't spin up the hdds.

---

### Post by drumsticks on 2009-09-27
I*have nothing to contribute but encouragement.  I'm keeping an eye on this thread to see what you've come up with.  Keep up the good work.  Thanks.

---

### Post by raduc on 2009-10-10
I have an identical problem (hard disks waking up every half hour). Subscribed to the bug too, thanks for submitting..

---

