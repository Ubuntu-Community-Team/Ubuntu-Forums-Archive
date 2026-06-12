---
title: "Grub install problem ...please help"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by ManyBeers on 2008-09-10
I have a Sony Vaio laptop with WindowsXP on it and tinight I installed Ubuntu 8.04
on it but i had a small problem. I elected Not to install Grub in the master boot record
for my reasons which I don't want to go into here. So here'e the deal-Ubuntu didn't boot
to finish the installation which means I probably installed Grub incorrectly.I will outline
my exact partition and where I installed Grub. Hopefully someone can confirm if my setup is correct. By the way I used the Alternate CD and not the Live cd.
 Hard drive 20 gb:
C:\drive NTFS (Windows 6.5 gb) 1st partition on drive..primary
D:\drive Fat32 (apps,storage6.5 gb) 2nd partition....primary
Linux Swap 630 MB 3rd drive on partition ...primary
Ubuntu ext3 remainder of drive 4th drive on partition...primary I set it to boot
When asked by the Grub setup where to put Grub I typed:
............................................................/dev/sda/4..........no error was given and the install proceeded
is that correct according to my partition layout.

---

### Post by ManyBeers on 2008-09-11
> **ManyBeers said:**
> I have a Sony Vaio laptop with WindowsXP on it and tinight I installed Ubuntu 8.04
on it but i had a small problem. I elected Not to install Grub in the master boot record
for my reasons which I don't want to go into here. So here'e the deal-Ubuntu didn't boot
to finish the installation which means I probably installed Grub incorrectly.I will outline
my exact partition and where I installed Grub. Hopefully someone can confirm if my setup is correct. By the way I used the Alternate CD and not the Live cd.
 Hard drive 20 gb:
C:\drive NTFS (Windows 6.5 gb) 1st partition on drive..primary
D:\drive Fat32 (apps,storage6.5 gb) 2nd partition....primary
Linux Swap 630 MB 3rd drive on partition ...primary
Ubuntu ext3 remainder of drive 4th drive on partition...primary I set it to boot
When asked by the Grub setup where to put Grub I typed:
............................................................/dev/sda/4..........no error was given and the install proceeded
is that correct according to my partition layout.

I fixed it using the System Rescue CD and GParted.For some reason
Ubuntu was not flagged to boot. It is now.

---

