---
title: "2 TB Storage with host bus error"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by support4 on 2014-01-02
Hey Guys,

hope you all have had a good start @ 2014.

Short prehistory. In my Home Server
```
Linux MyComputeName 3.8.0-34-generic #49-Ubuntu SMP Tue Nov 12 18:00:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
```
I have 2 drives atm. 1TB Seageate and 750GB WDC. Both are S-ATA drives and are connected via S-ATA to the Mainboard. In this constellation everything works fine.
Mainboard is => [ASUS P5G41T-M]("http://www.asus.com/Motherboards/P5G41TM_LE/")
CPU
```
processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5800  @ 3.20GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 2003.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 6402.32
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```
RamSize: 8GB
I wanted to make my home server a small gift, a 2TB hard drive from [Toshiba]("http://storage.toshiba.eu/cms/de/hdd/computing/product_detail.jsp?productid=447")[ DT01ACA200]("http://storage.toshiba.eu/cms/de/hdd/computing/product_detail.jsp?productid=447")
I dont want to make this drive as additional drive but as boot drive (New Server Setup)

But during install and also when new installation is started, Im getting alot of error messages like this:
```
Jan  2 12:11:34 MyComputeName kernel: [  398.336865] ata4.01: configured for UDMA/133
Jan  2 12:11:34 MyComputeName kernel: [  398.336912] ata4: EH complete
Jan  2 12:11:37 MyComputeName kernel: [  401.231967] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:11:37 MyComputeName kernel: [  401.231972] ata4.00: BMDMA stat 0x66
Jan  2 12:11:37 MyComputeName kernel: [  401.231975] ata4.00: failed command: WRITE DMA EXT
```

sudo parted -l gives this result
```

Modell: ATA ST31000528AS (scsi)
Festplatte  /dev/sda:  1000GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      32,3kB  1000GB  1000GB  primary


Modell: ATA TOSHIBA DT01ACA200 (scsi)
Festplatte  /dev/sdb:  2000GB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ       Dateisystem  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   2000GB  2000GB  extended
 5      257MB   2000GB  2000GB  logical


Modell: ATA WDC WD7500AARS-0 (scsi)
Festplatte  /dev/sdc:  750GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende   Größe  Typ       Dateisystem  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   750GB  750GB  extended
 5      257MB   750GB  750GB  logical


Modell: Linux-Device-Mapper (linear) (dm)
Festplatte  /dev/mapper/mint--vg-swap_1:  8552MB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: loop

Nummer  Anfang  Ende    Größe   Dateisystem     Flags
 1      0,00B   8552MB  8552MB  linux-swap(v1)


Modell: Linux-Device-Mapper (linear) (dm)
Festplatte  /dev/mapper/mint--vg-root:  1991GB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: loop

Nummer  Anfang  Ende    Größe   Dateisystem  Flags
 1      0,00B   1991GB  1991GB  ext4


Fehler: /dev/mapper/luks-91b2fd1e-15a8-4515-8f10-1a34ba1d7ced: unbekannte 
Partitionstabelle

Modell: Linux-Device-Mapper (crypt) (dm)
Festplatte  /dev/mapper/luks-f86e0bd7-ed2b-4499-a97f-1cc024eb65d6:  1000GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop

Nummer  Anfang  Ende    Größe   Dateisystem  Flags
 1      0,00B   1000GB  1000GB  ext4


Modell: Linux-Device-Mapper (linear) (dm)
Festplatte  /dev/mapper/MyComputeName--vg-root:  741GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop

Nummer  Anfang  Ende   Größe  Dateisystem  Flags
 1      0,00B   741GB  741GB  ext4


Modell: Linux-Device-Mapper (linear) (dm)
Festplatte  /dev/mapper/MyComputeName--vg-swap_1:  8556MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop

Nummer  Anfang  Ende    Größe   Dateisystem     Flags
 1      0,00B   8556MB  8556MB  linux-swap(v1)


Fehler: /dev/mapper/sda5_crypt: unbekannte Partitionstabelle 
```

sudo lsblk -o NAME,UUID,FSTYPE,SIZE,LABEL,MOUNTPOINT says;
```

NAME                                                 UUID                                   FSTYPE       SIZE LABEL MOUNTPOINT
sda                                                                                                    931,5G       
&#9492;&#9472;sda1                                               f86e0bd7-ed2b-4499-a97f-1cc024eb65d6   crypto_LUK 931,5G       
  &#9492;&#9472;luks-f86e0bd7-ed2b-4499-a97f-1cc024eb65d6 (dm-3) 0b2ab832-b3d8-4f10-8480-ba22376b9c8f   ext4       931,5G TB    /media/com
sdb                                                                                                      1,8T       
&#9500;&#9472;sdb1                                               7f9f0e97-9c03-4e03-9e17-83fac4cf358c   ext2         243M       
&#9500;&#9472;sdb2                                                                                                     1K       
&#9492;&#9472;sdb5                                               91b2fd1e-15a8-4515-8f10-1a34ba1d7ced   crypto_LUK   1,8T       
  &#9492;&#9472;luks-91b2fd1e-15a8-4515-8f10-1a34ba1d7ced (dm-4) on7JJF-vjkd-xmEo-6IBQ-j0kT-p1Hc-Z8dKLR LVM2_membe   1,8T       
    &#9500;&#9472;mint--vg-root (dm-5)                           e6494041-9c4f-44c2-a087-de63884e8f5a   ext4         1,8T       /media/com
    &#9492;&#9472;mint--vg-swap_1 (dm-6)                         88f078e0-4c2a-4a17-beb8-303755a912f5   swap           8G       
sdc                                                                                                    698,7G       
&#9500;&#9472;sdc1                                               d07638af-c089-4a1e-9d96-bc27108ecd34   ext2         243M       /boot
&#9500;&#9472;sdc2                                                                                                     1K       
&#9492;&#9472;sdc5                                               fa0cfc6c-e930-4612-900a-0b4d09de0724   crypto_LUK 698,4G       
  &#9492;&#9472;sda5_crypt (dm-0)                                xtAE7w-q0Eq-frMV-X895-BWqS-oyt9-ms5dGE LVM2_membe 698,4G       
    &#9500;&#9472;MyComputeName--vg-root (dm-1)                   e4ad25f4-2829-4e8b-82fc-4ed74621b535   ext4       690,4G       /
    &#9492;&#9472;MyComputeName--vg-swap_1 (dm-2)                 283cb32c-bbd4-4117-b742-87012a82d6e8   swap           8G       [SWAP]
```

and 
und cat /var/log/syslog:
```

Jan  2 12:11:34 MyComputeName kernel: [  398.336865] ata4.01: configured for UDMA/133
Jan  2 12:11:34 MyComputeName kernel: [  398.336912] ata4: EH complete
Jan  2 12:11:37 MyComputeName kernel: [  401.231967] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:11:37 MyComputeName kernel: [  401.231972] ata4.00: BMDMA stat 0x66
Jan  2 12:11:37 MyComputeName kernel: [  401.231975] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:11:37 MyComputeName kernel: [  401.231978] ata4.00: cmd 35/00:00:00:85:c8/00:04:1e:00:00/e0 tag 0 dma 524288 out
Jan  2 12:11:37 MyComputeName kernel: [  401.231978]          res 51/84:a0:60:88:c8/84:00:1e:00:00/0e Emask 0x30 (host bus error)
Jan  2 12:11:37 MyComputeName kernel: [  401.231980] ata4.00: status: { DRDY ERR }
Jan  2 12:11:37 MyComputeName kernel: [  401.231982] ata4.00: error: { ICRC ABRT }
Jan  2 12:11:37 MyComputeName kernel: [  401.231989] ata4: soft resetting link
Jan  2 12:11:37 MyComputeName kernel: [  401.420333] ata4.00: configured for UDMA/33
Jan  2 12:11:37 MyComputeName kernel: [  401.436343] ata4.01: configured for UDMA/133
Jan  2 12:11:37 MyComputeName kernel: [  401.436396] ata4: EH complete
Jan  2 12:11:39 MyComputeName kernel: [  403.560391] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:11:39 MyComputeName kernel: [  403.560399] ata4.00: BMDMA stat 0x66
Jan  2 12:11:39 MyComputeName kernel: [  403.560405] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:11:39 MyComputeName kernel: [  403.560414] ata4.00: cmd 35/00:00:00:0d:08/00:04:1f:00:00/e0 tag 0 dma 524288 out
Jan  2 12:11:39 MyComputeName kernel: [  403.560414]          res 51/84:d0:30:0e:08/84:02:1f:00:00/0f Emask 0x30 (host bus error)
Jan  2 12:11:39 MyComputeName kernel: [  403.560419] ata4.00: status: { DRDY ERR }
Jan  2 12:11:39 MyComputeName kernel: [  403.560423] ata4.00: error: { ICRC ABRT }
Jan  2 12:11:39 MyComputeName kernel: [  403.560435] ata4: soft resetting link
Jan  2 12:11:39 MyComputeName kernel: [  403.748317] ata4.00: configured for UDMA/33
Jan  2 12:11:39 MyComputeName kernel: [  403.756504] ata4.01: configured for UDMA/133
Jan  2 12:11:39 MyComputeName kernel: [  403.756554] ata4: EH complete
Jan  2 12:11:40 MyComputeName kernel: [  405.082323] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:11:40 MyComputeName kernel: [  405.082331] ata4.00: BMDMA stat 0x66
Jan  2 12:11:40 MyComputeName kernel: [  405.082337] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:11:40 MyComputeName kernel: [  405.082347] ata4.00: cmd 35/00:00:00:5d:08/00:04:1f:00:00/e0 tag 0 dma 524288 out
Jan  2 12:11:40 MyComputeName kernel: [  405.082347]          res 51/84:90:70:60:08/84:00:1f:00:00/0f Emask 0x30 (host bus error)
Jan  2 12:11:40 MyComputeName kernel: [  405.082352] ata4.00: status: { DRDY ERR }
Jan  2 12:11:40 MyComputeName kernel: [  405.082355] ata4.00: error: { ICRC ABRT }
Jan  2 12:11:40 MyComputeName kernel: [  405.082368] ata4: soft resetting link
Jan  2 12:11:41 MyComputeName kernel: [  405.268362] ata4.00: configured for UDMA/33
Jan  2 12:11:41 MyComputeName kernel: [  405.277190] ata4.01: configured for UDMA/133
Jan  2 12:11:41 MyComputeName kernel: [  405.277249] ata4: EH complete
Jan  2 12:11:52 MyComputeName kernel: [  416.599335] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:11:52 MyComputeName kernel: [  416.599344] ata4.00: BMDMA stat 0x66
Jan  2 12:11:52 MyComputeName kernel: [  416.599350] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:11:52 MyComputeName kernel: [  416.599359] ata4.00: cmd 35/00:00:00:05:c8/00:04:1f:00:00/e0 tag 0 dma 524288 out
Jan  2 12:11:52 MyComputeName kernel: [  416.599359]          res 51/84:30:d0:07:c8/84:01:1f:00:00/0f Emask 0x30 (host bus error)
Jan  2 12:11:52 MyComputeName kernel: [  416.599365] ata4.00: status: { DRDY ERR }
Jan  2 12:11:52 MyComputeName kernel: [  416.599368] ata4.00: error: { ICRC ABRT }
Jan  2 12:11:52 MyComputeName kernel: [  416.599381] ata4: soft resetting link
Jan  2 12:11:52 MyComputeName kernel: [  416.784319] ata4.00: configured for UDMA/33
Jan  2 12:11:52 MyComputeName kernel: [  416.800717] ata4.01: configured for UDMA/133
Jan  2 12:11:52 MyComputeName kernel: [  416.800762] ata4: EH complete
Jan  2 12:12:03 MyComputeName kernel: [  427.608665] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:03 MyComputeName kernel: [  427.608671] ata4.00: BMDMA stat 0x66
Jan  2 12:12:03 MyComputeName kernel: [  427.608674] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:03 MyComputeName kernel: [  427.608677] ata4.00: cmd 35/00:00:00:95:48/00:04:20:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:03 MyComputeName kernel: [  427.608677]          res 51/84:40:c0:95:48/84:03:20:00:00/00 Emask 0x30 (host bus error)
Jan  2 12:12:03 MyComputeName kernel: [  427.608679] ata4.00: status: { DRDY ERR }
Jan  2 12:12:03 MyComputeName kernel: [  427.608681] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:03 MyComputeName kernel: [  427.608689] ata4: soft resetting link
Jan  2 12:12:03 MyComputeName kernel: [  428.092315] ata4.00: configured for UDMA/33
Jan  2 12:12:03 MyComputeName kernel: [  428.109170] ata4.01: configured for UDMA/133
Jan  2 12:12:03 MyComputeName kernel: [  428.109217] ata4: EH complete
Jan  2 12:12:08 MyComputeName kernel: [  432.880640] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:08 MyComputeName kernel: [  432.880648] ata4.00: BMDMA stat 0x66
Jan  2 12:12:08 MyComputeName kernel: [  432.880654] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:08 MyComputeName kernel: [  432.880664] ata4.00: cmd 35/00:00:00:bd:88/00:04:20:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:08 MyComputeName kernel: [  432.880664]          res 51/84:b0:50:bf:88/84:01:20:00:00/00 Emask 0x30 (host bus error)
Jan  2 12:12:08 MyComputeName kernel: [  432.880669] ata4.00: status: { DRDY ERR }
Jan  2 12:12:08 MyComputeName kernel: [  432.880672] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:08 MyComputeName kernel: [  432.880686] ata4: soft resetting link
Jan  2 12:12:08 MyComputeName kernel: [  433.068465] ata4.00: configured for UDMA/33
Jan  2 12:12:08 MyComputeName kernel: [  433.076582] ata4.01: configured for UDMA/133
Jan  2 12:12:08 MyComputeName kernel: [  433.076641] ata4: EH complete
Jan  2 12:12:09 MyComputeName kernel: [  433.846631] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:09 MyComputeName kernel: [  433.846636] ata4.00: BMDMA stat 0x66
Jan  2 12:12:09 MyComputeName kernel: [  433.846639] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:09 MyComputeName kernel: [  433.846643] ata4.00: cmd 35/00:00:00:e1:c7/00:04:20:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:09 MyComputeName kernel: [  433.846643]          res 51/84:50:b0:e2:c7/84:02:20:00:00/00 Emask 0x30 (host bus error)
Jan  2 12:12:09 MyComputeName kernel: [  433.846645] ata4.00: status: { DRDY ERR }
Jan  2 12:12:09 MyComputeName kernel: [  433.846646] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:09 MyComputeName kernel: [  433.846655] ata4: soft resetting link
Jan  2 12:12:09 MyComputeName kernel: [  434.032327] ata4.00: configured for UDMA/33
Jan  2 12:12:09 MyComputeName kernel: [  434.049022] ata4.01: configured for UDMA/133
Jan  2 12:12:09 MyComputeName kernel: [  434.049084] ata4: EH complete
Jan  2 12:12:14 MyComputeName kernel: [  438.280181] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:14 MyComputeName kernel: [  438.280189] ata4.00: BMDMA stat 0x66
Jan  2 12:12:14 MyComputeName kernel: [  438.280194] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:14 MyComputeName kernel: [  438.280204] ata4.00: cmd 35/00:00:00:ed:07/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:14 MyComputeName kernel: [  438.280204]          res 51/84:10:f0:ef:07/84:01:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:14 MyComputeName kernel: [  438.280209] ata4.00: status: { DRDY ERR }
Jan  2 12:12:14 MyComputeName kernel: [  438.280213] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:14 MyComputeName kernel: [  438.280225] ata4: soft resetting link
Jan  2 12:12:14 MyComputeName kernel: [  438.540351] ata4.00: configured for UDMA/33
Jan  2 12:12:14 MyComputeName kernel: [  438.557190] ata4.01: configured for UDMA/133
Jan  2 12:12:14 MyComputeName kernel: [  438.557240] ata4: EH complete
Jan  2 12:12:15 MyComputeName kernel: [  439.330907] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:15 MyComputeName kernel: [  439.330915] ata4.00: BMDMA stat 0x66
Jan  2 12:12:15 MyComputeName kernel: [  439.330921] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:15 MyComputeName kernel: [  439.330931] ata4.00: cmd 35/00:00:00:11:08/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:15 MyComputeName kernel: [  439.330931]          res 51/84:f0:10:11:08/84:03:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:15 MyComputeName kernel: [  439.330936] ata4.00: status: { DRDY ERR }
Jan  2 12:12:15 MyComputeName kernel: [  439.330940] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:15 MyComputeName kernel: [  439.330953] ata4: soft resetting link
Jan  2 12:12:15 MyComputeName kernel: [  439.516348] ata4.00: configured for UDMA/33
Jan  2 12:12:15 MyComputeName kernel: [  439.524633] ata4.01: configured for UDMA/133
Jan  2 12:12:15 MyComputeName kernel: [  439.524695] ata4: EH complete
Jan  2 12:12:20 MyComputeName kernel: [  444.802206] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:20 MyComputeName kernel: [  444.802214] ata4.00: BMDMA stat 0x66
Jan  2 12:12:20 MyComputeName kernel: [  444.802220] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:20 MyComputeName kernel: [  444.802230] ata4.00: cmd 35/00:00:00:59:48/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:20 MyComputeName kernel: [  444.802230]          res 51/84:a0:60:5a:48/84:02:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:20 MyComputeName kernel: [  444.802235] ata4.00: status: { DRDY ERR }
Jan  2 12:12:20 MyComputeName kernel: [  444.802239] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:20 MyComputeName kernel: [  444.802251] ata4: soft resetting link
Jan  2 12:12:20 MyComputeName kernel: [  444.988338] ata4.00: configured for UDMA/33
Jan  2 12:12:20 MyComputeName kernel: [  445.005283] ata4.01: configured for UDMA/133
Jan  2 12:12:20 MyComputeName kernel: [  445.005340] ata4: EH complete
Jan  2 12:12:22 MyComputeName kernel: [  446.577609] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:22 MyComputeName kernel: [  446.577615] ata4.00: BMDMA stat 0x66
Jan  2 12:12:22 MyComputeName kernel: [  446.577618] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:22 MyComputeName kernel: [  446.577621] ata4.00: cmd 35/00:00:00:b5:48/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:22 MyComputeName kernel: [  446.577621]          res 51/84:90:70:b6:48/84:02:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:22 MyComputeName kernel: [  446.577623] ata4.00: status: { DRDY ERR }
Jan  2 12:12:22 MyComputeName kernel: [  446.577625] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:22 MyComputeName kernel: [  446.577633] ata4: soft resetting link
Jan  2 12:12:22 MyComputeName kernel: [  446.764366] ata4.00: configured for UDMA/33
Jan  2 12:12:22 MyComputeName kernel: [  446.773149] ata4.01: configured for UDMA/133
Jan  2 12:12:22 MyComputeName kernel: [  446.773213] ata4: EH complete
Jan  2 12:12:24 MyComputeName kernel: [  448.357909] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:24 MyComputeName kernel: [  448.357915] ata4.00: BMDMA stat 0x66
Jan  2 12:12:24 MyComputeName kernel: [  448.357918] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:24 MyComputeName kernel: [  448.357922] ata4.00: cmd 35/00:00:00:15:88/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:24 MyComputeName kernel: [  448.357922]          res 51/84:c0:40:18:88/84:00:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:24 MyComputeName kernel: [  448.357924] ata4.00: status: { DRDY ERR }
Jan  2 12:12:24 MyComputeName kernel: [  448.357925] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:24 MyComputeName kernel: [  448.357933] ata4: soft resetting link
Jan  2 12:12:24 MyComputeName kernel: [  448.544351] ata4.00: configured for UDMA/33
Jan  2 12:12:24 MyComputeName kernel: [  448.560956] ata4.01: configured for UDMA/133
Jan  2 12:12:24 MyComputeName kernel: [  448.560997] ata4: EH complete
Jan  2 12:12:27 MyComputeName kernel: [  451.449519] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:27 MyComputeName kernel: [  451.449528] ata4.00: BMDMA stat 0x66
Jan  2 12:12:27 MyComputeName kernel: [  451.449534] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:27 MyComputeName kernel: [  451.449544] ata4.00: cmd 35/00:00:00:c5:c7/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:27 MyComputeName kernel: [  451.449544]          res 51/84:30:d0:c8:c7/84:00:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:27 MyComputeName kernel: [  451.449549] ata4.00: status: { DRDY ERR }
Jan  2 12:12:27 MyComputeName kernel: [  451.449552] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:27 MyComputeName kernel: [  451.449565] ata4: soft resetting link
Jan  2 12:12:27 MyComputeName kernel: [  451.636356] ata4.00: configured for UDMA/33
Jan  2 12:12:27 MyComputeName kernel: [  451.644467] ata4.01: configured for UDMA/133
Jan  2 12:12:27 MyComputeName kernel: [  451.644531] ata4: EH complete
Jan  2 12:12:27 MyComputeName kernel: [  451.911731] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:27 MyComputeName kernel: [  451.911736] ata4.00: BMDMA stat 0x66
Jan  2 12:12:27 MyComputeName kernel: [  451.911739] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:27 MyComputeName kernel: [  451.911742] ata4.00: cmd 35/00:00:00:d9:c7/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:27 MyComputeName kernel: [  451.911742]          res 51/84:c0:40:dc:c7/84:00:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:27 MyComputeName kernel: [  451.911744] ata4.00: status: { DRDY ERR }
Jan  2 12:12:27 MyComputeName kernel: [  451.911746] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:27 MyComputeName kernel: [  451.911754] ata4: soft resetting link
Jan  2 12:12:27 MyComputeName kernel: [  452.096331] ata4.00: configured for UDMA/33
Jan  2 12:12:27 MyComputeName kernel: [  452.104697] ata4.01: configured for UDMA/133
Jan  2 12:12:27 MyComputeName kernel: [  452.104760] ata4: EH complete
Jan  2 12:12:30 MyComputeName kernel: [  454.474254] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:30 MyComputeName kernel: [  454.474263] ata4.00: BMDMA stat 0x66
Jan  2 12:12:30 MyComputeName kernel: [  454.474268] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:30 MyComputeName kernel: [  454.474278] ata4.00: cmd 35/00:00:00:6d:c8/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:30 MyComputeName kernel: [  454.474278]          res 51/84:30:d0:6d:c8/84:03:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:30 MyComputeName kernel: [  454.474283] ata4.00: status: { DRDY ERR }
Jan  2 12:12:30 MyComputeName kernel: [  454.474286] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:30 MyComputeName kernel: [  454.474298] ata4: soft resetting link
Jan  2 12:12:30 MyComputeName kernel: [  454.660339] ata4.00: configured for UDMA/33
Jan  2 12:12:30 MyComputeName kernel: [  454.676924] ata4.01: configured for UDMA/133
Jan  2 12:12:30 MyComputeName kernel: [  454.676983] ata4: EH complete
Jan  2 12:12:31 MyComputeName kernel: [  455.200886] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:31 MyComputeName kernel: [  455.200891] ata4.00: BMDMA stat 0x66
Jan  2 12:12:31 MyComputeName kernel: [  455.200894] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:31 MyComputeName kernel: [  455.200898] ata4.00: cmd 35/00:00:00:89:c8/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:31 MyComputeName kernel: [  455.200898]          res 51/84:00:00:8a:c8/84:03:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:31 MyComputeName kernel: [  455.200900] ata4.00: status: { DRDY ERR }
Jan  2 12:12:31 MyComputeName kernel: [  455.200901] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:31 MyComputeName kernel: [  455.200909] ata4: soft resetting link
Jan  2 12:12:31 MyComputeName kernel: [  455.388340] ata4.00: configured for UDMA/33
Jan  2 12:12:31 MyComputeName kernel: [  455.405273] ata4.01: configured for UDMA/133
Jan  2 12:12:31 MyComputeName kernel: [  455.405312] ata4: EH complete
Jan  2 12:12:31 MyComputeName kernel: [  455.924028] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:31 MyComputeName kernel: [  455.924037] ata4.00: BMDMA stat 0x66
Jan  2 12:12:31 MyComputeName kernel: [  455.924042] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:31 MyComputeName kernel: [  455.924052] ata4.00: cmd 35/00:00:00:a1:c8/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:31 MyComputeName kernel: [  455.924052]          res 51/84:60:a0:a3:c8/84:01:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:31 MyComputeName kernel: [  455.924057] ata4.00: status: { DRDY ERR }
Jan  2 12:12:31 MyComputeName kernel: [  455.924061] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:31 MyComputeName kernel: [  455.924073] ata4: soft resetting link
Jan  2 12:12:31 MyComputeName kernel: [  456.112340] ata4.00: configured for UDMA/33
Jan  2 12:12:31 MyComputeName kernel: [  456.128594] ata4.01: configured for UDMA/133
Jan  2 12:12:31 MyComputeName kernel: [  456.128655] ata4: EH complete
Jan  2 12:12:32 MyComputeName kernel: [  456.137407] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:32 MyComputeName kernel: [  456.137414] ata4.00: BMDMA stat 0x66
Jan  2 12:12:32 MyComputeName kernel: [  456.137420] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:32 MyComputeName kernel: [  456.137429] ata4.00: cmd 35/00:00:00:a5:c8/00:04:21:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:32 MyComputeName kernel: [  456.137429]          res 51/84:01:ff:a8:c8/84:00:21:00:00/01 Emask 0x30 (host bus error)
Jan  2 12:12:32 MyComputeName kernel: [  456.137434] ata4.00: status: { DRDY ERR }
Jan  2 12:12:32 MyComputeName kernel: [  456.137438] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:32 MyComputeName kernel: [  456.137450] ata4: soft resetting link
Jan  2 12:12:32 MyComputeName kernel: [  456.324332] ata4.00: configured for UDMA/33
Jan  2 12:12:32 MyComputeName kernel: [  456.332714] ata4.01: configured for UDMA/133
Jan  2 12:12:32 MyComputeName kernel: [  456.332760] ata4: EH complete
Jan  2 12:12:32 MyComputeName kernel: [  456.867694] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:32 MyComputeName kernel: [  456.867703] ata4.00: BMDMA stat 0x66
Jan  2 12:12:32 MyComputeName kernel: [  456.867708] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:32 MyComputeName kernel: [  456.867718] ata4.00: cmd 35/00:00:00:c9:07/00:04:22:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:32 MyComputeName kernel: [  456.867718]          res 51/84:80:80:c9:07/84:03:22:00:00/02 Emask 0x30 (host bus error)
Jan  2 12:12:32 MyComputeName kernel: [  456.867723] ata4.00: status: { DRDY ERR }
Jan  2 12:12:32 MyComputeName kernel: [  456.867727] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:32 MyComputeName kernel: [  456.867739] ata4: soft resetting link
Jan  2 12:12:32 MyComputeName kernel: [  457.052342] ata4.00: configured for UDMA/33
Jan  2 12:12:32 MyComputeName kernel: [  457.069080] ata4.01: configured for UDMA/133
Jan  2 12:12:32 MyComputeName kernel: [  457.069125] ata4: EH complete
Jan  2 12:12:36 MyComputeName kernel: [  460.504360] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:36 MyComputeName kernel: [  460.504369] ata4.00: BMDMA stat 0x66
Jan  2 12:12:36 MyComputeName kernel: [  460.504375] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:36 MyComputeName kernel: [  460.504384] ata4.00: cmd 35/00:00:00:9d:08/00:04:22:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:36 MyComputeName kernel: [  460.504384]          res 51/84:70:90:a0:08/84:00:22:00:00/02 Emask 0x30 (host bus error)
Jan  2 12:12:36 MyComputeName kernel: [  460.504389] ata4.00: status: { DRDY ERR }
Jan  2 12:12:36 MyComputeName kernel: [  460.504393] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:36 MyComputeName kernel: [  460.504405] ata4: soft resetting link
Jan  2 12:12:36 MyComputeName kernel: [  460.692335] ata4.00: configured for UDMA/33
Jan  2 12:12:36 MyComputeName kernel: [  460.708821] ata4.01: configured for UDMA/133
Jan  2 12:12:36 MyComputeName kernel: [  460.708871] ata4: EH complete
Jan  2 12:12:37 MyComputeName kernel: [  461.765869] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:37 MyComputeName kernel: [  461.765878] ata4.00: BMDMA stat 0x66
Jan  2 12:12:37 MyComputeName kernel: [  461.765884] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:37 MyComputeName kernel: [  461.765894] ata4.00: cmd 35/00:00:00:d9:47/00:04:22:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:37 MyComputeName kernel: [  461.765894]          res 51/84:20:e0:dc:47/84:00:22:00:00/02 Emask 0x30 (host bus error)
Jan  2 12:12:37 MyComputeName kernel: [  461.765899] ata4.00: status: { DRDY ERR }
Jan  2 12:12:37 MyComputeName kernel: [  461.765902] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:37 MyComputeName kernel: [  461.765915] ata4: soft resetting link
Jan  2 12:12:37 MyComputeName kernel: [  461.952324] ata4.00: configured for UDMA/33
Jan  2 12:12:37 MyComputeName kernel: [  461.968420] ata4.01: configured for UDMA/133
Jan  2 12:12:37 MyComputeName kernel: [  461.968461] ata4: EH complete
Jan  2 12:12:42 MyComputeName kernel: [  466.717193] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:42 MyComputeName kernel: [  466.717198] ata4.00: BMDMA stat 0x66
Jan  2 12:12:42 MyComputeName kernel: [  466.717201] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:42 MyComputeName kernel: [  466.717205] ata4.00: cmd 35/00:00:00:fd:87/00:04:22:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:42 MyComputeName kernel: [  466.717205]          res 51/84:90:70:00:88/84:00:22:00:00/02 Emask 0x30 (host bus error)
Jan  2 12:12:42 MyComputeName kernel: [  466.717207] ata4.00: status: { DRDY ERR }
Jan  2 12:12:42 MyComputeName kernel: [  466.717209] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:42 MyComputeName kernel: [  466.717217] ata4: soft resetting link
Jan  2 12:12:42 MyComputeName kernel: [  466.904322] ata4.00: configured for UDMA/33
Jan  2 12:12:42 MyComputeName kernel: [  466.920795] ata4.01: configured for UDMA/133
Jan  2 12:12:42 MyComputeName kernel: [  466.920843] ata4: EH complete
Jan  2 12:12:43 MyComputeName kernel: [  467.712003] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:43 MyComputeName kernel: [  467.712032] ata4.00: BMDMA stat 0x66
Jan  2 12:12:43 MyComputeName kernel: [  467.712038] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:43 MyComputeName kernel: [  467.712048] ata4.00: cmd 35/00:00:00:29:88/00:04:22:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:43 MyComputeName kernel: [  467.712048]          res 51/84:91:6f:2b:88/84:01:22:00:00/02 Emask 0x30 (host bus error)
Jan  2 12:12:43 MyComputeName kernel: [  467.712053] ata4.00: status: { DRDY ERR }
Jan  2 12:12:43 MyComputeName kernel: [  467.712057] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:43 MyComputeName kernel: [  467.712071] ata4: soft resetting link
Jan  2 12:12:43 MyComputeName kernel: [  467.900330] ata4.00: configured for UDMA/33
Jan  2 12:12:43 MyComputeName kernel: [  467.917298] ata4.01: configured for UDMA/133
Jan  2 12:12:43 MyComputeName kernel: [  467.917362] ata4: EH complete
Jan  2 12:12:52 MyComputeName kernel: [  476.334723] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:52 MyComputeName kernel: [  476.334730] ata4.00: BMDMA stat 0x66
Jan  2 12:12:52 MyComputeName kernel: [  476.334736] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:52 MyComputeName kernel: [  476.334746] ata4.00: cmd 35/00:00:00:21:08/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:52 MyComputeName kernel: [  476.334746]          res 51/84:d0:30:21:08/84:03:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:12:52 MyComputeName kernel: [  476.334751] ata4.00: status: { DRDY ERR }
Jan  2 12:12:52 MyComputeName kernel: [  476.334754] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:52 MyComputeName kernel: [  476.334767] ata4: soft resetting link
Jan  2 12:12:52 MyComputeName kernel: [  476.520357] ata4.00: configured for UDMA/33
Jan  2 12:12:52 MyComputeName kernel: [  476.536437] ata4.01: configured for UDMA/133
Jan  2 12:12:52 MyComputeName kernel: [  476.536500] ata4: EH complete
Jan  2 12:12:56 MyComputeName kernel: [  480.208624] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:56 MyComputeName kernel: [  480.208629] ata4.00: BMDMA stat 0x66
Jan  2 12:12:56 MyComputeName kernel: [  480.208632] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:56 MyComputeName kernel: [  480.208635] ata4.00: cmd 35/00:00:00:0d:48/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:56 MyComputeName kernel: [  480.208635]          res 51/84:80:80:0e:48/84:02:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:12:56 MyComputeName kernel: [  480.208637] ata4.00: status: { DRDY ERR }
Jan  2 12:12:56 MyComputeName kernel: [  480.208639] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:56 MyComputeName kernel: [  480.208647] ata4: soft resetting link
Jan  2 12:12:56 MyComputeName kernel: [  480.396324] ata4.00: configured for UDMA/33
Jan  2 12:12:56 MyComputeName kernel: [  480.405277] ata4.01: configured for UDMA/133
Jan  2 12:12:56 MyComputeName kernel: [  480.405304] ata4: EH complete
Jan  2 12:12:57 MyComputeName kernel: [  481.210617] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:57 MyComputeName kernel: [  481.210625] ata4.00: BMDMA stat 0x66
Jan  2 12:12:57 MyComputeName kernel: [  481.210630] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:57 MyComputeName kernel: [  481.210640] ata4.00: cmd 35/00:00:00:3d:48/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:57 MyComputeName kernel: [  481.210640]          res 51/84:e0:20:40:48/84:00:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:12:57 MyComputeName kernel: [  481.210645] ata4.00: status: { DRDY ERR }
Jan  2 12:12:57 MyComputeName kernel: [  481.210649] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:57 MyComputeName kernel: [  481.210662] ata4: soft resetting link
Jan  2 12:12:57 MyComputeName kernel: [  481.396321] ata4.00: configured for UDMA/33
Jan  2 12:12:57 MyComputeName kernel: [  481.404762] ata4.01: configured for UDMA/133
Jan  2 12:12:57 MyComputeName kernel: [  481.404792] ata4: EH complete
Jan  2 12:12:57 MyComputeName kernel: [  481.964797] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:57 MyComputeName kernel: [  481.964802] ata4.00: BMDMA stat 0x66
Jan  2 12:12:57 MyComputeName kernel: [  481.964805] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:57 MyComputeName kernel: [  481.964809] ata4.00: cmd 35/00:00:00:5d:48/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:57 MyComputeName kernel: [  481.964809]          res 51/84:40:c0:5f:48/84:01:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:12:57 MyComputeName kernel: [  481.964811] ata4.00: status: { DRDY ERR }
Jan  2 12:12:57 MyComputeName kernel: [  481.964812] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:57 MyComputeName kernel: [  481.964820] ata4: soft resetting link
Jan  2 12:12:58 MyComputeName kernel: [  482.152335] ata4.00: configured for UDMA/33
Jan  2 12:12:58 MyComputeName kernel: [  482.169117] ata4.01: configured for UDMA/133
Jan  2 12:12:58 MyComputeName kernel: [  482.169147] ata4: EH complete
Jan  2 12:12:58 MyComputeName kernel: [  482.455592] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:12:58 MyComputeName kernel: [  482.455597] ata4.00: BMDMA stat 0x66
Jan  2 12:12:58 MyComputeName kernel: [  482.455600] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:12:58 MyComputeName kernel: [  482.455604] ata4.00: cmd 35/00:00:00:65:48/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:12:58 MyComputeName kernel: [  482.455604]          res 51/84:c0:40:66:48/84:02:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:12:58 MyComputeName kernel: [  482.455606] ata4.00: status: { DRDY ERR }
Jan  2 12:12:58 MyComputeName kernel: [  482.455607] ata4.00: error: { ICRC ABRT }
Jan  2 12:12:58 MyComputeName kernel: [  482.455616] ata4: soft resetting link
Jan  2 12:12:58 MyComputeName kernel: [  482.640340] ata4.00: configured for UDMA/33
Jan  2 12:12:58 MyComputeName kernel: [  482.656346] ata4.01: configured for UDMA/133
Jan  2 12:12:58 MyComputeName kernel: [  482.656375] ata4: EH complete
Jan  2 12:13:04 MyComputeName kernel: [  488.170485] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:04 MyComputeName kernel: [  488.170491] ata4.00: BMDMA stat 0x66
Jan  2 12:13:04 MyComputeName kernel: [  488.170493] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:04 MyComputeName kernel: [  488.170497] ata4.00: cmd 35/00:00:00:b1:88/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:04 MyComputeName kernel: [  488.170497]          res 51/84:10:f0:b4:88/84:00:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:13:04 MyComputeName kernel: [  488.170499] ata4.00: status: { DRDY ERR }
Jan  2 12:13:04 MyComputeName kernel: [  488.170500] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:04 MyComputeName kernel: [  488.170508] ata4: soft resetting link
Jan  2 12:13:04 MyComputeName kernel: [  488.356333] ata4.00: configured for UDMA/33
Jan  2 12:13:04 MyComputeName kernel: [  488.372338] ata4.01: configured for UDMA/133
Jan  2 12:13:04 MyComputeName kernel: [  488.372372] ata4: EH complete
Jan  2 12:13:06 MyComputeName kernel: [  490.193861] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:06 MyComputeName kernel: [  490.193866] ata4.00: BMDMA stat 0x66
Jan  2 12:13:06 MyComputeName kernel: [  490.193869] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:06 MyComputeName kernel: [  490.193873] ata4.00: cmd 35/00:00:00:21:c8/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:06 MyComputeName kernel: [  490.193873]          res 51/84:10:f0:22:c8/84:02:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:13:06 MyComputeName kernel: [  490.193875] ata4.00: status: { DRDY ERR }
Jan  2 12:13:06 MyComputeName kernel: [  490.193876] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:06 MyComputeName kernel: [  490.193884] ata4: soft resetting link
Jan  2 12:13:06 MyComputeName kernel: [  490.380319] ata4.00: configured for UDMA/33
Jan  2 12:13:06 MyComputeName kernel: [  490.397060] ata4.01: configured for UDMA/133
Jan  2 12:13:06 MyComputeName kernel: [  490.397122] ata4: EH complete
Jan  2 12:13:06 MyComputeName kernel: [  490.398090] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:06 MyComputeName kernel: [  490.398097] ata4.00: BMDMA stat 0x66
Jan  2 12:13:06 MyComputeName kernel: [  490.398102] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:06 MyComputeName kernel: [  490.398112] ata4.00: cmd 35/00:00:00:21:c8/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:06 MyComputeName kernel: [  490.398112]          res 51/84:90:70:21:c8/84:03:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:13:06 MyComputeName kernel: [  490.398117] ata4.00: status: { DRDY ERR }
Jan  2 12:13:06 MyComputeName kernel: [  490.398121] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:06 MyComputeName kernel: [  490.398137] ata4: soft resetting link
Jan  2 12:13:06 MyComputeName kernel: [  490.584319] ata4.00: configured for UDMA/33
Jan  2 12:13:06 MyComputeName kernel: [  490.601170] ata4.01: configured for UDMA/133
Jan  2 12:13:06 MyComputeName kernel: [  490.601230] ata4: EH complete
Jan  2 12:13:07 MyComputeName kernel: [  491.414329] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:07 MyComputeName kernel: [  491.414334] ata4.00: BMDMA stat 0x66
Jan  2 12:13:07 MyComputeName kernel: [  491.414337] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:07 MyComputeName kernel: [  491.414341] ata4.00: cmd 35/00:00:00:5d:c8/00:04:23:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:07 MyComputeName kernel: [  491.414341]          res 51/84:f0:10:60:c8/84:00:23:00:00/03 Emask 0x30 (host bus error)
Jan  2 12:13:07 MyComputeName kernel: [  491.414343] ata4.00: status: { DRDY ERR }
Jan  2 12:13:07 MyComputeName kernel: [  491.414344] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:07 MyComputeName kernel: [  491.414352] ata4: soft resetting link
Jan  2 12:13:07 MyComputeName kernel: [  491.600341] ata4.00: configured for UDMA/33
Jan  2 12:13:07 MyComputeName kernel: [  491.616675] ata4.01: configured for UDMA/133
Jan  2 12:13:07 MyComputeName kernel: [  491.616723] ata4: EH complete
Jan  2 12:13:12 MyComputeName kernel: [  496.534788] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:12 MyComputeName kernel: [  496.534793] ata4.00: BMDMA stat 0x66
Jan  2 12:13:12 MyComputeName kernel: [  496.534796] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:12 MyComputeName kernel: [  496.534800] ata4.00: cmd 35/00:00:00:89:08/00:04:24:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:12 MyComputeName kernel: [  496.534800]          res 51/84:a1:5f:8c:08/84:00:24:00:00/04 Emask 0x30 (host bus error)
Jan  2 12:13:12 MyComputeName kernel: [  496.534802] ata4.00: status: { DRDY ERR }
Jan  2 12:13:12 MyComputeName kernel: [  496.534803] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:12 MyComputeName kernel: [  496.534811] ata4: soft resetting link
Jan  2 12:13:12 MyComputeName kernel: [  496.720324] ata4.00: configured for UDMA/33
Jan  2 12:13:12 MyComputeName kernel: [  496.729099] ata4.01: configured for UDMA/133
Jan  2 12:13:12 MyComputeName kernel: [  496.729130] ata4: EH complete
Jan  2 12:13:13 MyComputeName kernel: [  498.010013] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:13 MyComputeName kernel: [  498.010018] ata4.00: BMDMA stat 0x66
Jan  2 12:13:13 MyComputeName kernel: [  498.010021] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:13 MyComputeName kernel: [  498.010024] ata4.00: cmd 35/00:00:00:d5:47/00:04:24:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:13 MyComputeName kernel: [  498.010024]          res 51/84:60:a0:d6:47/84:02:24:00:00/04 Emask 0x30 (host bus error)
Jan  2 12:13:13 MyComputeName kernel: [  498.010027] ata4.00: status: { DRDY ERR }
Jan  2 12:13:13 MyComputeName kernel: [  498.010028] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:13 MyComputeName kernel: [  498.010036] ata4: soft resetting link
Jan  2 12:13:14 MyComputeName kernel: [  498.196337] ata4.00: configured for UDMA/33
Jan  2 12:13:14 MyComputeName kernel: [  498.204836] ata4.01: configured for UDMA/133
Jan  2 12:13:14 MyComputeName kernel: [  498.204867] ata4: EH complete
Jan  2 12:13:14 MyComputeName cracklib: no dictionary update necessary.
Jan  2 12:13:18 MyComputeName kernel: [  502.192361] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:18 MyComputeName kernel: [  502.192365] ata4.00: BMDMA stat 0x66
Jan  2 12:13:18 MyComputeName kernel: [  502.192368] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:18 MyComputeName kernel: [  502.192372] ata4.00: cmd 35/00:00:00:c5:87/00:04:24:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:18 MyComputeName kernel: [  502.192372]          res 51/84:40:c0:c5:87/84:03:24:00:00/04 Emask 0x30 (host bus error)
Jan  2 12:13:18 MyComputeName kernel: [  502.192374] ata4.00: status: { DRDY ERR }
Jan  2 12:13:18 MyComputeName kernel: [  502.192375] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:18 MyComputeName kernel: [  502.192384] ata4: soft resetting link
Jan  2 12:13:18 MyComputeName kernel: [  502.380357] ata4.00: configured for UDMA/33
Jan  2 12:13:18 MyComputeName kernel: [  502.396819] ata4.01: configured for UDMA/133
Jan  2 12:13:18 MyComputeName kernel: [  502.396870] ata4: EH complete
Jan  2 12:13:22 MyComputeName NetworkManager[1590]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  2 12:13:24 MyComputeName kernel: [  508.224636] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan  2 12:13:24 MyComputeName kernel: [  508.224644] ata4.00: BMDMA stat 0x66
Jan  2 12:13:24 MyComputeName kernel: [  508.224650] ata4.00: failed command: WRITE DMA EXT
Jan  2 12:13:24 MyComputeName kernel: [  508.224660] ata4.00: cmd 35/00:00:00:2d:c8/00:04:24:00:00/e0 tag 0 dma 524288 out
Jan  2 12:13:24 MyComputeName kernel: [  508.224660]          res 51/84:40:c0:30:c8/84:00:24:00:00/04 Emask 0x30 (host bus error)
Jan  2 12:13:24 MyComputeName kernel: [  508.224665] ata4.00: status: { DRDY ERR }
Jan  2 12:13:24 MyComputeName kernel: [  508.224668] ata4.00: error: { ICRC ABRT }
Jan  2 12:13:24 MyComputeName kernel: [  508.224681] ata4: soft resetting link
Jan  2 12:13:24 MyComputeName kernel: [  508.412317] ata4.00: configured for UDMA/33
Jan  2 12:13:24 MyComputeName kernel: [  508.420716] ata4.01: configured for UDMA/133
Jan  2 12:13:24 MyComputeName kernel: [  508.420770] ata4: EH complete
Jan  2 12:13:25 MyComputeName rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="1186" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
```

This Toshiba Drive is new and its the Second one. Days ago Ive got the same Drive with the same errors so i've replaced it. I cannot imagine that I have got two drives with the same error. So I guess its may the cables or the mainboard but the "old" System with Seagate & WDC runs very stable without hardware problems. Ive allready tried to format with GPT but the same error appears.  Also when the drive is set as additional drive. System runs good for round about 20 min, then it freezes completely. 

Hope youll forgive my bad grammar and also bad english .. Im from Germany.....
May one of you guys has a solution for that problem.

---

### Post by tgalati4 on 2014-01-02
Perhaps not enough power from the power supply to support the extra drive?  The older drives may use less power (or have broken in and spin easier).  Try removing some components to reduce the electrical load and see if the drive stays running for more than 20 minutes.  And it is possible to get two defective drives, especially if there is a bad batch of drives and they are from the same batch.

---

