---
title: "Installation woes"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by Kalvados on 2007-11-15
Hello,

I'm installing Ubuntu for the first time on an older machine of mine, and having problems.

I downloaded the LiveCD iso and burnt it off, booted it up, and installed it okay, right up to the point where it asked to restart the pc. No errors were reported. Very seamless installation, and I was very  impressed with what I saw up to that point.

It then rebooted, and came up with the GRUB Error 17 that I have seen reported elsewhere. I resolved this by changing the boot order of my disks in bios (this machine has 3 separate hdds), and no longer get a grub 17 error.

Now however, on bootup, I get the word GRUB appear, with a flashing cursor, and I can't do anything with it.

I found [this page]("http://osdir.com/ml/boot-loaders.grub.bugs/2002-09/msg00002.html") [osdir.com], where it points me to the [GRUB faq]("http://www.gnu.org/software/grub/grub-faq.en.html#q13") [gnu.org], and it lists three possible solutions, only two of which are appropriate to my system (all my disks are ide, and all of my disks are > 32 GB in size).

I looked into a bios update, and found that I am running the most up to date bios that my vendor supplies (PhoenixBios 4.0 Release 6.1, v11). I have no problem viewing the disk contents from the LiveCD or from windows.

So I looked into the other, that the disk order may be out in /.../boot/grub/device.map. After working out how to get permissions on this file, I changed the order to reflect the order as I had done to fix the GRUB error 17 that I had experience earlier.

But this has made no difference. I still get nothing but the word GRUB appear on bootup, and no keyboard or mouse entry possible.

This is my first ever attempt to install Ubuntu, having previously been on Fedora. I've been using the LiveCD for a little while and liked what I've seen, but if I can't install it then it isn't very usable.

Does anyone have any idea how I can resolve this issue? Any assistance massively appreciated.

---

### Post by Kalvados on 2007-11-15
Forgot to say, this is Ubuntu 7.10

---

### Post by Kalvados on 2007-11-16
I've repartitioned the drive I installed it on so that no partition is > 30 Gb, and tried this again, and still no joy. Exactly the same result, hangs on boot, showing just the word "GRUB  " and a flashing cursor.

So I can only assume that this is down to device.map, but having changed everything so that it is in the same order as the list of drives in bios, it's still not working.

Has no-one ever solved this issue before?

---

### Post by bren on 2007-11-16
the usual advice in these circumstances is to download the alternate CD (non GUI installer which requires less RAM and therefore should install easier on an old PC)

however, if the LIVE CD has been working well then I am not sure this is the correct way to go

in summary 

1) If you have the time /inclination try the alternate CD
2) if not then wait for some more advice.

if you go for 2) then you might like to run the command

lshw -short 

and post the results here so more knowledgeable people can tell you how suited your hardware specs are to "the gibbon"

bren

---

### Post by Kalvados on 2007-11-16
I've got ubuntu installed on /dev/sdc1

Because of the GRUB 17 error, I've rejigged the order in the bios so it is now:
sdc
sdb
sda
sdd

and made sdc my first bootable disk.

I've changed my device.map to reflect this. Device.map contents follow:

```
(hd0)	/dev/sdc
(hd1)	/dev/sdb
(hd2)	/dev/sda
(hd3)	/dev/sdd
```

Lastly, following is the output of lshw -short.

```

root@ubuntu:/home/ubuntu# lshw -short
H/W path          Device      Class       Description
=====================================================
                              system      XPST800
/0                            bus         SE440BX-3
/0/0                          memory      1MB BIOS
/0/4                          processor   Pentium III (Coppermine)
/0/4/9                        memory      32KB L1 cache
/0/4/a                        memory      256KB L2 cache
/0/2b                         memory      512MB System Memory
/0/2b/0                       memory      256MB DIMM DRAM Synchronous
/0/2b/1                       memory      256MB DIMM DRAM Synchronous
/0/2b/2                       memory      DIMM DRAM Synchronous [empty]
/0/100                        bridge      440BX/ZX/DX - 82443BX/ZX/DX Host bridg
/0/100/1                      bridge      440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
/0/100/1/0                    display     NV10DDR [GeForce 256 DDR]
/0/100/7                      bridge      82371AB/EB/MB PIIX4 ISA
/0/100/7.1        scsi0       storage     82371AB/EB/MB PIIX4 IDE
/0/100/7.1/0      /dev/sda    disk        27GB QUANTUM FIREBALL
/0/100/7.1/0/1    /dev/sda1   volume      27GB W95 FAT32 (LBA) partition
/0/100/7.1/1      /dev/sdb    disk        76GB IC35L080AVVA07-0
/0/100/7.1/1/1    /dev/sdb1   volume      58GB Extended partition
/0/100/7.1/1/1/5  /dev/sdb5   volume      38GB W95 FAT32 partition
/0/100/7.1/1/1/6  /dev/sdb6   volume      19GB W95 FAT32 partition
/0/100/7.1/1/2    /dev/sdb2   volume      18GB W95 FAT32 (LBA) partition
/0/100/7.1/2      /dev/sdc    disk        37GB ST340810A
/0/100/7.1/2/1    /dev/sdc1   volume      17GB Linux filesystem partition
/0/100/7.1/2/2                volume      1466MB Extended partition
/0/100/7.1/2/2/5  /dev/sdc5   volume      1466MB Linux swap / Solaris partition
/0/100/7.1/2/3    /dev/sdc3   volume      17GB Linux filesystem partition
/0/100/7.1/3      /dev/cdrom  disk        DVD+/-RW8B9
/0/100/7.1/3/0    /dev/cdrom  disk        
/0/100/7.2                    bus         82371AB/EB/MB PIIX4 USB
/0/100/7.3                    bridge      82371AB/EB/MB PIIX4 ACPI
/0/100/e          wlan0       network     ACX 111 54Mbps Wireless Interface
/0/100/10                     multimedia  SB Audigy
/0/100/10.1                   input       SB Audigy Game Port
/0/100/10.2                   bus         SB Audigy FireWire Port
/0/100/11         eth0        network     NC100 Network Everywhere Fast Ethernet

```

---

