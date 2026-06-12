---
title: "Feisty boo boos"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by jack_teagarden on 2007-04-21
Help me please!!!

My box was running Edgy Eft, and I upgraded to Feisty.
Along the way, about halfway through the install, the computer spontaneously rebooted.
Now that the install didn't work, I can't boot that drive.

Okay. The drive that is messed up is "sda1", 75 gig 7800RPM Maxtor drive, and I have a another drive with Ubuntu I am using now, which is "hdd1", 18 gig Western Digital Drive.
When I try to mount /dev/sda1 my box says something about it being LVM_2, and I can't mount it
I looked it up, and the place where Gnome Partition Editor says it is mounted is blank.

Any questions, comments?

---

### Post by taurus on 2007-04-21
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by jack_teagarden on 2007-04-21
root@THOR:/home/jordan# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9349    75095811   83  Linux
/dev/sda2            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2330    18715693+  83  Linux
/dev/hdd2            2331        2434      835380    5  Extended
/dev/hdd5            2331        2434      835348+  82  Linux swap / Solaris

---

### Post by taurus on 2007-04-21
Try something like

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```

---

### Post by jack_teagarden on 2007-04-21
Thanks!
It worked! I feel kind of inept, but it'll pass.
Thanks a lot for going out of your way to help me!!

---

