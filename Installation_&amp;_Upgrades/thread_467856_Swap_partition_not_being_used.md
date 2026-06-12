---
title: "Swap partition not being used?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Sloddy Shipper on 2007-06-08
Hi, can anyone tell me how to ensure my swap partition is being used? Everything got super slow on a couple of occasions and i find my swap partition is not in use-

free -m
             total       used       free     shared    buffers     cached
Mem:           503        497          6          0         10        191
-/+ buffers/cache:        295        208
Swap:            0          0          0

Swap 0 of 0 in use, well i have a 1gb swap partition. I have 512mb RAM and the swap previously showed a small amount of usage. Here is the entry in /etc/fstab-

# /dev/hda5
UUID=9f775d42-d82c-4c57-adfb-e55625e56283 none            swap    sw              0       0

I gather some people had issues with partitions with the recent kernel update. I didn't notice anything at the time but perhaps this is the cause. Anyway, hopefully someone can help me out here.

---

### Post by Stephen Howard on 2007-06-08
Hmm, what does this command display:

```
swapon -s
```

Also, try the following command sequence and report the output :

```
swapoff -av   (you may need to sudo this)
swapon -av
swapon -s
```

---

### Post by AnRa on 2007-06-08
Type "blkid" in a console and see if the UUIDs are the same.

---

### Post by Sloddy Shipper on 2007-06-08
Hi, thanks for the reply, here we are - 

$swapon -s
 Filename                                Type            Size    Used    Priority

nuthin

$ sudo swapoff -av
 Password:
 swapoff on UUID=9f775d42-d82c-4c57-adfb-e55625e56283
$ sudo swapon -av
 swapon on /dev/disk/by-uuid/9f775d42-d82c-4c57-adfb-e55625e56283
 swapon: cannot stat /dev/disk/by-uuid/9f775d42-d82c-4c57-adfb-e55625e56283: No such file    or directory
$ sudo swapon -s
 Filename                                Type            Size    Used    Priority
 
Ok looking in /dev/dik/by-uuid i see that hda5 has a different uuid from the one in /etc/fstab. If i just edit /etc/fstab then

swapon-a

should my swap partition be back in use?

---

### Post by Stephen Howard on 2007-06-08
...worth a try!

---

### Post by Stephen Howard on 2007-06-08
UUID - guaranteed to screw up almost every time.

Not only is UUID the most ill thought-out addition to Ubuntu ever, its also ugly.

...sorry, my pet peeve.

---

### Post by Sloddy Shipper on 2007-06-08
That did the trick, thankyou both. I'm guessing it was the kernel update that messed this up. To guess more - i imagine UUID is supposed to uniquely identify a partition even if the device file or other set up is changed. A new kernel disagrees about this identifier with the old one but doesn't update all relevant configuration. Lucky for me my root filesystem partition was unaffected. I think this may have happened to a bunch of people. Enough guessing. Thanks again.

---

### Post by mr_ed on 2007-06-15
> **Stephen Howard said:**
> UUID - guaranteed to screw up almost every time.

Not only is UUID the most ill thought-out addition to Ubuntu ever, its also ugly.


Agreed.  I've lost my swap on about 5 separate occasions.

---

