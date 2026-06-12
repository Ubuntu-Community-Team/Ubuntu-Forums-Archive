---
title: "Ubuntu 16.04 not booting anymore after new motherboard"
date: 2017-05-19
forum: Installation &amp; Upgrades
---

### Post by bartvde2 on 2017-05-19
So today Dell replaced the motherboard in my XPS 13 Developer Edition, but after that it doesn't boot anymore. I get into the busybox prompt.
This is the info from boot repair disk: [http://paste.ubuntu.com/24603831/](http://paste.ubuntu.com/24603831/)

Anybody able to help? Dell is supposed to call me back but it can take several days.
Thanks in advance.

---

### Post by ajgreeny on 2017-05-19
The only disk showing in the disk-repair output is the 125.8GB sda with a fat32 partition only, and no Ubuntu installation is detected.

I assume that is a large USB drive with a live system on it but correct me if that is not the case.  If you are using a live system please also show us the output of ```
sudo parted -l
```

Was the old motherboard using BIOS and the new one UEFI?

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by bartvde2 on 2017-05-19
> **ajgreeny said:**
> The only disk showing in the disk-repair output is the 125.8GB sda with a fat32 partition only, and no Ubuntu installation is detected.

I assume that is a large USB drive with a live system on it but correct me if that is not the case.  If you are using a live system please also show us the output of ```
sudo parted -l
```

Was the old motherboard using BIOS and the new one UEFI?

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Yes indeed that is the USB stick from which I am booting. The new motherboard is using UEFI indeed, not sure what the old one was using to be honest, but I think the same.
sudo parted -l output in the live session only shows the USB drive as well.

---

### Post by bartvde2 on 2017-05-19
I got it resolved, had to change the disk in the BIOS from RAID to AHCI

---

