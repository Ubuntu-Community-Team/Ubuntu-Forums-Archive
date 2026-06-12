---
title: "Upgrade to kernel 5.x problem"
date: 2020-04-01
forum: Installation &amp; Upgrades
---

### Post by Goldengate01 on 2020-04-01
Hi guys, first time I've seen this, I'm trying to upgrade my kernel to a more recent version in my Ubuntu Bionic:

**Kernel**: 4.15.0-20-generic
**Command**: sudo parted -l
**Response**:
Modelo: ATA SSEA4M8240GDS (scsi)
Disco /dev/sda: 240GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: msdos
Indicadores de disco:

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  210GB  210GB   primary   ntfs
 2      210GB   239GB  29,2GB  primary   ext4
 3      239GB   240GB  1099MB  extended
 5      239GB   240GB  1099MB  logical   linux-swap(v1)

Error: /dev/mmcblk0boot0: etiqueta de disco no reconocida
Modelo: Tarjeta de almacenamiento SD/MMC genérica (sd/mmc)
Disco /dev/mmcblk0boot0: 4194kB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: unknown
Indicadores de disco:

Error: /dev/mmcblk0boot1: etiqueta de disco no reconocida
Modelo: Tarjeta de almacenamiento SD/MMC genérica (sd/mmc)
Disco /dev/mmcblk0boot1: 4194kB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: unknown
Indicadores de disco:

Modelo: MMC Biwin (sd/mmc)
Disco /dev/mmcblk0: 30,9GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: gpt
Indicadores de disco:

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre                        Banderas
 1      1049kB  106MB   105MB   fat32                EFI system partition          arranque, esp
 2      106MB   123MB   16,8MB                       Microsoft reserved partition  msftres
 3      123MB   30,1GB  30,0GB  ntfs                 Basic data partition          msftdata
 4      30,1GB  30,9GB  839MB   ntfs                 Basic data partition          oculta, diag

**Command**: blkid
**Response**:
/dev/mmcblk0p1: LABEL="SYSTEM" UUID="D05A-9ED8" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="44cbc224-6734-44e1-bfeb-cae75dd46865"
/dev/mmcblk0p3: LABEL="Windows" UUID="4A20687C206870BD" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="12653868-4e52-4710-a8a5-d371c868b3d6"
/dev/mmcblk0p4: LABEL="Recovery" UUID="64966A1B9669EE4C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a4ba2a45-e210-4323-895e-400ca5c0ed4a"
/dev/sda1: UUID="10D0FDC8D0FDB456" TYPE="ntfs" PARTUUID="1373d5a9-01"
/dev/sda2: UUID="1379020b-b071-42d7-aca7-1a78701bb326" TYPE="ext4" PARTUUID="1373d5a9-02"
/dev/sda5: UUID="e49618cf-97d3-4cde-8997-00a3e0d5af0f" TYPE="swap" PARTUUID="1373d5a9-05"
/dev/mmcblk0: PTUUID="4d32ded6-1ef7-4cae-acfa-6bfa1c7d1c5b" PTTYPE="gpt"
/dev/mmcblk0p2: PARTLABEL="Microsoft reserved partition" PARTUUID="4fa942bb-dc40-48ad-8785-9c6795678e59"

**Upgrade to kernel 5.x without any problem and update-grub runs without any problem, says: "done"**: 

(Leyendo la base de datos ... 254403 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../linux-modules-5.3.0-45-generic_5.3.0-45.37~18.04.1_amd64.deb ...
Desempaquetando linux-modules-5.3.0-45-generic (5.3.0-45.37~18.04.1) ...
Seleccionando el paquete linux-image-5.3.0-45-generic previamente no seleccionado.
Preparando para desempaquetar .../linux-image-5.3.0-45-generic_5.3.0-45.37~18.04.1_amd64.deb ...
Desempaquetando linux-image-5.3.0-45-generic (5.3.0-45.37~18.04.1) ...
Configurando linux-modules-5.3.0-45-generic (5.3.0-45.37~18.04.1) ...
Configurando linux-image-5.3.0-45-generic (5.3.0-45.37~18.04.1) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.18.0-25-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.18.0-25-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-5.3.0-45-generic
I: /initrd.img is now a symlink to boot/initrd.img-5.3.0-45-generic
Procesando disparadores para linux-image-5.3.0-45-generic (5.3.0-45.37~18.04.1) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-45-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generando un fichero de configuración de grub...
Encontrado fondo de pantalla: /etc/grub.d/backgrounds/bodhi.png
Aviso: Ya no se soporta fijar GRUB_TIMEOUT a un valor no nulo cuando GRUB_HIDDEN_TIMEOUT está fijado.
Found background image: /etc/grub.d/backgrounds/bodhi.png
Encontrada imagen de linux: /boot/vmlinuz-5.3.0-45-generic
Encontrada imagen de memoria inicial: /boot/initrd.img-5.3.0-45-generic
Encontrada imagen de linux: /boot/vmlinuz-4.18.0-25-generic
Encontrada imagen de memoria inicial: /boot/initrd.img-4.18.0-25-generic
Encontrada imagen de linux: /boot/vmlinuz-4.15.0-20-generic
Encontrada imagen de memoria inicial: /boot/initrd.img-4.15.0-20-generic
Encontrado Windows Boot Manager en /dev/mmcblk0p1@/EFI/Microsoft/Boot/bootmgfw.efi
Añadiendo menú de entrada de inicio para la configuración del firmware EFI
hecho

**Situation**: Booting into the new kernel gives error: "***Timed out waiting for device dev-disk-by\x2duuid-D05A\x2d9ed0.device***", the UEFI partition is in the missing device!, but more strange is:

fgonzalez@mbook:~$ sudo parted -l
Modelo: ATA SSEA4M8240GDS (scsi)
Disco /dev/sda: 240GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: msdos
Indicadores de disco:

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  210GB  210GB   primary   ntfs
 2      210GB   239GB  29,2GB  primary   ext4
 3      239GB   240GB  1099MB  extended
 5      239GB   240GB  1099MB  logical   linux-swap(v1)

fgonzalez@mbook:~$

Ok... I said: hummmm strange! where is "/dev/mmcblk0"? UEFI is in there so the question is: what's going on??? any clues, thoughs, suggestions, advice are very very welcome because I don't have any clue!

Regards!

Francisco

---

### Post by Goldengate01 on 2020-04-01
Ok I solved the problem!!! diggin' a little deep and checking the modules the kernel has only as dependency the package linux-modules-5.3.0-45-generic wich doesn't include the module "mmc_block.ko" for mmcblk device, thing is this module its in the package linux-modules-extra-5.3.0-45-generic and its not installed by default you've to do it manually so I installed and BAM!!! now its working as usual!

Sorry 4 bother you guys!

Regards!

Francisco

---

