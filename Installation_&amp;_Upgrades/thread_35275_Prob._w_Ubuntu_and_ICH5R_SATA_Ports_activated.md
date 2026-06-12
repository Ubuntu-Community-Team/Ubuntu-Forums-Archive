---
title: "Prob. w/ Ubuntu and ICH5R SATA Ports activated"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by roadrunner on 2005-05-18
Hy everyone,
nice to be here ;-) 

I'm tried Installing Ubuntu on my Fileserver without luck, having always the same Problem:

SYSCONFIG:
[SIZE=1]P4 2,4C
MSI 865PE-Neo2Series (newest BIOS)
4x256mb pc3200 Samsung cl3
ICH5r:
1xSATA-WD36gb Raptor **Win XP**
1xSATA-WD120gb NTFS
obboardPromiseFastTrack376/378:
2x SATA-WD160gb raid 0 array  NTFS
pci: Highpoint RocketRaid 1540/1640 Sata RAID
2x SATA-Maxtor200gb NTFS
2x SATA-WD200gb NTFS
IDE1 Master: 30gb Seagate Cuda 4 **here i'd like to install Ubuntu** 
IDE2 Master: DVD-Rom[/SIZE]

always when the sata ports are activated, i can't install properly nor b00t into Ubuntu.
with these errors during first startup:
```

IRQ18: nobody cared (try booting with the "irqpoll" option)
handlers:
[<f8877e24>] ......idecore
[<f8877e24>] ......idecore
[<f8877e24>] ......usbcore
Disabling IRQ18

```
i already tried boot arguments noacpi nolacpi and irqpoll, no luck :/


when deaktivating these SATA-Ports, the installation already hangs up when ubuntu tries finding networkfolders (50% of installation).

any help please? :-|

/EDIT:
ok, after using the ICH5r SAtA in Legacy Mode it worked out without the "irqpoll" option!
but still i can't use the onboard promise 3112r sata controller :/

---

### Post by Marcelo Santos on 2005-09-08
> **roadrunner]Hy everyone,
nice to be here  said:**
> P4 2,4C
MSI 865PE-Neo2Series (newest BIOS)
4x256mb pc3200 Samsung cl3
ICH5r:
1xSATA-WD36gb Raptor **Win XP**
1xSATA-WD120gb NTFS
obboardPromiseFastTrack376/378:
2x SATA-WD160gb raid 0 array  NTFS
pci: Highpoint RocketRaid 1540/1640 Sata RAID
2x SATA-Maxtor200gb NTFS
2x SATA-WD200gb NTFS
IDE1 Master: 30gb Seagate Cuda 4 **here i'd like to install Ubuntu** 
IDE2 Master: DVD-Rom[/SIZE]

always when the sata ports are activated, i can't install properly nor b00t into Ubuntu.
with these errors during first startup:
```

IRQ18: nobody cared (try booting with the "irqpoll" option)
handlers:
[<f8877e24>] ......idecore
[<f8877e24>] ......idecore
[<f8877e24>] ......usbcore
Disabling IRQ18

```
i already tried boot arguments noacpi nolacpi and irqpoll, no luck :/


when deaktivating these SATA-Ports, the installation already hangs up when ubuntu tries finding networkfolders (50% of installation).

any help please? :-|

/EDIT:
ok, after using the ICH5r SAtA in Legacy Mode it worked out without the "irqpoll" option!
but still i can't use the onboard promise 3112r sata controller :/

I'm having the same issue that You have.

I can't install Ubuntu, and if I disable SATA Controller, My Hard Disk isn't available.

How I can fix this?

MarcSant.

---

