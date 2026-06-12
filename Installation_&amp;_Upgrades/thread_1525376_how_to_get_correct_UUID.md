---
title: "how to get correct UUID?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by mosaik on 2010-07-06
After doing the proposed security updates (re)booting stalls with a message like:
One or more mounts listed in /etc/fstab cannot be mounted yet
/home: waiting for UUID ...

In the escape shell I can see from /etc/fstab that /home was mounted to /dev/sda6. But when calling blkid this device is missing.

Trying to mount /home I get the error:
mount: special device UUID=... does not exist.

In other threads I have read that the UUID-entry for /home in /etc/fstab has to be corrected. But how do I get the correct UUID? Will making a live-CD, booting from it and then calling blkid give me the UUID for /dev/sda6?

thanks,

Wolfgang

---

### Post by oldfred on 2010-07-06
Yes

Normally in your install. 

sudo blkid

---

### Post by drdos2006 on 2010-07-06
You could also list the drives from the terminal:
ls -l /dev/disk/by-uuid

regards

---

### Post by mosaik on 2010-07-06
In the escape-shell ls -l /dev/disk/by-uuid again only lists sda1|3|5 but not sda6 ..
I hope the live-CD will help ..

thanks,
Wolfgang

---

### Post by mosaik on 2010-07-16
The live CD did not help nor was it acutally needed.
All that I needed was to manually mount the /home partition in the escape-shell, in my case:
```

mount -t ext3 /dev/sda6 /home

```
The details for this command I could find with simply typing the following in the escape-shell:
```

cat /etc/fstab

```
After two such boots my system started booting normally again ...

Wolfgang

---

