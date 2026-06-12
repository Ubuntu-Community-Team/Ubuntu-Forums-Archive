---
title: "Grub Lost ubuntu 12.04 install"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by Dr Dedoverde on 2012-08-08
Hello all! 
My my problem is with the GRUB installation ubuntu 12.04 desktop.

[B]Executing 'grub-install/dev/sda1' failed. This is a fatal error

[/B]search found the following command lines, but I do not work.


```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
``````
ubuntu@ubuntu:~$ **sudo fdisk -l**
Atención: el indicador 0x0000 inválido de la tabla de particiones 5 se corregirá mediante w(rite)

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x000ede28

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1             254  1250021631   625010689    5  Extendida

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x00000000

El disco /dev/sdb no contiene una tabla de particiones válida

Disco /dev/mapper/pdc_bbhijcigfi: 640.0 GB, 640011599872 bytes
255 cabezas, 63 sectores/pista, 77810 cilindros, 1250022656 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 65536 bytes / 131072 bytes
Identificador del disco: 0x000ede28

                Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/mapper/pdc_bbhijcigfi1             254  1250021631   625010689    5  Extendida
La partición 1 no se inició en el limite físico del sector
/dev/mapper/pdc_bbhijcigfi5             256    10000127     4999936   83  Linux
/dev/mapper/pdc_bbhijcigfi6        10000384    30000127     9999872   83  Linux
/dev/mapper/pdc_bbhijcigfi7        30000384  1230000127   599999872   83  Linux
/dev/mapper/pdc_bbhijcigfi8      1230000384  1250021631    10010624   82  Linux swap / Solaris
Atención: no se tienen en cuenta los datos adicionales de la tabla de particiones 6
Atención: el indicador 0x0007 inválido de la tabla de particiones 6 se corregirá mediante w(rite)

Disco /dev/mapper/pdc_bbhijcigfi1: 640.0 GB, 640010945536 bytes
255 cabezas, 63 sectores/pista, 77810 cilindros, 1250021378 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 65536 bytes / 131072 bytes
Posición de alineamiento: 1024 bytes
Identificador del disco: 0x00000000

                  Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/mapper/pdc_bbhijcigfi1p1               2     9999873     4999936   83  Linux
/dev/mapper/pdc_bbhijcigfi1p2         9999874    29999873    10000000    5  Extendida
/dev/mapper/pdc_bbhijcigfi1p5        10000130    29999873     9999872   83  Linux
/dev/mapper/pdc_bbhijcigfi1p6      4057225475  4057230528        2527   be  arranque de Solaris
La partición 6 no se inició en el limite físico del sector

Disco /dev/mapper/pdc_bbhijcigfi5: 5119 MB, 5119934464 bytes
255 cabezas, 63 sectores/pista, 622 cilindros, 9999872 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 65536 bytes / 131072 bytes
Identificador del disco: 0x00000000

El disco /dev/mapper/pdc_bbhijcigfi5 no contiene una tabla de particiones válida

Disco /dev/mapper/pdc_bbhijcigfi6: 10.2 GB, 10239868928 bytes
255 cabezas, 63 sectores/pista, 1244 cilindros, 19999744 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 65536 bytes / 131072 bytes
Identificador del disco: 0x00000000

El disco /dev/mapper/pdc_bbhijcigfi6 no contiene una tabla de particiones válida

Disco /dev/mapper/pdc_bbhijcigfi7: 614.4 GB, 614399868928 bytes
255 cabezas, 63 sectores/pista, 74696 cilindros, 1199999744 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 65536 bytes / 131072 bytes
Identificador del disco: 0x00000000

El disco /dev/mapper/pdc_bbhijcigfi7 no contiene una tabla de particiones válida

Disco /dev/mapper/pdc_bbhijcigfi8: 10.3 GB, 10250878976 bytes
255 cabezas, 63 sectores/pista, 1246 cilindros, 20021248 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 65536 bytes / 131072 bytes
Identificador del disco: 0xf943b280

El disco /dev/mapper/pdc_bbhijcigfi8 no contiene una tabla de particiones válida
```these are my partitions
[IMG]http://img689.imageshack.us/img689/1919/capturadepantallade2012yt.png[/IMG]

please help I have been over 12 hours looking for a solution and my eyes are burning xD

---

### Post by oldfred on 2012-08-09
Welcome to the forums.

I do not know RAID and you have RAID. Did you use the standard desktop installer. It does not have the RAID drivers. You need to use the alternative installer. It is text based, but otherwise like the gui version. But without the extra gui, it has room for extra drivers like the RAID drivers you need.

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

You might be able to use boot repair to install grub but you want to install to the root of raid not the devices. Or install grub2's boot loader to /dev/mapper/pdc_bbhijcigfi with no number for partition or the root of the RAID device. The manual example your were following were for non-RAID and used the devices like /dev/sda, but yours should be /dev/mapper/pdc_bbhijcigfi.

I think this downloads the extra RAID driver and then works with the desktop liveCD to install grub2.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Update
If you have a separate /boot and using the manual commands you have to also mount it. If using Boot-Repair tick the separate /boot and tell it which partition is /boot.

---

### Post by Dr Dedoverde on 2012-08-09
hello again! 
 I ran the boot repair as you indicated and I could not fix the problem.
 I leave the bootinfo

 **[COLOR=Blue][http://paste.ubuntu.com/1137767/](http://paste.ubuntu.com/1137767/)[/COLOR]**

[**http://paste.ubuntu.com/openid/login/?next=/1137767/plain/**]("http://paste.ubuntu.com/openid/login/?next=/1137767/plain/")

I'm downloading the installation Alternatively, if the problem persists I will use it.
thanks for helpme

---

### Post by oldfred on 2012-08-09
I do not know RAID well enough to know if the reported issues are real or just that the standard partitions tools do not work with the RAID. 

It looks like while grub2's boot loader was installed, the core.img file did not get correctly installed.

---

### Post by Dr Dedoverde on 2012-08-09
Is it possible to install the core.img manually?

---

### Post by oldfred on 2012-08-09
No, not that I know of. It is customized for your install. Normally with MBR it is starts at the sector just after the MBR and with gpt you have to have another bios_grub partition to hold it. Not sure about RAID. It usually seems to put a copy into the /boot/grub folder.

---

### Post by Dr Dedoverde on 2012-08-10
has miraculously solved the problem of grub
this was what I did:
I created a new raid configuration (raid1) with the following partition configuration.

[IMG]http://desmond.imageshack.us/Himg442/scaled.php?server=442&filename=capturadepantallade2012v.png&res=landing[/IMG]
(looking at the picture I realize that I'm an unmounted partition. I promise to fix it :P)

then, when you specify the path grub boot without any problems let me choose /dev/mapper/pdc_cdgjjiaecf (298.03 GIB) as pictured.
it is clear that I'm new to ubuntu (2 days)
 bye and thanks

---

