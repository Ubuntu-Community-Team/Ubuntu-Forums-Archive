---
title: "Asus G50v - Ubuntu 10.04 LTS, Major install issue"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by mattyd on 2010-06-11
Hey there,

I was wondering if anyone can give me a hand with an issue I am having while trying to run/install Ubuntu 10.04 LTS on my lappy.

Laptop Specs:
15.4" LCD - 1450x1050
Core 2 Duo T9400 
Mobile Intel® PM45 Express Chipset +ICH9M
4gb DDR2
nVidia 9700m GT 512mb GDDR3
2x 250gb HDDs
ICH9-M SATA Controller (controlled through intel matrix storage manager)

I have attempted to setup my hard drives in the following formats and get the same error messages
- RAID 0 (striped)
- RAID 1 (mirrored)
- NON-RAID; disabled raid controller and ran them in normal SATA mode

I am getting the following various errors:
-> unable to open /dev/sda
-> unable to open /dev/sdb
-> getpwuid_r() unknown user id (0) dev/mapper/isw)biijbgffbi_Volume0
-> 1/0 error dev sr0 sector end_request
-> SQUASHFS error unable to read fragment cache entry
-> buffer I/O error

When I attempt LiveCD mode, it crashes out claiming buffer i/o and squashfs error

Also when I attempt to install Ubuntu, the installer claims it was unable to setup the hard drive(s) under ext4 or ext3 - RAID or NOT

---

### Post by dino99 on 2010-06-11
use sata mode with ahci into bios, as there are some issues with raid

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by mattyd on 2010-06-11
> **dino99 said:**
> use sata mode with ahci into bios, as there are some issues with raid[/url]

I have tried sata mode (disabling RAID) with the same results. I will try 3rd party partition tool tonight rather then built in tool for partitioning.

I cannot even start the live cd option.

---

### Post by ronparent on 2010-06-13
Once you have configured a raid in bios, it has written meta data to your drives. You would have to be able to boot into the 10.04 live cd? Once that was done you would erase the meta data by opening a terminal and running 'sudo dmraid -E /dev/sda /dev/sdb'. Once that is done you can start all over again after deciding whether of not to use raid.

Meanwhile you have to focus on getting the live cd to run on your system? If you can get it running with one or more of the <f6> options (except for 'nodmraid') you will be able to proceed.

---

