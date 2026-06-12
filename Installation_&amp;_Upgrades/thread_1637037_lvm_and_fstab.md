---
title: "lvm and fstab"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by d_morgan on 2010-12-03
What should I have in fstab to mount /var and /home to logical volumes on my 2nd hard disk (/dev/sdb)?
I currently have

```
 /etc/fstab
proc  /proc  proc  nodev,noexec,nosuid  0  0
UUID=7bfa90f4-5840-48b1-9668-e8f00d6f2a5a  /  ext4  errors=remount-ro 0  1
/dev/mapper/vg1-var  /var  ext4  defaults  0  1
/dev/mapper/vg1-home  /home  ext4  defaults  0  1
UUID=0c5e45ba-3cd8-4b4e-a7f4-e32ab657a666  none  swap  sw  0  0
```

The system boots but I get a ureadahead error.  Plus I have two /var and /home directories. One mounted to /dev/sda and one on the lvm on /dev/sdb.  If I boot with a live usb stick I can go look at the var directory on /dev/sda.  If i delete the /var dir on /dev/sda the system won't boot anymore.


**Back-ground and more info**
I started with a single 80GB hard drive and installed ubuntu server 10.04.  I selected LAMP server, samba file server, and mythbuntu master back-end during the install.  One side note, I was a surprise to find out that mythbuntu backend includes xfce desktop since it I didn't want this option.  After the installation I setup myth and was happy with it so it was time to add storage so I added a 750GB hard drive to the system.

Now I had /dev/sda with / and a swap space mounted to it.  I wanted to have /var and /home mounted on the new 750GB drive on two logical volumes labeled home and var.

I've created the lvm setup using the following guide [http://www.linux.com/learn/tutorials/306352:weekend-project-migrate-from-direct-partitions-to-lvm-volumes]("http://www.linux.com/learn/tutorials/306352:weekend-project-migrate-from-direct-partitions-to-lvm-volumes")

The system boots but gives ureadahead errors and I can't delete the var and home directories off the original drive without causing problems.

---

