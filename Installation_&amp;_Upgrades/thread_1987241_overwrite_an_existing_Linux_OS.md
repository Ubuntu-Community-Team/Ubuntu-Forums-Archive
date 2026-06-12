---
title: "overwrite an existing Linux OS?"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by domis4 on 2012-05-26
Hello everyone,

i have two Operating systems on my Notebook, Windows 7 and an older Linux distro of Linux mint.

Well, i decidet to delete Linux Mint and install Ubuntu 12.04 on it. Unfortunatelly, i dont now how :(

i installed Grub boot loader into the MBR

---

### Post by carl4926 on 2012-05-26
Boot the ubuntu cd and start the installation
When you get here: choose something else
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/4_install_custom.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/4_install_custom.jpeg)

From here you can select the partitions manually to overwrite Mint

---

### Post by domis4 on 2012-05-26
well, at that point, i get stuck. 

/dev/sda6 is my linux mint partition
/dev/sda7 is the swap

how do i set flags, and which i should^^

thanks for the fast reply

this is the partition table
[http://www10.pic-upload.de/26.05.12/cbc9pw9o2atg.png](http://www10.pic-upload.de/26.05.12/cbc9pw9o2atg.png)



EDIT: I got it, just put a "\" for the root point

---

### Post by ajgreeny on 2012-05-26
> **domis4 said:**
> EDIT: I got it, just put a "\" for the root point
Well, almost correct!

It is "/" not "\" for root.

---

### Post by fantab on 2012-05-26
> **domis4 said:**
> well, at that point, i get stuck. 

/dev/sda6 is my linux mint partition
/dev/sda7 is the swap

how do i set flags, and which i should^^

thanks for the fast reply

this is the partition table
[http://www10.pic-upload.de/26.05.12/cbc9pw9o2atg.png](http://www10.pic-upload.de/26.05.12/cbc9pw9o2atg.png)



EDIT: I got it, just put a "\" for the root point

When you are manually allocating drive space- select /dev/sda6 and choose CHANGE/Edit, choose to format, choose your filesystem, ext4 and mountpoint.

Don't do anything with SWAP just leave it... Ubuntu will identify it as SWAP and use it. 

On the same dialog box choose to install Grub to /dev/sda only and not to /dev/sda3 or /dev/sda2.

---

