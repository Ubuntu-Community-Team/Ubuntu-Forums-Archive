---
title: "Installing on Dell Mini 9"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by lilyphoenix on 2011-05-19
I'm trying to install ubuntu netbook remix on my dell mini 9. There's a small 32 MB partition, and I think from googling it's some sort of dell diagnostics. Anyway, I figured I leave it and install to the larger partition that 8.04 was installed in, but I'm having trouble interpreting the partition menu. I think I want to check format on the big partition, choose ext3 as the format since that's what it was already, and then choose the big partition as device to install boot loader. Can anyone confirm that this is how to work it.:confused:

---

### Post by garvinrick4 on 2011-05-19
> **lilyphoenix said:**
> I'm trying to install ubuntu netbook remix on my dell mini 9. There's a small 32 MB partition, and I think from googling it's some sort of dell diagnostics. Anyway, I figured I leave it and install to the larger partition that 8.04 was installed in, but I'm having trouble interpreting the partition menu. I think I want to check format on the big partition, choose ext3 as the format since that's what it was already, and then choose the big partition as device to install boot loader. Can anyone confirm that this is how to work it.:confused:
Is your USB install flash drive Live, can you boot it and choose Try Ubuntu and then open
a terminal and:
sudo fdisk -l (lower case L)
or you can open a application called "gparted" and it is part of
your Graphic user interface and will show you the partition table.
#Never put grub in a partition number put it in sda and if you have a second drive and are
installing linux put grub in sdb and then sdc and so on and on. Never sda1 or sda5 always sda
# When you install say to partition sda1 for / and make it ext4 and grub in sda
# / being your files system, ext4 is format and grub (boot manager) in sda

---

