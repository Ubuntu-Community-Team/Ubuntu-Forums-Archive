---
title: "What is the &quot;installation size&quot; option when installing in windows?"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by damonkashu on 2012-01-18
I bought a new 80 GB solid state drive for installing ubuntu onto, I am running windows 7 off my older SSD. When I run the installer in windows, and I select my 80GB drive, it gives me an option called "Installation Size" which ranges from 5GB to 30GB. What exactly does this mean, is it determining how much disk space that ubuntu will be allocated? If so, how come I can't get the full 80 GB?

---

### Post by raja.genupula on 2012-01-18
> **damonkashu said:**
> I bought a new 80 GB solid state drive for installing ubuntu onto, I am running windows 7 off my older SSD. When I run the installer in windows, and I select my 80GB drive, it gives me an option called "Installation Size" which ranges from 5GB to 30GB. What exactly does this mean, is it determining how much disk space that ubuntu will be allocated? If so, how come I can't get the full 80 GB?

you can give the size from 5 GB to 30 GB for selected partition and yes its asking you how much memory you wanna give for ubuntu installation . that 80GB is a single partition ? is that listed in the selection options ? 

I wanna give small suggestion that install Ubuntu directly on a separate partition for better performance .

---

### Post by coffeecat on 2012-01-18
> **damonkashu said:**
> it gives me an option called "Installation Size" which ranges from 5GB to 30GB. What exactly does this mean, is it determining how much disk space that ubuntu will be allocated? If so, how come I can't get the full 80 GB?

I thought the smallest size was 8GB, but anyway...

When you install Ubuntu through wubi, the installer creates a file called root.disk in the ubuntu\disks folder of the partition you are installing it to. If you were installing to the C: partition, the file would be C:\ubuntu\disks\root.disk. It sounds as though you are installing to your D: or E: (or whatever) partition, so the file would be D:\ubuntu\disks\root.disk (or E:, etc), and the size of the file is the size you are choosing. This file is used as a pseudo-partition and is itself formatted with a Linux filesystem for the Ubuntu system to be installed to.

As far as size is concerned, you probably don't need much more than about 12-16GB. The host partition (C:, D:, whichever it is) can be accessed read-write in /host from your wubi Ubuntu system, the advantage being that both Ubuntu and Windows will then have access to the files.

More on wubi here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2012-01-18
If you bought a dedicated drive for Ubuntu, then probably Wubi is not the right choice - it uses a "virtual drive" (a file containing an ext4 filesystem which is stored on the ntfs filesystem) which isn't as good performance as a direct install - and since you bought an SSD I would assume you want good performance.

So burn an Ubuntu CD or create an Ubuntu USB instead and install using that: [http://ubuntu.com/download/ubuntu/download](http://ubuntu.com/download/ubuntu/download)

---

