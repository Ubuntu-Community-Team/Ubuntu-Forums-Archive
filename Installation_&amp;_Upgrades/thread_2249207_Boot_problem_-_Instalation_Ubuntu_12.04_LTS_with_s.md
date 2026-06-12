---
title: "Boot problem - Instalation Ubuntu 12.04 LTS with software RAID1"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by Pablo_Moreno_Navar on 2014-10-20
[COLOR=#333333][FONT=Ubuntu]Hello, I installed using Alternate version of Ubuntu 12.04 LTS in order to configure my PC's with RAID1 configuration. Each computer has 2 HDD 1TB storage.

The procedure of partitioning I followed  in each HDD, (they're all formated using MBR: Master Boot Record):

Part. 1: 200 GB - Primary with Bootable flag activated. Use as: Physical volume for RAID.
Part. 2: 798 GB - Logical. Use as: Physical volume for RAID.
Part. 3: 2.2 GB - Logical. Use as: Physical volume for RAID.

I do the same in each HDD, giving the system names to partitions automatically #1, #5 and #6 respectively.

Then I choose the option Configure Software RAID and Create a MD device, I select by pairs /dev/sda1 and /dev/sdb1, /dev/sda5 and /dev/sdb5, /dev/sda6 and /dev/sdb6. Inside each RAID 1 device I give them this characteristics:

ext4, mounted in / and format for #0
ext4, moutned in /home and format for #1
swap, for #2

As you can see in: [https://www.dropbox.com/s/tm0kz1welo7c5tm/Particionado_1.jpg?dl=0](https://www.dropbox.com/s/tm0kz1welo7c5tm/Particionado_1.jpg?dl=0) (I'm so sorry as this is in Spanish)

After the instalation, there are two diferent reactions:

PC-1: Appears a black screen with the '_' cursor. Inside BIOS boot menu there are no Bootable options (UEFI Boot Sources)
PC-2: Appears a bootable option in the BIOS menu, but it gives the error "error: efidisk read error" and the goes to this Grub Screen: [https://www.dropbox.com/s/7zamh49kk5yrllv/Grub_error.jpg?dl=0](https://www.dropbox.com/s/7zamh49kk5yrllv/Grub_error.jpg?dl=0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
I don't understand what is happening in the installation process, but I did the same in a Virtual Machine and it was made instantly without an error.[/FONT][/COLOR]

---

