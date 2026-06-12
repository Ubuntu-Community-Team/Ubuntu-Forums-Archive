---
title: "Acomdata 2.5 usb no access help"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by leeley on 2007-06-05
I have a acomdata 2.5 usb harddrive and am trying to access the harddrive side of the thing now for 2 weeks. when I plug thing in it comes up as a cd (cdrom1) 25.4 gig writable, floppy 25.4 and flopp1 25.4 gig. When I go into fstab it does not show up what so ever, any ideas.

---

### Post by scott_g on 2007-06-05
What format is the drive in?  Fat32?  Ext3?  NTFS?

Scott

---

### Post by leeley on 2007-06-06
> **scott_g said:**
> What format is the drive in?  Fat32?  Ext3?  NTFS?

Scott

I don,t know seeing that I can not get into it

---

### Post by scott_g on 2007-06-06
> **leeley said:**
> I don,t know seeing that I can not get into it

Can you try a (in a terminal):

```

fdisk -l

```

and see if the hard drive is listed?

also, can you see if you can see the hard drive on a windows computer?

Thanks,
Scott

---

### Post by leeley on 2007-06-06
> **scott_g said:**
> Can you try a (in a terminal):

```

fdisk -l

```

and see if the hard drive is listed?

also, can you see if you can see the hard drive on a windows computer?

Thanks,
Scott
here it is
sudo fdisk -l
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          65      522081   83  Linux
/dev/hda2              66         256     1534207+  82  Linux swap / Solaris
/dev/hda3             257        4081    30724312+  83  Linux
/dev/hda4            4082       19457   123507720    5  Extended
/dev/hda5            4082        9945    47102548+  83  Linux
/dev/hda6            9946       15809    47102548+  83  Linux
/dev/hda7           15810       19457    29302528+  83  Linux

Disk /dev/hdb: 30.7 GB, 30736613376 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3736    30009388+  83  Linux

---

### Post by scott_g on 2007-06-06
Try typing the following into the terminal:

```

sudo mkdir /media/usbhd
sudo mount -t ext3 /dev/hdb1 /media/usbhd

```

or a variation; I'm guessing its an ext3, as the fdisk states its a 83 linux partition (the same as the rest of your partitions)

Scott

---

### Post by leeley on 2007-06-17
Thanks guys got it working after using a friends XP (ouch) but it is worhing just fine.  had ti use XP to set it writable as it comes read only:p

---

### Post by kamiccolo291 on 2007-06-26
I am having the same problem with my Acomdata External HD. How did you use XP to make the drive writable?

---

