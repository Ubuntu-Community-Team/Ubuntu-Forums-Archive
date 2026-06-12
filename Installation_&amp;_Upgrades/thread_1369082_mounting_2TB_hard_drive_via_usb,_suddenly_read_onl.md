---
title: "mounting 2TB hard drive via usb, suddenly read only??"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by boandmichele on 2009-12-31
i bought a new 2 terabyte hdd for storage reasons, my current 750gb and 320gb drives are full up.  it is an internal drive, which i have hooked up currently by a usb dock.  

upon first getting it, i went into gparted and formatted it as ext4 (this is being done in 9.04 running ext3 btw)

i then proceeded to transfer 960gb to the drive over the next several hours.  this went smoothly (and slowly), but now i am having trouble with the last 300 gb.  it acts as if it is transferring just fine, but when i come back in an hour or two, it's thrown an error saying the file system is read-only, due to permissions problem.  it also appears to have come un-mounted.  

any ideas?  i feel like a simple fstab entry would fix it but i have no idea what that would be.  its currently mounted as /dev/sdd1, but i am afraid to try and move any files to it now :/

---

### Post by deadalus.globalnode on 2009-12-31
Have you tried copying it as root? Also where did you order this hd from?

---

### Post by CharlesA on 2009-12-31
Try mounting it with:

```
sudo mount -t ext3 /dev/device /mountpoint/goes/here -o rw
```

---

### Post by boandmichele on 2009-12-31
> **CharlesA said:**
> Try mounting it with:

```
sudo mount -t ext3 /dev/device /mountpoint/goes/here -o rw
```

that seems to have worked using
```
sudo mount -t ext4 /dev/sdd1 /media/2tb -o rw
```

im copying files now but i won't know for a few minutes if it is successful.  

deadalus, i ordered it from frys, and yes i tried copying as root and it still gives the same error, which is why this is so frustrating.

---

### Post by CharlesA on 2009-12-31
Looks good. Hope it works for you. :)

---

### Post by boandmichele on 2009-12-31
okay well it did it again.  i transferred a folder of about 70gb just fine.  but the next folder of 131gb stopped a third or so of the way through, and said 'cannot copy to 2tb, drive is read-only,' or something like that.  :(

---

