---
title: "RAID MD devices out of order"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by thesheff17 on 2008-03-20
I have installed ubuntu 6.06 LTS on a box with two scsi drives so this is the layout:

md0 -> /boot/
md1 -> swap
md2 -> /

I have added a sata card and drives and created a new raid 5 like this

mdadm --create /dev/md3 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

I even do mdadm --scan --detail > /etc/mdadm/mdadm.conf

When I reboot the server for some reason the assignment of the mdX is completely out of order 

The /dev/md3 device is actually be assigned to /dev/md0 instead on reboot?

Of course the system hangs because the assignments of the mdX devices and enters the busybox prompt.

Why is this doing this?  Thanks in advance.

---

### Post by mrsteveman1 on 2008-03-20
Are these numbers supposed to remain static? I mean, i know when you change almost any drive config on some linux boxes the device numbers change all over the place.

If the problem is filesystem mounting you can use the UUID for the filesystem instead of the mdraid device as long as the system has udev (does 6.06 have udev?)

---

### Post by thesheff17 on 2008-03-20
I know the drives change when you add them but this is what I did:

installed the os with the 2 scsi drives - works fine
attached the sata card and boot ubuntu again - works fine

now I have all the drives present in the os with no issues.  It isn't until I create the array of the 4 drives that somehow ubuntu thinks it should be pointed at /dev/md0 even though I pointed it at /dev/md3

I could actually boot a knoppix cd and format all the drives in the raid a 5 and the system would boot fine again.  It something to do with the mdadm and how ubuntu understands the mdX devices.

I used to have Gentoo linux on this box and it worked fine.  Anyone really good with mdadm?

---

