---
title: "How to add space to root filesystem dynamically ?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by samjam86 on 2009-12-26
I am facing space issues on my 10GB Ubuntu root filesystem.

So I decided to create a new filesystem at the end of the harddisk and then add this space to some directory under root filesystem.

The below is the output from "fdisk -l":
sda5 -> Ubuntu root FS
sda9 -> new ext4 FS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f27a03e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       38913   286350592+   5  Extended
/dev/sda5            3265        4569    10482381   83  Linux
/dev/sda6            4570        7180    20970496    7  HPFS/NTFS
/dev/sda7            7181        7429     2000061   82  Linux swap / Solaris
/dev/sda8            7430       37528   241770186    b  W95 FAT32
/dev/sda9           37529       38913    11124981   83  Linux


Here, I will definitely need some help on how to mount sda9 on some location inside sda5 such that new software installation files are saved on sda9 in place of sda5.

Help is greatly appreciated.

---

### Post by oldfred on 2009-12-26
Are you sure you even have 10GB? Blocks are 512.

run 
sudo parted -l  (el not I or 1)

and 
sudo df -h

Generally you can houseclean downloaded files and move /home easier.

HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean

I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..
Autoclean cleans up the downloaded archives (.gz or .tar) files used to install things. Autoremove cleans libraries that are no longer needed.
you can run any "apt-get" command predeccesed by the "-s" (simulate) switch

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by phillw on 2009-12-26
Hi,

can you post the output of ..

```
df -ah | grep dev
```

Thanks,

Phill.

---

### Post by samjam86 on 2009-12-26
Hi Phillw,

Output of

df -h | grep dev

is

/dev/sda5             9.9G  4.4G  5.1G  47% /
udev                  1.5G  308K  1.5G   1% /dev
none                     0     0     0   -  /dev/pts
none                  1.5G  648K  1.5G   1% /dev/shm
/dev/sda1              26G   16G  9.3G  64% /media/sda1
/dev/sda6              20G   14G  6.1G  70% /media/sda6
/dev/sda8             231G   76G  155G  33% /media/sda8
/dev/sda9              11G  169M  9.8G   2% /media/sda9

---

### Post by phillw on 2009-12-26
> **samjam86 said:**
> Hi Phillw,

Output of

df -h | grep dev

is

/dev/sda5             9.9G  4.4G  5.1G  47% /
udev                  1.5G  308K  1.5G   1% /dev
none                     0     0     0   -  /dev/pts
none                  1.5G  648K  1.5G   1% /dev/shm
/dev/sda1              26G   16G  9.3G  64% /media/sda1
/dev/sda6              20G   14G  6.1G  70% /media/sda6
/dev/sda8             231G   76G  155G  33% /media/sda8
/dev/sda9              11G  169M  9.8G   2% /media/sda9

Your root area is still in good health. 10GB for a purely **/** is very good :)
You can see from that output, it is still 47% free ... no need to worry. 

If you have a seperate /home partition, then 10GB is a really kewl amount to allocate to /  (I'm biased, of course, coz that's what I give my LAMP Server - lol)

I've got be honest, I've never seen an allocation table like that !!!

Can you pop on the result of ```
sudo fdisk -l
```  That is little L, not the number 1

Regards,

Phill.

---

### Post by samjam86 on 2009-12-27
Output of

fdisk -l

is

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f27a03e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       38913   286350592+   5  Extended
/dev/sda5            3265        4569    10482381   83  Linux
/dev/sda6            4570        7180    20970496    7  HPFS/NTFS
/dev/sda7            7181        7429     2000061   82  Linux swap / Solaris
/dev/sda8            7430       37528   241770186    b  W95 FAT32
/dev/sda9           37529       38913    11124981   83  Linux


My issue is that I normally do updates on regular basis and when I was using 9.04, that time within 3 months my root was full to about 80%. This time I am trying to be a bit good with my root **/** ;).

Please tell me some of the good ways to manage file system. My normal use consists of installations of softwares and games.

---

