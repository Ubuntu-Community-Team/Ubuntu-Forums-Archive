---
title: "Triple Boot Help Please"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by thechungster on 2008-10-12
Hey, I'm typically a noob at linux at the moment. 
So, I'm on MacOSX 10.5.5. And I'm using VMware Fusion to boot Ubuntu 8.04. I'm trying to boot Linux via this guide. 
[Triple Boot via BootCamp - OnMac.net Wiki](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#)
But thing is, I already have my windows partioned and I have no idea what to do to partion my existing MacHDD so it will be partioned.

Ok, my current Harddrive stats are.
MacHDD: 125.88GB
Windows: 22.86GB (NTFS)

This is what I get with diskutil

```
#:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            125.9 Gi   disk0s2
   3:       Microsoft Basic Data                         22.9 Gi    disk0s3

```

What I really want is the command to partion my HDD. This is the command the website gives.

```
sudo diskutil resizeVolume [disk identifier] [disk size] [partition type] ["Partition label"] [partition size] [partition type] ["Partition label"] [partition size]
```
I'm slightly confused at the moment and help is greatly appreciated

---

