---
title: "upgrade through another partition"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by Black Kelpie on 2010-09-06
Is it possible to upgrade Ubuntu when I'm in different partition (which also has Linux)?
I.e. can I use the terminal (in partition A) to change the directory to where I want to go (partition B), and apply any terminal command in the Linux version which is in that partition (B)?

---

### Post by garvinrick4 on 2010-09-06
Yes if you have two linux partitions you can mount the other one.
You use the chroot command and it puts you in root of that partition
and you can update && upgrade.

---

### Post by Black Kelpie on 2010-09-06
Thank you for this speedy reply. Could you please elaborate somewhat on this chroot command which allows me to update and upgrade and uhm..yes..repair.

---

### Post by kansasnoob on 2010-09-06
The following link describes how I mount and chroot an inoperative Linux OS:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Just be certain you properly identify the partition you wish to mount. I quite often use some older Debian based Live CD or Puppy and they sometimes still use the drive designation "hd" rather than "sd" :)

---

### Post by garvinrick4 on 2010-09-06
You have to make a directory for partition.
you have to mount partition
you have to get internet connection copy it over.
you have to get into root
then you can apt-get update && apt-get upgrade
or run a fsck to check file system
I attached a pdf file that tells you about commands. Opps wrong file.

---

### Post by Black Kelpie on 2010-09-06
Thank you
I can mount partition A in partition B (using a GUi in this case) and change into that partition. 
However, does a command like sudo apt-get dist-upgrade then not apply to partition B..?

---

### Post by garvinrick4 on 2010-09-06
> **Black Kelpie said:**
> Thank you
I can mount partition A in partition B (using a GUi in this case) and change into that partition. 
However, does a command like sudo apt-get dist-upgrade then not apply to partition B..? I have never tried to update && upgrade while in root in nautilus using GUI.
Seems risky at best. I would say learn to mount and chroot into in terminal so as not
to make a mess. If you can give me your sda # you want to mount and it's label that you
gave it or give it one. I will then give you commands to chroot into and update && upgrade from another Linux install or live cd.

---

### Post by Black Kelpie on 2010-09-06
here's part of the output which I got from using mount | column -t

/dev/sda2         on  /media/CHOOKS                                type  fuseblk                (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

/dev/sda5         on  /media/038639fc-0eea-47f8-948d-328011e50cd0  type  ext3                   (rw,nosuid,nodev,uhelper=udisks)

/dev/sdb1         on  /media/VACUUMBAG                             type  ext2                   (rw,nosuid,nodev,uhelper=udisks)

The partition we need in on  /media/038639fc-0eea-47f8-948d-328011e50cd0 so sda# would be sda5.

---

### Post by garvinrick4 on 2010-09-07
Label your sda5 lets say jaunty in gparted of live cd.
Given you have internet connection in Live CD.

```
sudo mkdir /media/jaunty
```
```
sudo mount /dev/sda5 /media/jaunty
```
```
sudo cp /etc/resolv.conf /media/jaunty/etc/resolv.conf
```
```
sudo chroot /media/jaunty
```
```
apt-get update 
```
```
apt-get upgrade
```
```
ctrl/d
```
```
sudo umount /media/jaunty
```
```
exit
```

You can use this in live CD or another ubuntu install
1. make a directory
2. mount partition
3. get internet connection copied to partition
4. get into root
5. update
6. upgrade
7. get out of root
8. unmount partition
9. exit terminal

---

