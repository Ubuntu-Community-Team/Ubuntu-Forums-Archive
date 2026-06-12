---
title: "Dual Boot: XP won't recognize share partition"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by xghstst0riesx on 2006-11-02
I have recently reinstalled Ubuntu. I have two partitions for windows - one is a tiny partition made by Dell for recovery, next is the main Windows NTFS partition. During my Ubuntu install I created a FAT32 partition to be shared by both operating systems. Then the main Ubuntu partition and finally a swap partition. The problem is Windows won't let me use the shared FAT32 partition. Linux recognizes it just fine. When I go in to disk management in windows it is shown but the status is "Healthy (Unknown Partition)". The Linux partitions have the same status. Does anyone know what I can do for Windows to let me use this partition? Thanks in advance.

---

### Post by highneko on 2006-11-02
Windows? Why would you want that? >_>;;

---

### Post by carlos1 on 2006-11-02
Is the FAT partition located after the Linux partition on the disk, or before it (in terms of sequence)?

---

### Post by rocknrolf77 on 2006-11-02
You can mount it at startup if you check out [www.ubuntuguide.org](www.ubuntuguide.org) and search for fat

---

### Post by xghstst0riesx on 2006-11-02
Carlos1: before. The partitions go like this:
| dell | windows (ntfs) | share (fat32) | ubuntu (ext3) | swap |

I will try what rocknrolf suggested.

---

### Post by dark.developer on 2006-11-02
Hi there,
I thnk u might have made the FAT32 partition with a Linux LiveCD or something like that.

If the above is not the case then check whether the partition is really FAT32 and not FAT16 or simply FAT.

!!If I am still incorrect let me know we will sort it out

Bye,
Take Care.;) 

"Live and Let Live!!!"

---

### Post by Kateikyoushi on 2006-11-02
I would backup the data from that fat partition and make a new from windows, if you really want to use a partition to transfer data.
You could read and write you linux partition in case you use ext with this driver. [LINK]("http://www.fs-driver.org/")

---

### Post by xghstst0riesx on 2006-11-02
I created the partition with the Ubuntu live cd when installing it. It is Fat32. Both Windows and Linux say so. But only Linux let's me use it. It doesn't show up as a drive in Windows.

---

