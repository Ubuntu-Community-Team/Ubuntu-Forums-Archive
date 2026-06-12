---
title: "Upgrade to Ubuntu 8.04 from Ubuntu 7.10 lost extra hard drives"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by ali_williams on 2008-09-10
hey guys,

I just did the upgrade to 8.04 but after the upgrade i lost my 3 other hard drives. Its so weird when i got to my /etc/fstab it reads this

/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/hda1                                  /media/hda1    ext3         defaults                    0  0  
/dev/hdb1                                  /media/hdb1    ext3         defaults                    0  0  

when i go into my media folder i still have the mount points. But for some reason when i log into the box it doesnt auto mount those shares anymore. When i do a 
#sudo mount -a

it says this
mount: special device /dev/hda1 does not exist
mount: special device /dev/hdb1 does not exist

but all i did was upgrade the os i didnt change anything inside the machine. So the question is how do i find out what they changed to so I can update my fstab?

---

### Post by bullium on 2008-09-10
Which drives are visible when list your disks with fdisk? 
```
$sudo fidsk -l
```

---

### Post by ali_williams on 2008-09-10
> **bullium said:**
> Which drives are visible when list your disks with fdisk? 
```
$sudo fidsk -l
```

thanks that fixed it after running that I see that they changed to

/dev/sdd1  
/dev/scd1  

after i changed the fstab then did a mount -a i was good thanks again :D

---

