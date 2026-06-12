---
title: "Moving Linux /boot partition on a 14.04 / windows 8.1 dual boot"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by el_garicimo on 2014-05-17
Heyo,

Over the past year I've started to teach myself web development, and in doing so started to mess around with Linux. As I'll be starting a bootcamp soon, I spent much of the past month learning linux more, spending hours and hours figuring out how to get the touchpad configured, fix silly tweaks, etc, and I finally got it just how I want it, dual booting with Windows 8.1.

A full backup of my system via clonezilla in hand, I then tried to do a couple other things--

1.) Resize windows partition from 120 GB to 100 GB to give some more space to my Data partition

2.) Move my some unallocated space at the end of the hard drive (16 GB) to my Data Partition

After moving the partitions, Xubuntu 14.04 stopped booting. I realized this was probably because when installing, and clicking "do something else", I created a seperate partition for /boot.

**Is there a way to make the /boot directory load on my Root partition, without having to reinstall everything? It took a while to get my distro configured just the way I like it.**

Thanks!

---

### Post by Luke M on 2014-05-17
What do you mean by stopped booting?

---

### Post by oldfred on 2014-05-17
Just to confirm where everything is at, post link to BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have moved boot files to a /boot partition and it worked but I decided I did not want it and moved them back, so it can be done.

---

