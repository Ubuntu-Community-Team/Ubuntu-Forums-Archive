---
title: "install problems"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by dog-soldier on 2012-08-22
i have a ibm laptop and i just put a 100 gig hdd in it. im unable to install Ubuntu 11.04 cause it says i only have 690 mb of space. 
how can i fix this? 
this is not a new hdd, its a used one

---

### Post by darkod on 2012-08-22
First of all, are you sure you want to install 11.04? The support ends in two months and it will be unsupported after that.

As for the hdd, boot with the cd in live mode, open terminal and check the hdd partitions with:
```
sudo fdisk -l
sudo parted -l
```

Post the results so we can have a look.

It might be that only 690MB are left as unallocated and all the rest belongs to partitions. The installer will not delete partitions for you because that can mean data loss. You have to do it yourself. Lets see what the above commands give for your partitions.

---

### Post by dog-soldier on 2012-08-22
when i run
```
sudo fdisk -l
```
i get nothing

when i run 
```
sudo parted -l
```

i get 
```
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label   
```

---

### Post by dog-soldier on 2012-08-22
this also came up

```
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.
Error: /dev/fd0: unrecognised disk label  
```

---

### Post by darkod on 2012-08-22
fd0 is usually a floppy and sr0 a cd-rom drive. You can ignore those.

The hdd doesn't seem to be recognized by ubuntu. If you are sure it's working, maybe the controller is not recognized, which is rare with linux but it does happen.

Is the hdd recognized correctly in BIOS?

---

### Post by dog-soldier on 2012-08-22
no its not

---

### Post by darkod on 2012-08-22
There you go. Until it shows up in BIOS correctly, it's like it's not there. You need to sort that out first, I think the installer will work just fine afterwards.

---

### Post by dog-soldier on 2012-08-22
what would cause that?
i have never ran into this before

---

### Post by darkod on 2012-08-22
Hard to say. Maybe the bios doesn't autodetect it and you have to select some option to detect the new hdd.
Double check whether the connection is good, if it's sata that it slots into the connector nicely. If it's ide make sure no pins are bent, etc.

That's basically it. On the hardware side double check the connection, on the software side look into the bios options. Refer to a manual for the bios if you have one, if all else fails try googling the machine model and this problem of not detecting the new hdd.

Are you 100% sure the disk works? It doesn't hurt trying it into another machine or a hdd case just to make sure, etc.

---

