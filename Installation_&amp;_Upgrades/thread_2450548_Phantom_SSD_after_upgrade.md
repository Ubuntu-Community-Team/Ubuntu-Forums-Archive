---
title: "Phantom SSD after upgrade"
date: 2020-09-16
forum: Installation &amp; Upgrades
---

### Post by twonotes on 2020-09-16
I have a System76 desktop, a few years old, that came with two 250G Samsung SSD drives, one with Ubuntu installed and an extra one for additional data. The motherboard is by Gigabyte. The main UUIDs ended as follows (last four digits shown):
 ```
Location     Label       UUID
    /dev/sda2    Ubuntu   e32b
    /dev/sdb2     MoreData 7a3c
```

Recently I decided to upgrade the root device to a 500G WD Blue SSD.  I installed a fresh copy of Ubuntu 20.04 on this device and it works properly.  It has /home split out to a separate partition.  I connected it in place of the "Ubuntu" SSD, however it is showing up as being at /dev/sdb instead of /dev/sda as I expected.

I still want access to the "MoreData" device, which is still connected on the same cable it was always on.  However, all the tools that display device characteristics ("blkid -c /dev/null", "Disks", etc) show this arrangement:

    ```
Location     Label      UUID
    /dev/sda2     Ubuntu   e32b
    /dev/sdb3     NewRoot  d8b0
    /dev/sdb6     NewHome  2510
```

The "Ubuntu" SSD is physically disconnected and removed.  I have it sitting on my desk.  Yet the system thinks it is still installed and does NOT show the MoreData device 7a3c as being present at all.  The NewRoot partition is indeed the system that is running and "/" points there.

Any attempts to mount whatever /dev/sda2 is give no error message but do not in fact mount anything.  This one line appears in dmesg:

[ 1767.349944] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)

If I then try to unmount it, I get
    umount: /dev/sda2: not mounted.

How do I force the new system, or the BIOS, to refresh its idea of what disks are really connected?  I have rebooted several times.

---

### Post by oldfred on 2020-09-16
Drives are enumerated by UEFI/BIOS and usually are in port order.
So depending on what port you installed new drive, it may be same or different device like /dev/sda.
You should always use UUIDs for mounting in fstab.

Post this:
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,MODEL,UUID | egrep -v "^loop"
and:
cat /etc/fstab

---

### Post by twonotes on 2020-09-16
```
NAME   FSTYPE   LABEL   MOUNTPOINT                     SIZE MODEL                     UUID
sda                                                  232.9G Samsung_SSD_850_EVO_250GB 
&#9500;&#9472;sda1 vfat     EFI                                    512M                           8FE6-F037
&#9500;&#9472;sda2 ext4     Ubuntu                               228.4G                           e6741671-2ae1-468c-8902-341a2e81e32b
&#9492;&#9472;sda3 swap                                              4G                           0695ac1e-dc9e-4623-8184-1fb455cf9938
sdb                                                  465.8G WDC_WDS500G2B0A-00SM50    
&#9500;&#9472;sdb1                                                   2M                           
&#9500;&#9472;sdb2 vfat             /boot/efi                      500M                           BF93-57AC
&#9500;&#9472;sdb3 ext4     NewRoot /                               30G                           88066788-2de3-45a8-b4f5-24d258eed8b0
&#9500;&#9472;sdb4 ext4             /var                            10G                           6e7d6699-82d0-4f1e-af73-c59739031784
&#9500;&#9472;sdb5 swap             [SWAP]                          10G                           87b230e5-0de9-40de-ad4b-7efef2d7b1eb
&#9492;&#9472;sdb6 ext4     NewHome /home                        415.3G                           6eab7120-ed89-448d-a0de-eddbfee72510
sr0    
```   

fstab:
```
UUID=88066788-2de3-45a8-b4f5-24d258eed8b0 /               ext4    errors=remount
-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=BF93-57AC  /boot/efi       vfat    utf8,umask=007,gid=46 0       1
# /home was on /dev/sda6 during installation
UUID=6eab7120-ed89-448d-a0de-eddbfee72510 /home           ext4    defaults      
  0       2
# /var was on /dev/sda4 during installation
UUID=6e7d6699-82d0-4f1e-af73-c59739031784 /var            ext4    defaults      
  0       2
# swap was on /dev/sda5 during installation
UUID=87b230e5-0de9-40de-ad4b-7efef2d7b1eb none            swap    sw            
  0       0

UUID=acdb38ba-ae62-474d-b464-807f31bb7a3c   /mnt/extra   ext4  noatime  0 0

```

The trouble is, this does not describe physical reality.

---

### Post by twonotes on 2020-09-16
Well, turns out it DOES describe physical reality.  All along I thought that the Samsung SSD that was bolted to the bottom of the case was the "extra" one, and the one nestled up in the proper SSD cage, close to the motherboard, was the "boot" disk.  Turns out System76 put them ion the other way around.  So blkid was telling me the truth and the disk I had disconnec ted was the "extra data" one I wanted all along.  Now I have put stickies on each one saying what each one is, and all is as I expect again.

Thank you for the fancy blkid command though - it helped me (through combinations of plugging and unplugging) figure out which was which.  It would be nice of the serial numbers printed on the bottom of each drive showed up in those listings.

---

