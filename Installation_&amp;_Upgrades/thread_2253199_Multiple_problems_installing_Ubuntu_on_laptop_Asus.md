---
title: "Multiple problems installing Ubuntu on laptop Asus amd a10"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by karxll on 2014-11-18
Hi!

Well, after installing Ubuntu 14.10 on my laptop amd asus a10 have the following problems:


1. The touchpad doesn't work. I searched on internet, but I have not found a solution.


2. It seems that the laptop has delay or reacts seconds after the actions are not flowing.


3. The windows can't be selected with the mouse pointer. After a while, it seems that the windows were locked.


I installed Ubuntu 14.10, 14.04 and Debian testing and I have the same problems. The laptop has Windows 8.1 and it works fine.


Kindly, can u help to know what is the solution to install Ubuntu correctly?


Sorry my english. Thank u.

---

### Post by fantab on 2014-11-18
Tell us more about your machine and its hardware like, CPU RAM and Graphics.

Boot with Ubuntu DVD/USB, "Try Ubuntu"... open Terminal [ctrl+alt+T], run the following commands and post its output here:

```
sudo parted -l
```

---

### Post by karxll on 2014-11-18
Hi fantab,thanks for ur answer.

I executed the command and this is the answer. The image is an attachment.


 [ATTACH=CONFIG]258058[/ATTACH]
> 
Modelo: ATA ST1000LM024 HN-M (scsi)
Disco /dev/sda: 1000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. gpt
Disk Flags: 

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre                        Banderas
 1      1049kB  106MB   105MB   fat32                EFI system partition          arranque, esp
 2      106MB   1050MB  944MB   ntfs                 Basic data partition          oculta, diag
 3      1050MB  1184MB  134MB                        Microsoft reserved partition  msftres
 4      1184MB  401GB   400GB   ntfs                 Basic data partition          msftdata
 5      401GB   601GB   200GB   ext4
 7      601GB   603GB   2048MB  linux-swap(v1)
 6      979GB   1000GB  21,5GB  ntfs                 Basic data partition          oculta, diag


Aviso: No se puede abrir /dev/sr0 en modo lectura-escritura (Sistema de archivos
de solo lectura). /dev/sr0 ha sido abierto en modo de sólo lectura.
Error: /dev/sr0: etiqueta de disco no reconocida
Modelo: MATSHITA DVD-RAM UJ8E2 S (scsi)                                   
Disco /dev/sr0: 4533MB
Tamaño de sector (lógico/físico): 2048B/2048B
Tabla de particiones. unknown
Disk Flags:



Thanks again.

---

### Post by karxll on 2014-11-18
About my laptop:

Asus K550D
CPU: Amd A10-5750M 2.5 GHz Elite Quad Core
Graphics: Radeon HD 8670M 2GB
RAM: 8Gb
HDD: 1 Tb

Thank u.

---

### Post by karxll on 2014-11-18
Hi!


I downloaded the ubuntu iso and tried to install ubuntu 14.10 again on my laptop but didn't work. I have the same issues. Then, i tried to install Debian testing again but in the main screen to select language, the touchpad panel not working and  the "clicks" wasn't in the correct positions. Really, i haven't idea what are the problems.


I have read about amd in Ubuntu and have seen multiple problems without solutions. 


What do u think about it?

Thank u.

---

