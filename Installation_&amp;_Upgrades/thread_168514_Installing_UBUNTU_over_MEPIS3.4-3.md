---
title: "Installing UBUNTU over MEPIS3.4-3"
date: 2006-04-30
forum: Installation &amp; Upgrades
---

### Post by denregan54 on 2006-04-30
I am running WinXP Pro on my main HDD and MEPIS 3.4-3 on a 2nd HDD.
It is a dual boot setup. I wish to replace MEPIS with UBUNTU and would like to know how I should go about it.
I am a Linux newbie and will appreciate advice and pointers.

---

### Post by aysiu on 2006-04-30
Do a regular (not expert or server) install by just pressing Enter after you boot up.

Then when you get to the partitioning part, select **Manually Edit the Partition Table**.

For the Mepis partition, select it, select Use as Ext3, select Format this partition, and select mount at /

Then proceed.

---

### Post by denregan54 on 2006-05-01
aysiu

Many thanks for that.
I wonder if there is an issue with the bootloader which I installed at the time I installed MEPIS ? I don't want my first ( hda ) HDD with WinXP installed to become unavailable. Will the existing bootloader remain effective ?

---

### Post by aysiu on 2006-05-01
No, you should ask Ubuntu to install Grub to the MBR--it'll overwrite Mepis' Grub. There's no point in keeping Mepis' Grub on there, as Mepis' Grub configuration file will *not* be there.

---

### Post by denregan54 on 2006-05-01
Aysiu
Many thanks for that.
I will install UBUNTU as soon as I get back from a trip this week.

---

