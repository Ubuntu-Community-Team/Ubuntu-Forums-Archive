---
title: "remove MBR partion from an SDHC"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by cisoprogressivo on 2008-05-06
Hi,
I want to install Ubuntu on a SDHC to use it on my eeepc.
I used eeexubuntu on it without problem, but now i want to try Ubuntu.
When I install it on the SDHC card, I get at the end an error about the installation of the grub.
Maybe the partition is corrupted, but how can I solve this?

I tried to format it with mkfs and also in windows but nothing changes.
Any ideas?

Thank you, and sorry for my English

---

### Post by Tom Mann on 2008-07-21
Hi there,

I've learned from a few sites recently about this - I find that you need to figure out the name of your SD card device (eg /dev/sdg in my case) by typing the following.

```
sudo fdisk -l
``` (you will need to enter your password when asked)

once you know this the command is (be very careful, type the wrong device and you could lose valuable data or even your OS!)

```
sudo mkfs.msdos -I /dev/sdg
```
(NB: /dev/sdg was what I had to put in, you need to put in whatever matches your SD card from the previous command - this command will wipe the card clean!)

If in doubt, post the result of sudo fdisk -l here, along with the capacity of your SD card.

---

