---
title: "Zcat boot.img.gz &gt; /dev/sdc Error Msg"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by FrodoDLB on 2010-11-07
Greetings,

I have Ubuntu version 10.10 loaded as dual boot on a Windows XP Pro system and it is working great. I want to try the boot from USB option for my laptops. I have downloaded the file boot.img.gz. When I execute the command:

"zcat /home/doug/Downloads/boot.img.gz > /dev/sdc" 

I get the following error:

doug@doug-MS-6728:~$ zcat /home/doug/Downloads/boot.img.gz > /dev/sdc
bash: /dev/sdc: Permission denied

The USB thumb drive is a 8GB W95 Fat32 (LBA) (0x0c) and is bootable according to the Disk Utility. In the top drive information it says the partitioning is : "Master Boot Record". There is only the one partition.

Do I need to be the administrator to run this command? Do I need to move the file to another location to run the command? Any help would be appreciated.

Thanks in Advance,

Doug

---

### Post by david_kt on 2010-12-25
Try:

```
sudo su
"zcat /home/doug/Downloads/boot.img.gz > /dev/sdc" 
```

DK

---

