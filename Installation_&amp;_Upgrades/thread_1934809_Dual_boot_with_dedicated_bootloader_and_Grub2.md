---
title: "Dual boot with dedicated bootloader and Grub2"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by sselt on 2012-03-02
Is all current ubuntu installs using grub2?

I will be installing ubuntu on a dual boot system that already has a dedicated boot loader in the MBR, and the linux system on there had legacy grub installed on the linux boot partition.

I would like to keep using the current boot loader as long as grub2 can be installed in the linux boot partition and not in the MBR. Is this possible for grub2?


I know some people will not understand, and ask why not use grub2 in the master boot record to boot everything. It is a preference.

---

### Post by MAFoElffen on 2012-03-03
> **sselt said:**
> Is all current ubuntu installs using grub2?

I will be installing ubuntu on a dual boot system that already has a dedicated boot loader in the MBR, and the linux system on there had legacy grub installed on the linux boot partition.

I would like to keep using the current boot loader as long as grub2 can be installed in the linux boot partition and not in the MBR. Is this possible for grub2?


I know some people will not understand, and ask why not use grub2 in the master boot record to boot everything. It is a preference.
When it comes to the end, it will popup a dialog box asking if you want to install Grub2... Select no, meaning do not install.

Then set it up in Grub, Lilo, whatever.  

I have multi-boots. I know how to do it from Grub and Lilo. I prefer Grub2.

---

### Post by ottosykora on 2012-03-03
I tried few times the same, as I have different boo tmanagers on different systems.

I tried first to make normal install and put the grub2 to the pbr, that means completely to the partition of the linux.

However I noticed each time I did so, a warning from the grub installer itself, that I should not do this.

I did it anyway with grub2 and realized, that the warning was right. Updates and particularly distribution upgrades did regularly destroy the grub2 in this position.

From then, I install grub legacy in the pbr if needed, with normal ubuntu install I often install the grub2 first as it is default check if all works and then go and purge the grub2 and install grub legacy to the pbr in question.
This works then very stable and I had so far no issues with it.

there is a guide for that:
[http://ubuntuforums.org/showthread.php?t=1298932&highlight=replace+grub2+grub+legacy](http://ubuntuforums.org/showthread.php?t=1298932&highlight=replace+grub2+grub+legacy)

---

