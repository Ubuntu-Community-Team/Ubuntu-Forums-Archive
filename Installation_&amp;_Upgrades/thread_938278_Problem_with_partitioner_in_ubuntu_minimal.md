---
title: "Problem with partitioner in ubuntu minimal"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by columbus_uncle on 2008-10-04
I am trying to install the minimal install of ubuntu on an old gateway PII.  I can get up to the partitioner at which point I get an error message saying:

Input/output error during read on /dev/hde

I ignore the error three times and get another error:

The creation of swap space in partition #5 of IDE3 master (hde) failed.


What am I doing wrong and what can I do to install ubuntu on this machine?

---

### Post by cariboo on 2008-10-04
Do you really have 5 hard drives in your computer? This almost indicates that you have the drive on an expansion card that isn't being detected properly. Check you cables and jumpers to make sure the hard drives are being detected in the proper order.

Jim

---

### Post by columbus_uncle on 2008-10-04
> **cariboo907 said:**
> Do you really have 5 hard drives in your computer? This almost indicates that you have the drive on an expansion card that isn't being detected properly. Check you cables and jumpers to make sure the hard drives are being detected in the proper order.

Jim

I was confused by that too.  I definitely have only one hard drive.  Excuse my noobness, but how would I know if the drive is plugged in correctly?

---

### Post by columbus_uncle on 2008-10-05
anyone have any ideas about this?

---

### Post by columbus_uncle on 2008-10-08
bump

---

### Post by snowpine on 2008-10-08
Can you post your system specs?

I would recommend partitioning your drive (using an Ubuntu Live CD, GParted CD, or similar) prior to the installation. If you set up your partitions ahead of time, you can select Manual Partitioning from the installer. Also, having the swap partition already set up may help the installer (not sure if that's true with the Mini ISO though).

---

### Post by columbus_uncle on 2008-10-08
> **snowpine said:**
> Can you post your system specs?

I would recommend partitioning your drive (using an Ubuntu Live CD, GParted CD, or similar) prior to the installation. If you set up your partitions ahead of time, you can select Manual Partitioning from the installer. Also, having the swap partition already set up may help the installer (not sure if that's true with the Mini ISO though).

The specs:

Pentium III 750 Mhz, 128mb RAM, 10 gig HD

I can't seem to get the live cd to work.  The system freezes when the desktop shows.  I assume this is because the system does not have enough ram for the normal version of 8.04.  I can't seem to figure out how to partition the hd manually using the mini iso.

---

### Post by snowpine on 2008-10-08
128mb is definitely enough ram to use the mini.iso, but not enough for the Ubuntu live cd. You should do a little research and find a live cd that will run with 128mb and has a partitioning tool such as gparted. (The mini.iso does not have a separate partitioner unfortunately.) If you can get a live CD going to set up the partitions, maybe run some disk diagnostics, that might help you prepare the disk so installation goes more smoothly. Sorry I can't be of more specific help, but I've never dealt with Linux on a 128mb system before.

---

### Post by cariboo on 2008-10-08
Here are a couple of things I would check.

1. Make sure the ide cable isplugged into the first ide port on the motherboard
2. Make sure you have the jumper on the hard drive set to master
3. Although this shouldn't make any difference, make sure the bios is detecting the hard drive properly.

Jim

---

