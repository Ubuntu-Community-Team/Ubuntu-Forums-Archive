---
title: "Upgrade Query"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by Dave2k6 on 2011-06-15
Hi.

I currently have Ubuntu 10.04 LTS 32-bit installed alongside Windows 7 32-bit.

My laptop processor is 64-bit compatible (Acer Aspire 6930G). Confirmed this via Windows 7's system information...

```
  Manufacturer Acer, inc. 
  Model Aspire 6930G  
  Total amount of system memory 3.00 GB RAM 
  System type 32-bit operating system 
  Number of processor cores 2 
  64-bit capable Yes
```

So, what is best upgrade from 10.04 to 11.04 (staying with 32-bit), or a fresh install of 11.04 64-bit (removing my previous 10.04 version).

---

### Post by Slovak on 2011-06-15
You first have to upgrade to 10.10 before going to 11.04, look [here]("https://help.ubuntu.com/community/MaverickUpgrades") for how to.

---

### Post by Dave2k6 on 2011-06-16
Thanks for that info.

I know that if I stay with 32-bit, that I would need to perform two upgrades (10.04 to 10.10, then 10.10 to 11.04).

Just trying to decide whether to stick with 32-bit or clean install 11.04 64 bit (as my laptop is 64-bit compatible). What do others recommend I do ?

Just for information, my partitions are:

```
sda1 Recovery Partition (Windows) 10Gb
sda2 Windows 7 (32-bit) (NTFS) 219Gb
sda3 OEM Partition (Windows) 4Gb

sdb1 Data Partition (NTFS) 229Gb
sdb2 Boot Partition (Linux) 1Gb
sdb3 Swap Partition (Linux) 3Gb

sdc1 Root Partition (Linux ext3) 250Gb
sdc2 Home Partition (Linux ext3) 250Gb
```

Note: sda & sdb are the two internal 250Gb HDD
      sdc is the external 500Gb USB2 HDD

---

### Post by mörgæs on 2011-06-16
Before going further I would recommend testing 11.04 in a live boot.

---

### Post by awam66 on 2011-06-16
I would stick to 32 bit. I have both on my desktop and there are some issues with the 64bit.

---

### Post by Dave2k6 on 2011-06-16
What issues are there with 64bit at the moment ?

---

