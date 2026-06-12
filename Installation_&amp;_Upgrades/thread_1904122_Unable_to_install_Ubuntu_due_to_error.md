---
title: "Unable to install Ubuntu due to error"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by meetdilip on 2012-01-04
Hi, I downloaded the latest Ubuntu and about to install it. I inserted the disc, booted from cd and chose install alongside windows.

It now shows a table with 6 partitions in my hdd namely

/dev/sd1 fat16 size 41 MB, used 33 MB
/dev/sda2 ntfs size 5368 MB used 1074 MB
/dev/sda3 ntfs size 42949 MB used 36211 Mb
/dev/sda5 ntfs size 42949 MB used 91 Mb
/dev/sda6 ntfs  size 107374 MB used 47087 Mb
/devsda7 nts size 301409 MB used 48760 MB

I want use 

/dev/sda5 ntfs size 42949 MB used 91 Mb

for Ubuntu which I selected and clicked **Install Now** button. But it shows 

> No root file system is defined

Please correct this from the partitioning menu.

Device fro boot loader installation : 

is given as  /dev/sda ATA SAMSUNG HM500JJ (500.1 GB)

Please tell me hwo to proceed further.

Thanks

---

### Post by 73ckn797 on 2012-01-04
You have to designate whether the partition will be "/" which is the root partition designation. That is found when in the partitioner of the installation process. Say if you also created another partition or wanted to use another one for /home, which would be to store your files and such, you would designate that also.

---

### Post by Raghav_K on 2012-01-04
hey... ideally you should define 3 partitions when installing linux...

a

/home      - home partition which has your documents and stuff
/          - root partition
/swap      - swap partition.. though its not needed usually if you have ram > 4 gb..

so you make a gparted disc, boot from it... delete your sda5, and of the 42 gb odd free space, create a root partition of 20gb and home with 22gb, ext4 partitions... apply changes.. restart.. install ;)

have fun dilip.. saw ur fb messages jus now...

---

### Post by oldos2er on 2012-01-04
Moved to Installation & Upgrades

---

