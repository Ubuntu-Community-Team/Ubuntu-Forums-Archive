---
title: "Windows XP(Master hdd) can't be loaded,Ubuntu installed on Slave HDD"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by ameya_joshi on 2010-01-06
Hi,

I have installed WindowsXP on Primary hdd (/dev/sda) and ubuntu on slave HDD (/dev/sdb).

So i set my primary boot device as the slave HDD.

In the grub menu it shows the window xp option but when i choose it it doesnt load,gives error.

So to load XP i have to change the boot device back to primary HDD.

My guess as windows boot record is in primary partition and grub bein in slave hdd it is not able to find the windows boot record and hence windows is not getting loaded.

grub menu list entries are correct

[I]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1[/I]

While The fdisk o/p is this

[I]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x214f214e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       19456   120439305    f  W95 Ext'd (LBA)
/dev/sda5            4463        8924    35840983+   7  HPFS/NTFS
/dev/sda6            8925       14023    40957686    7  HPFS/NTFS
/dev/sda7           14024       19456    43640541    7  HPFS/NTFS

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06dae652

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1158     9301603+  83  Linux
/dev/sdb2            1159        1216      465885    5  Extended
/dev/sdb5            1159        1216      465853+  82  Linux swap / Solaris

[/I]Is there any way/solution where in i can load windows xp while keeping the slave hdd as primary boot device.

Suggestions are welcome.

Regards,
Ameya Joshi

---

### Post by darkod on 2010-01-06
Boot your ubuntu with the slave hdd first in boot order and open the file /boot/grub/device.map
Copy the content here so we can see which of your drives is hd0 and hd1.

---

### Post by ameya_joshi on 2010-01-06
Hi Darko,

Here is the o/p of device map

hd0  /dev/sda (Master HDD)
hd1  /dev/sdb (Slave HDD)
hd2  /dev/sdc

---

### Post by presence1960 on 2010-01-06
Boot into ubuntu. Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
that is a lowercase L in .lst

scroll down to this :

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1
```

Change it to:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title         Microsoft Windows XP Professional
rootnoverify  (hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1
```

Keep the disk with Ubuntu on it as first disk to boot in BIOS.

---

### Post by ameya_joshi on 2010-01-06
Hi Thanks,

It stuck at Read error.

what does rootnoverify do , identifies where the kernel image is rt??

while booting ubuntu it boots from (hd0,0) i.e according to device map /dev/sda

but linux kernel image is on (hd1) /dev/sdb. This has confused me


Regards

---

### Post by ameya_joshi on 2010-01-06
Hi,

It finally worked 
i changed the map command 

map (hd1) (hd0)
map (hd0) (hd1)

And it worked



But am still confused abt the root command

why does ubuntu boot from device (hd0,0) when in device map hd0 is /dev/sda while ubuntu kernel image is on /dev/sdb (hd1) in the device.map file?

what exactly is hdbias in root command is it partition no?? 


so can any body clear my doubt

---

### Post by presence1960 on 2010-01-06
> **ameya_joshi said:**
> Hi,

It finally worked 
i changed the map command 

map (hd1) (hd0)
map (hd0) (hd1)

And it worked



But am still confused abt the root command

why does ubuntu boot from device (hd0,0) when in device map hd0 is /dev/sda while ubuntu kernel image is on /dev/sdb (hd1) in the device.map file?

what exactly is hdbias in root command is it partition no?? 


so can any body clear my doubt

Because in Legacy GRUB 0.97 the (hdx,y) designations where x = device & y = partition is different than GRUB 2. In Legacy GRUB the x (device) designation is taken from the order of hard disk booting in BIOS not device map or fdisk output. Since you have sdb booting first to bring up GRUB that is now (hd0) and sda becomes (hd1) because it boots second.

It can be confusing that is one of the reasons why GRUB 2 works differently in that respect.

---

### Post by ameya_joshi on 2010-01-10
Thnx presence ....... 1 more question....any idea why my USB keyboard sometimes works while booting (when the grub screen comes) and sometimes it doesnt!! googled it ..dint find much

---

### Post by presence1960 on 2010-01-10
> **ameya_joshi said:**
> Thnx presence ....... 1 more question....any idea why my USB keyboard sometimes works while booting (when the grub screen comes) and sometimes it doesnt!! googled it ..dint find much

Go into BIOS and make sure you have USB support enabled. It may be under the term USB Legacy support.

---

