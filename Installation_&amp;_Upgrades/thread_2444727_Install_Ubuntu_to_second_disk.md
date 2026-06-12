---
title: "Install Ubuntu to second disk"
date: 2020-06-03
forum: Installation &amp; Upgrades
---

### Post by bahadirgurel on 2020-06-03
Hi, I have a computer with two disks (1TB HDD and 512GB SSD). Ubuntu was installed on 1TB HDD. But I want to install on SSD and delete Ubuntu from HDD. No CD/DVD on this computer. I have an external USB HDD for Ubuntu installation (I use BalenaEtcher).

I tried to format SSD and to install Ubuntu on SSD. After the install computer does not boot from SSD. If I use fdisk -l command, I see "BIOS boot" filesystem. But in HDD, I see EFI Filesystem. How can I install Ubuntu to SSD and boot from SSD?


```
Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectorsDisk model: CAZ-82512-Q11 NVMe LITEON 512GB
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 07B651A2-4550-404A-BF24-15426414E421


Device             Start       End   Sectors Size Type
/dev/nvme0n1p1      2048      4095      2048   1M BIOS boot
/dev/nvme0n1p2      4096 104861695 104857600  50G Linux filesystem
/dev/nvme0n1p3 104861696 106958847   2097152   1G Linux filesystem
/dev/nvme0n1p4 106958848 211816447 104857600  50G Linux filesystem




Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ04ABF1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: CDD5834A-E719-437C-92F5-6BEB83DCB273


Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953521663 1952471040  931G Linux filesystem



```

---

### Post by CelticWarrior on 2020-06-03
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Please read the above in order to understand UEFI.
You can't mix modes and if you intend to keep both drives you can also keep its EFI partition and boot from there regardless of Ubuntu being installed in a different drive. But you can also change the settings to give first priority to the new SSD and then install Ubuntu, Or you can simply disconnect the HDD temporarily and install Ubuntu in the SSD. In any case you need to boot in UEFI mode; the presence of "bios_boot" means you installed Ubuntu in Legacy (BIOS") mode in a GPT drive. Your computer is set to boot UEFI installations, reason why the old and proper installation boots and the new and improper installation doesn't.

---

### Post by oldfred on 2020-06-03
How you boot install media UEFI or BIOS is then how it installs.

UEFI & BIOS are not really compatible. 
Once you start booting in one mode, you cannot switch. Or grub can only boot other installs that are in same boot mode.

---

### Post by bahadirgurel on 2020-06-03
Your answer worked very well! First I read the UEFI link. But in "creating an UEFI System Partition" section, I didn't understand the procedure (I am really new to linux world). This link ([https://youtu.be/tt5z68BEY7M](https://youtu.be/tt5z68BEY7M)) told me how to create an UEFI system partition step by step. After that I installed bootable Ubuntu on SSD. Thank you for your help.

---

