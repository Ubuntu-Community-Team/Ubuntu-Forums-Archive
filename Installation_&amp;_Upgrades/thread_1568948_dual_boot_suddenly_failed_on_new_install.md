---
title: "dual boot suddenly failed on new install"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by shallowthought on 2010-09-06
1. made 3 live CD's with:
    (a) 10.04 32 bit;
    (b)  10.04.1 32 bit;
     (c)  10.04.1 64 bit.
but can only boot from the 10.04 32 bit.

2. following local advice, I used unetbootin to put 10.04.1 64 bit on a flash drive and can boot fine from the flash drive

3. went through a dual boot installation from the flash drive.
4. everything worked fine (except no sound in Ubuntu). I
booted several times into Ubuntu and several times into Windows 7.
It worked fine.
5. shut computer down for the night. In the morning tried to boot and got message:
             no module name found
6.  I then tried F12 on boot and went into the BIOS. This is what it said:
CD/DVD : PO-HL-DT-ST  DVD +/-RW GH5

SATA: P1-WDC  WD100FAES -75W7A0

Boot to Utility Partition

Diagnostics

<Enter Setup>

7. following advice on a thread below I typed:
    sudo fdisk -l

This is what I get in part:

Disk /dev/sda : 1000.2 GB
.
.
.

 Device Boot     Start       End      Blocks        Id      System
/dev/sda1         1           5         ...         de      dell utility
/dev/sda2         6         1235        ....         7        HPFS/NTFS
/dev/sda3        1235       63365     499063142      7       HPFS/NTFS
/dev/sda4        63365      121602    467783681      5       Extended
/dev/sda5        63365      119240    448813056      83       Linux
/dev/sda6        119240     121602               82          Linux Swap / Solaris 

I'm not sure what this all means. Perhaps the desired partition is really there,
but I can't access it?

8. Don't know what to do now. Need help!
I am willing to give up Windows 7 and just install Ubuntu on the entire disk
 if it avoids this kind of problem.

9. My set up: a brand new Dell xps 9100 with 
                  i7 960 microprocessor
                   9gb ram
                   ATI Radeon HD 5770 1024MB GDDR5
                   1TB Serial ATA 2 Hard Drive 

10. I am barely computer literate
11. Thanks in advance for any help

---

