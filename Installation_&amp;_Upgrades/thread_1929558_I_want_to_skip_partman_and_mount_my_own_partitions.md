---
title: "I want to skip partman and mount my own partitions on the target mountpoint"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by lxvi on 2012-02-22
Hello,

I am in the process of setting up a multiboot system for the first time.  I have a PowerSpec G-211 with two ssd's (/dev/sda and /dev/sdd) and a RAID-1 comprising two 2TB drives (/dev/md127).  The first ssd has Windows 7.  The second ssd has been set up with several partitions, two of which are /boot (/dev/sdd1) and / (/dev/sdd2) for Centos 6.  /home and /var are on the RAID (/dev/md127p7 and /dev/md127p5).

I would like to do essentially the same thing with ubuntu server.  I want to use /dev/sdd1 as /boot (using grub to select which kernel) and /dev/sdd5 as / and /dev/md127p8 for /home and /dev/md127p9 for /var (although since debian doesn't seem to use /var the same way, maybe what I want is some part of /usr).

I understand (due to the error messages I'm getting) that these partitions need to be mounted under /target but how would I do that manually, and then do I need to pass any special parameters to base-installer?  I'm hoping if I set things up properly the rest of the installation tasks will just roll along smoothly.

Thanks

---

### Post by efflandt on 2012-02-22
I know nothing about the RAID end of it.

But when you get to the partitioning part of install, you want to select "Other" for manual partitioning, which should allow you to use specific existing partitions for specific mount points and whether to format any of them or not.  The bottom of that page also allows you to set where to install grub.

But isn't it risky using the same partition as /boot for more than one OS, or are you going to somehow split them into different directories?

---

