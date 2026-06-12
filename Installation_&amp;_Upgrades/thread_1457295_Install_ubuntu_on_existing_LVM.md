---
title: "Install ubuntu on existing LVM"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by amksep on 2010-04-18
I am planning to install 10.4 when it arrives. And am not going to upgrade because i upgraded from 9.04 to 9.10 so now i need to refresh the system.

But I have all my partitions except root using lvm2 logical volumes.

My question is : What is the safest procedure to install 10.4 on an existing lvm2 without losing my files/partitions 

thank you all.

---

### Post by tom4everitt on 2010-04-18
I have no particular experience working with LVM:s, but assuming its not significantly different to normal partitions, the best way would be this:

In the install procedure, choose manual partition layout, and be very careful with which partitions you mark for formatting. Apart from that, it is just to assign the desired mount points to the different partitions. 

And of course you should keep an backup of all the data just in case.

---

### Post by amksep on 2010-04-30
I have done the installation successfully and wanted to share my experience here :

I booted the Live CD and selected to try without installation.

The installation differs from the normal method at two steps.

The first is installing lvm2 package before the install : open a terminal and type : sudo apt-get install lvm2

Then I started the installation , the partitions appeared and i choose the mount points.

The second step is to install the lvm2 package in the new installed system:

open a terminal and mount the new root partition at a certain mount point called target : create the directory if not exist:

mkdir /target
mount /dev/your_new_root_partition /target
chroot /target
mount -t proc proc /proc
mount -t sysfs sys /sys

then 
apt-get install lvm2
shutdown -r now

that is it!.

---

### Post by ivanmacx on 2012-08-08
I know this is an old thread but it comes up top in Google when searching for this problem.  Just to add a further detail, I did what was described by amksep above, but before the Ubuntu installer disk would detect the LVM partitions I had to activate the existing volume group.  Hence start up the live installer disk, open a terminal and then:

```
sudo -s
apt-get install lvm2
vgscan

    Reading all physical volumes.  This may take a while...
    Found volume group "vg1" using metadata type lvm2

vgchange -ay vg1

```Change the name of the volume group from "vg1" to whatever yours is detected as.

After that the installer should detect the logical volumes and let you install onto them.

---

