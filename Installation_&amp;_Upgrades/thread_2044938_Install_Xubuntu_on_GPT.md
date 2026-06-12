---
title: "Install Xubuntu on GPT"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by Vonius on 2012-08-20
Hello!

I tried install Xubuntu on notebook Asus A55V but Xubuntu's installer doesn't recognize GPT partitions.  GPARTED doen't recognize any partition.

fdisk-l gives this:

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x000230f1

Thanks in advance.

---

### Post by oldfred on 2012-08-20
I have not tried  Xubuntu, but have Ubuntu with gpt partitions since 9.10. You do have to create a bios_grub partition to get grub2 to install correctly.

fdisk does not see gpt partitions, but normally shows an error message saying gpt.

I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

Post this:
sudo parted /dev/sda unit s print

---

