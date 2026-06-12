---
title: "Dual boot with two hard drives using bcdedit (not grub)"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by mphaua on 2010-01-31
Hi,

I have successfully installed Ubuntu 9.10 on a second hard drive (/dev/sdb). I already had Windows 7 installed on first hard drive (/dev/sda).

/dev/sdb is partioned into 3 partitions. /dev/sdb1 is formatted with ext4 and mounts /, /dev/sdb2 is swap area and /dev/sdb3 i a formatted ntfs partition for OS sharing. GRUB is installed into the MBR of /dev/sdb.

I am able to boot Ubuntu if I tell my laptop (Lenovo Thinkpad T60) to boot from my second hard drive. However, I would prefer to have my Windows boot loader (bcdedit) recongize Ubuntu so I could select Ubuntu from there. I am not able to get this to work. When I select Ubuntu on the boot manager menu I get black screen displaying GRUP in the upper left corner and a blinking cursor.

I have followed the paragraph "Configuring for Dual Boot" in [http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/) which seems to work for most people. However, it seems that most people have a single hard drive scenario and that might be my problem?

Any help would be appreciated.

---

### Post by darkod on 2010-01-31
I don't want to sound harsh but isn't this a question for a windows forum? The windows bootloader is their product.

As for your question, usually that procedure would just chainload from win7 bootloader to grub2, the similar way that grub2 boots windows (by chainloading it). I believe that procedure requires that you have grub2 installed on your ubuntu root partition (/dev/sdb1 in your case), while you have grub2 on the MBR of /dev/sdb, as per your words.

Hence the linux.bin file they are cutting out of the partition, is probably blank in your case.

---

### Post by mikemunsil on 2010-04-07
I have Win7 on one hard drive sda and Ubuntu 9.10 on the other sdb. Can I configure grub to chainload the windows drive?

---

### Post by oldfred on 2010-04-07
What version of grub. Actually grub chainloads as its standard settings. The windows boot loader in the MBR just looks for the active partition (boot flag) and chainloads to the PBR of that partition. Grub just skips the MBR and jumps (chainloads) to the windows PBR. With two drives you could chain to the other MBR but might as well chainload to the PBR.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Grub legacy sometimes had trouble finding windows, grub2 is very good at finding windows if the windows is bootable. Often moving partitions around and making changes to the system make windows want to run a repair before it boots, then grub2 does not find it.

---

