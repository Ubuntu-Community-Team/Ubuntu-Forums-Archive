---
title: "Installation problem with SCSI RAID Adapter"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by wokka on 2006-04-09
](*,) Hi all,

I am a first time installer of the ubuntu product and am having problems installing on a server with a RAID 5 configuration and am wondering if anyone could help?

The details of the server are as follows;

IPEX C400RM Server
PIII 1GHz with 1GIG RAM
Adaptec AIC 7896 SCSI RAID Controller
4 x Seagate 18.4 GB 10000RPM U160 S3 HD (3 x RAID 5, 1 x HOT Spare)

I tried the installation process after following the F6 instructions for special boot parameters for selected disk controllers with the following syntax;

**linux aic7896=no_reset **

The issue I am facing is that I receive the following message when I process the Configure Software RAID section of the setup;

**"No RAID partitions available - No unused partitions of the type "Linux RAID Autodetect are available. Please create such a partition, or delete an already used multidisk device to free its partitions". **

After doing some research I found some information on the cfdisk tool to allow me to change the partition type. I can use the cfdisk tool via the execute shell via the install CD, but I receive the following message;

**"Opened disk read only - - you have no permission to write"**.

_Additional Information_

Windows Server 2003 Standard Edition is currently installed on the server.
The server has 2 partitions. 1 which contained the server build and i for data. The data partition has been formatted in an attempt to allow a free partition.

If anyone could be of any assistance it would be muchly appreciated.

---

