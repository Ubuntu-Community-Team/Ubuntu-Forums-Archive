---
title: "Partitioning on an EEE 900"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by captcadaver on 2009-11-22
Hi,

I'm installing Ubuntu Netbook Remix 9.10 on my EEE 900 but I've got no idea how to partition it. The 900 has:

One 4 GB SSD (primary)
One 16 GB SSD

Help?

---

### Post by captcadaver on 2009-11-23
Any help would be appreciated.

Thanks!

---

### Post by captcadaver on 2009-11-23
Anyone got any suggestions? Thanks.

---

### Post by snowpine on 2009-11-23
Hi there, there's no one "right way" to do it. Based on what I've read on forums.eeeuser.com, most 900 users choose Manual Partitioning with the / (root) partition on the faster 4gb drive and /home on the slower 16gb drive. I do not personally recommend a swap partition on a solid state drive.

Good luck!

---

### Post by captcadaver on 2009-11-23
> **snowpine said:**
> Hi there, there's no one "right way" to do it. Based on what I've read on forums.eeeuser.com, most 900 users choose Manual Partitioning with the / (root) partition on the faster 4gb drive and /home on the slower 16gb drive. I do not personally recommend a swap partition on a solid state drive.

Good luck!

Thanks for your help.

There are all of ext4 type, correct?

What's wrong with using the swap space? Ubuntu gives me crap if I don't use one.

Also, last time I installed UNR, I had a nasty problem where Ubuntu kept telling me everything was full. Was it filling up only my 4 GB SSD? How can I prevent this? Why don't I just put everything on my 16 GB SSD if all the packages and such are installed on the 4 GB SSD?

---

### Post by snowpine on 2009-11-23
ext4 is the default for 9.10; I personally am using ext4 on my Dell Mini 9's solid state drive with no problems.

At the time I bought my first EEE, the "word on the street" was that a swap partition would reduce the lifespan of the drive (since swap is constantly being written and rewritten). I do not know if this is still the case with current SSD technology but I am still hesitant. Also, my netbook has 1gb ram and I seldom exceed 200-300mb, so I have no need for swap. If you regularly approach your RAM limit, use your own judgement.

If you decide not to use swap, the installer will give you a message like "are you sure? do you want to go back?" but you can safely ignore it. :)

To answer your "drive full" question, applications and system files go in the / partition. If you create a separate /home partition (which is not the default; you need to choose Manual), your personal documents will be there. So, by putting / on the 4gb partition and /home on the 16gb, your documents, music, videos, photos, etc. will be on a separate drive from your system files and you'll have an easier time managing drive space. (If your usage is non-typical, for example, you install lots of applications but not a lot of documents, maybe a different solution is better.... all my answers so far should be prefaced "for the average user...")

---

### Post by captcadaver on 2009-11-23
> **snowpine said:**
> ext4 is the default for 9.10; I personally am using ext4 on my Dell Mini 9's solid state drive with no problems.

At the time I bought my first EEE, the "word on the street" was that a swap partition would reduce the lifespan of the drive (since swap is constantly being written and rewritten). I do not know if this is still the case with current SSD technology but I am still hesitant. Also, my netbook has 1gb ram and I seldom exceed 200-300mb, so I have no need for swap. If you regularly approach your RAM limit, use your own judgement.

If you decide not to use swap, the installer will give you a message like "are you sure? do you want to go back?" but you can safely ignore it. :)

To answer your "drive full" question, applications and system files go in the / partition. If you create a separate /home partition (which is not the default; you need to choose Manual), your personal documents will be there. So, by putting / on the 4gb partition and /home on the 16gb, your documents, music, videos, photos, etc. will be on a separate drive from your system files and you'll have an easier time managing drive space. (If your usage is non-typical, for example, you install lots of applications but not a lot of documents, maybe a different solution is better.... all my answers so far should be prefaced "for the average user...")

Cool, thanks for your help.

---

### Post by sgosnell on 2009-11-23
4GB is tight for a full install.  You won't have a huge amount of room for installing new apps.  You can put everything on the 16GB drive if you want, or put / on it and put /home on an SD card.  

My 900 has only one SSD, and I've upgraded that to a SuperTalent 32GB SSD, and things are much, much better - faster, and obviously more space.  I've set it up with 10GB for /, and the rest for /home.  I do have a swap partition, but it's rarely used at all.  You normally only need it for hibernation, and I never do that, choosing either suspend or a full shutdown.  A cold boot doesn't take that long, and suspend doesn't use swap, it just keeps the RAM refreshed with battery power.

All that said, there are lots of ways to do it, and it's your machine, so do whatever makes the most sense to you.

---

