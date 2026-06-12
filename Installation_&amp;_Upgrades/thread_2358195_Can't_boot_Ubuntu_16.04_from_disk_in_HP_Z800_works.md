---
title: "Can't boot Ubuntu 16.04 from disk in HP Z800 workstation"
date: 2017-04-10
forum: Installation &amp; Upgrades
---

### Post by bobjervis on 2017-04-10
I just bought an HP Z800 workstation and I tried installing Ubuntu 16.04 from a USB stick. The USB stick booted and ran the full install sequence. I chose the following configuration:

- 500 GB drive: GRUB partition + Ubuntu partition
- 2TB drive: /home

Use LVM: one logical volume for the Ubuntu partition on the 500GB drive and 1 logical volume in the 2TB drive.

After install I get the following message from the BIOS: Attempting Boot from Hard Driver and then it hangs.

If I 'try Ubuntu' from the USB stick, fdisk reports all the volumes and disk partitions consistently with what I installed. When I mount those logical drives, the files are all there. I've re-run the install multiple times, I've run the BIOS disk drive tests with no errors (and I haven't seen anything like a hardware failure when trying to read/write to the physical disks).

I've been trying things for three days with no luck. Only the USB stick successfully boots.

---

### Post by mörgæs on 2017-04-12
Does 17.04 work better?

---

### Post by bobjervis on 2017-04-12
Turns out that the problem is with the bootloader that comes with the Ubuntu 16.04 ISO. I installed Fedora, then defined a menuentry in its bootloader to chain to Ubuntu and now I can boot Ubuntu from the chained loader.

---

### Post by bobjervis on 2017-04-12
I haven't tried 17.04. I've been using 16.04 on other systems so I wanted to minimize the variables for now.

---

### Post by mörgæs on 2017-04-13
Good that the problem is solved. Please mark the thread so in order to help other users.

---

### Post by fchen0000 on 2018-01-27
would you please elaborate how to do so? Thanks!

---

### Post by mörgæs on 2018-01-28
You just google *ubuntuforum solved thread* :-)
It gives for example the link here: [https://ubuntuforums.org/showthread.php?t=2355489](https://ubuntuforums.org/showthread.php?t=2355489)

---

