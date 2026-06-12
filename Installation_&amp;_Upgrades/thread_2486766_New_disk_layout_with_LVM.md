---
title: "New disk layout with LVM"
date: 2023-05-09
forum: Installation &amp; Upgrades
---

### Post by old.dog on 2023-05-09
I am relatively new to logical volume management as I switched to it when I upgraded to Jammy Jellyfish. My current disk layout is:
```

sda               8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1            8:1    0   300M  0 part /boot/efi
&#9492;&#9472;sda2            8:2    0 931.2G  0 part 
  &#9500;&#9472;vg01-jammy  253:0    0    30G  0 lvm  /var/snap/firefox/common/host-hunspell
  &#9474;                                       /
  &#9500;&#9472;vg01-home   253:1    0   300G  0 lvm  /home
  &#9492;&#9472;vg01-archive
```

I recently bought a new disk and plan to reinstall all.  From my research it seems that it is possible to have everything including ESP boot all within logical volumes.
My question is this:  First, is this possible and, if so,  what are the advantages and disadvantages.

My computer is a Gigabyte GA-Z170XP-SLI with latest bios.

Thanks

---

### Post by Dennis N on 2023-05-09
UEFI firmware cannot read a file system of ESP if it's in a logical volume when booting your OS - it only can read files on a standard partition formatted FAT. Also, with the new "Ubuntu Desktop Installer" available in 23.04, you must have a separate boot partition that's not inside an LV when installing the OS on a logical volume. The old Ubiquity installer did not require a separate boot partition.

So, you can't have everything inside LVs.

---

### Post by old.dog on 2023-05-09
Thanks Dennis,

I appreciate the information.

Dan

---

### Post by MAFoElffen on 2023-05-10
> **Dennis N said:**
> UEFI firmware cannot read a file system of ESP if it's in a logical volume when booting your OS - it only can read files on a standard partition formatted FAT. Also, with the new "Ubuntu Desktop Installer" available in 23.04, you must have a separate boot partition that's not inside an LV when installing the OS on a logical volume. The old Ubiquity installer did not require a separate boot partition.

So, you can't have everything inside LVs.
I noticed that the new installer for 23.04 also, if you use manual mode, the partitioner is not LVM aware, and does not recognize LVM LV's, VG's, etc.

---

### Post by Dennis N on 2023-05-10
> **MAFoElffen said:**
> I noticed that the new installer for 23.04 also, if you use manual mode, the partitioner is not LVM aware, and does not recognize LVM LV's, VG's, etc.
Yes, I discovered that too. I intended to install 23.04 using an existing LV, but that is no longer possible with the manual partitioning option. "Erase disk and install" is the only option that allows LVM to be used. Perhaps better LVM support will be included before the next LTS arrives?

FWIW,
I installed 23.04 in a VM instead, but found the VM would not use the "Ubuntu on Xorg" option. Only "Ubuntu" (Wayland) worked.

---

### Post by MAFoElffen on 2023-05-10
> **Dennis N said:**
> Yes, I discovered that too. I intended to install 23.04 using an existing LV, but that is no longer possible with the manual partitioning option. "Erase disk and install" is the only option that allows LVM to be used. [COLOR=#ff0000]Perhaps better LVM support will be included before the next LTS arrives?[/COLOR]

FWIW,
I installed 23.04 in a VM instead, but found the VM would not use the "Ubuntu on Xorg" option. Only "Ubuntu" (Wayland) worked.
+1 -- The same. I created this LVM RAID6 root LV and wanted to install Lunar to it... 
```

root@lvm-raid6-on-root:/home/mafoelffen# lvs -o name,size,devices,segtype ubuntu-2204-vg
  LV       LSize  Devices                                                                                                  Type  
  lv--root 20.00g lv--root_rimage_0(0),lv--root_rimage_1(0),lv--root_rimage_2(0),lv--root_rimage_3(0),lv--root_rimage_4(0) raid6 
  lv--swap  4.00g /dev/sda2(1708)                                                                                          linear
root@lvm-raid6-on-root:/home/mafoelffen# pvs
  PV         VG             Fmt  Attr PSize   PFree  
  /dev/sda2  ubuntu-2204-vg lvm2 a--   14.64g   3.97g
  /dev/sdb1  ubuntu-2204-vg lvm2 a--   14.64g   7.97g
  /dev/sdc1  ubuntu-2204-vg lvm2 a--   14.64g   7.97g
  /dev/sdd1  ubuntu-2204-vg lvm2 a--  <19.53g <12.86g
  /dev/sde1  ubuntu-2204-vg lvm2 a--  <19.53g <12.86g
root@lvm-raid6-on-root:/home/mafoelffen# vgs
  VG             #PV #LV #SN Attr   VSize   VFree  
  ubuntu-2204-vg   5   2   0 wz--n- <82.99g <45.63g

```
The Lunar installer's partitioner does not see anything related to LVM at all. I popped a 22.04 Server Live ISO into it and even though it should have less features, it saw everything and installed fine. To do it with Lunar's Desktop Installer, you can still debootstrap it, but that is not the point. 

I really think they made some major steps backwards. I am hoping they make quite a few improvements with this installer before the next LTS release. 

Besides LVM, they crippled support for ZFS in the installer. I filed a Bug Report for that about 4 months ago. They changed it to a "Change > Format As" option in the manual partitioner section(???) I think they did that just to say it was still there. (LOL) Of course, that does not work at all... Doesn't make sense.

Dang. That was built up inside and had to come out. Sorry. Oh well. LOL. Will just have to adapt.

---

