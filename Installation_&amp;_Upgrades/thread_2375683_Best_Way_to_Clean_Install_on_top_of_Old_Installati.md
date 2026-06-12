---
title: "Best Way to Clean Install on top of Old Installation"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by gr8 on 2017-10-26
I've got a tower with two separate 2TB hard drives. The first hard drive has Windows 10 on it. The second hard drive has Ubuntu 16.04 on it. This is a dual boot system that defaults to Windows, but you can pick which system to boot, I think it's through GRUB, when I turn on the computer. UEFI, Legacy, I don't know.

What's the best way to wipe out my 16.04 installation and get 17.10 on there? Should I pick "something else" during installation and delete all partitions, then add a root /, a /home, and a swap space? Or should I just pick one of the automatic "erase and reinstall" options? I do not want to save any files or settings from my home directory. I do want to leave Windows 10 as is.

---

### Post by Impavidus on 2017-10-27
Use the "something else" option, the other options might damage Windows. You don't have to delete the partitions, you can just select the existing partitions and format them. And you don't really have to format your /home partition, the new applications should have no problem handling old versions of config files. Unless you want to clean the /home partition too, but that defies the purpose of /home partitions.

You don't really need a swap partition any more, from 17.04 on Ubuntu will use a swap file by default if no swap partition is present. But you can use a swap partition if you prefer.

---

### Post by VMC on 2017-10-27
> **Impavidus said:**
> ...You don't really need a swap partition any more, from 17.04 on Ubuntu will use a swap file by default if no swap partition is present. But you can use a swap partition if you prefer.
I didn't know this. I've been using swap partition forever. I searched and found this regarding [Ubuntu default swapfile]("http://linuxbsdos.com/2017/04/18/swap-partition-out-swap-file-in-on-ubuntu-17-04/").

---

### Post by gr8 on 2017-10-27
What's the best way to merge my old swap partition with my root partition? And do I need to worry about keeping certain partitions at the end of my hard drive? What's that about?

---

### Post by Impavidus on 2017-10-28
If the swap partition is adjacent to the root partition, you can simply delete the swap partition and expand the root partition. Or delete the root partition too and create a new one. If they're not adjacent, it gets more complex. But there's nothing wrong with using a swap partition, so you could simply keep it too. I still have one on my 17.04 system (although it never really gets used).

---

### Post by kc1di on 2017-10-28
You don't really need the swap unless you using a laptop and want it to hibernate or suspend when lid is closed , then you'll need it. The files or partition at the end of the drive are usually reserved for windows use. But I've also seen them placed there by HD manufactors I'm not sure of their purpose, but I would leave them if you don't really need the space.

---

### Post by VMC on 2017-10-28
> **gr8 said:**
> What's the best way to merge my old swap partition with my root partition? And do I need to worry about keeping certain partitions at the end of my hard drive? What's that about?
I would first backup using 'fsarchiver' then delete both partitions. Then create the new larger partition out of the unallocated space. Then using 'fsachiver' restore your system. You might need to resize using 'resize /dev/sdXX'. All of this depends if both system and swap are next to each other.

If you go with 'gparted' it can take hours to resize.

---

### Post by monkeybrain20122 on 2017-10-28
> **VMC said:**
> I would first backup using 'fsarchiver' then delete both partitions. Then create the new larger partition out of the unallocated space. Then using 'fsachiver' restore your system. You might need to resize using 'resize /dev/sdXX'. All of this depends if both system and swap are next to each other.

If you go with 'gparted' it can take hours to resize.


+ 100 to fsarchiver. :)

---

### Post by uRock on 2017-10-28
When I go for a clean install, I backup my data, then format all of the partitions while using the "Something Else" option in the installer. Since I run so many VMs and tend to fill the SSD, I will keep the swap partition just to have a protected amount of space.

---

