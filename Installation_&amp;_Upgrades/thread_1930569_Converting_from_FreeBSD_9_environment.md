---
title: "Converting from FreeBSD 9 environment"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by derekcentrico on 2012-02-23
Is it possible to have read/write mounted drives on Ubuntu 11.10?

I have 2.7TB of data on UFS drives.  I don't have extra drives to use to store the data while changing to ext4.

I'd like to have them mount automatically but I'm not sure if that would be possible either.

Thanks for any future help!

---

### Post by derekcentrico on 2012-02-27
Simply converted over but had to buy another HDD to hold data while I created EXT4 filesystems.

Mounting UFS is easy, but thought it best to convert to Linux partitions.

I'm writing a guide to build a complete media and file server with full VPN access...

---

### Post by ratcheer on 2012-02-27
> **derekcentrico said:**
> 
I'm writing a guide to build a complete media and file server with full VPN access...

Very cool!

Tim

---

### Post by derekcentrico on 2012-02-27
Thanks.  It's almost complete.  

Anyone curious about UFS to EXT, use this mounting procedure:
```
mount -r -t ufs -o ufstype=ufs2 /dev/<partition> <mount point>
```

Whereas I did:
```
mount -r -t ufs -o ufstype=ufs2 /dev/sdc1 /mnt/temporaryufsdrive/
```

Don't forget to create the mount-point directory first. mkdir.
```
mkdir /mnt/temporaryufsdrive/
```

Then, copy your data over to the new or holding harddrive.  I bought an extra 2TB for this purpose.

&&

As for the guide, I'm stuck on what I perceive is a routing problem with VPN.  I can access and manipulate the server's content via VPN no problem, but I cannot hit the LAN network.  I have a separate thread for this issue.  [http://ubuntuforums.org/showthread.php?t=1931610](http://ubuntuforums.org/showthread.php?t=1931610)

---

