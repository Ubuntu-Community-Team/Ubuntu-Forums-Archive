---
title: "Acer Aspire Z5600 Kernel panic"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by fballem on 2010-08-08
I have acquired a brand new Acer Aspire AZ5600 all-in-one computer. I have installed ubuntu 10.04 on the system - single boot.

When I restart, I am getting the message [0.681800] Kernel panic - not syncing: VFS : Unable to mount root fs on unknown-block(0,0)

I have wiped the disk using DiskPart from Windows. I admit that my technical knowledge at this point is very limited, so I would appreciate any suggestions that others might care to offer.

This really shouldn't be this hard!

Thanks,

---

### Post by dino99 on 2010-08-08
prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

kernel panic can happen from many reasons, but always use the distro tools to work on a specific distro (dont mix windoz tools with ubuntu tools

as your pc is a recent model you probably find some unknown issue: look at errors logged (system admin logviewer) and google around the chipset giving trouble

---

### Post by fballem on 2010-08-09
Thanks - I downloaded PartedMagic.

I am still having the exact same error message however. There seems to be a block at the start of the disk that I cannot get rid of.

When I run fdisk -l from Parted after installing ubuntu, I get the following information:

/dev/sda1 start 2048 End 1917845503 blocks 958921728 id 83 sytem Linux Boot *

/dev/sda2 start 1917847550 end 1953523711 blocks 17838081 id 5 system Extended

/dev/sda5 start 1917847552 end 1953523711 blocks 17838080 id 82 system Linux swap / Solaris

I have a feeling that I have to configure Grub - but I am not sure what values I need to put into the Root or the Setup parts

Thanks,

---

### Post by fballem on 2010-08-12
I tried installing Ubuntu 10.10 Alpha 3 using the Alternate CD. I still have the kernel panic error, but I do have a little more information to go with it:

[0.773698] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[0.774195] Pid: 1, comm: swapper Not tainted 2.6.35-14-generic #19-Ubuntu
[0.774605] Call Trace:
[0.774758] [<ffffffff81585eb8>] panic+0x90/0x111
[0.775047] [<ffffffff81af82ba>] mount_block_root+0x1ea/0x29e
[0.775396] [<ffffffff81af83c4>] mount_root+0x56/0x5a
[0.775703] [<ffffffff81af8538>] prepare_namespace+0x170/0x1a9
[0.776056] [<ffffffff81af78c9>] kernel_init+0x1ad/0x1bd
[0.776380] [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[0.776773] [<ffffffff81af771c>] ? kernel_init+0x0/0x1bd
[0.777055] [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10

I hope this helps

Thanks,

---

### Post by marapiel on 2010-08-12
Hi. I had the same problem (with the same computer). After quite a struggle here is how i fixed it :

- restart and go to the bios
- go to the menu advanced>Advanced Chipset Feature
- switch "Memory Hole Remapping" to disable

I don't know what it is, but it seemed to fix the problem.

---

### Post by fballem on 2010-08-13
Perfect - it is now working!!!!!

---

### Post by RestoredState on 2010-09-06
After searching and searching, digging, sweating, swearing, threatening to go back to windoze, installing, reinstalling, 9.10, 10.04, 10.10, with a clean install each time, and the Kernel Panic to follow - I happened upon this thread.

I'm running a Frankenstiened desktop, but the memory hole fix worked a treat for me.  Thanks a million!!!  :p

Biostar K8M800 Micro AM2
AMD Athlon64 X2 2GHz
2GB RAM
Dual Seagate 160GB HDD
ATI Radeon HD 3850 AGP

---

