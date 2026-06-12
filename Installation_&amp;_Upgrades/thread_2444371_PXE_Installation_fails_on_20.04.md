---
title: "PXE Installation fails on 20.04"
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by vatuu on 2020-05-29
So, I've been trying to set up a PXE server to quickly set up laptops and whatever without having to shuffle USB sticks and disks around all the time.
Plenty of Linux Distros and even Windows is on there. However, Ubuntu 20.04, regardless of Server or Desktop always fail to boot without exception.
Ubuntu 18.04 works just fine, but with 20.04 I am always greeted with "Unable to find a live file system on the network", and a dead boot process.

I am using a NFS share to hold the installation image and I have confirmed that it is authenticated and mounted to /cdrom before failing the boot.

In regards of the pxe boot script, that'd be this: 
```

label ubuntus2004
   menu label ^6) Install Ubuntu Server 20.04 LTS
  kernel images/ubuntus2004/vmlinuz
  initrd images/ubuntus2004/initrd
  append root=/dev/nfs ip=dhcp boot=casper netboot=nfs nfsroot=X:/netboot/nfs/ubuntus2004/ splash ---
```

I've been tearing my hairs out about this for over 2 weeks now, so any help is apprechiated.
Best regards, Nicolas

---

### Post by vatuu on 2020-06-04
Bump?

---

### Post by tribouth on 2020-06-05
Hi,

I experience exactly he same, last (of today) Ubuntu Server 2004 doesn't boot on pxe with the same error "Unable to find a live file system on the network".
The weird is that with an image of Ubuntu Desktop Beta 2004 it work find.

My config works perfectly with an image of Ubuntu Desktop/Server 1804.

Any idea?

---

### Post by tribouth on 2020-06-05
Ok I found the solution thanks to [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1877618](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1877618)
I missed to copy the .disk folder to my tftpboot directory.

Don't forget to run cp -rp * and cp -rp .disk /path-to-tftpboot/ubuntu-2004-folder

Regards

---

