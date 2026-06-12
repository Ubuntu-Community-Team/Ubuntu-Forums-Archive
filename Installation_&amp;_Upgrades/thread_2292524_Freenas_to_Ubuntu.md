---
title: "Freenas to Ubuntu"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by mirdragon on 2015-08-28
Hi,

I currently have a freenas setup running from a 16GB USB 3.0 stick and am looking to switch to Ubuntu.

The reason for the switch is because I want to be able to use VM's a lot more (moving away from desktop pc's and using tablets) and Freenas has problems implementing them, plus some features of Plex are not supported on Freenas and I can't use the standard updates for it.

My drives are all currently using ZFS and would like to know if Ubuntu can now fully read ZFS to make it easier for migrating or will I need to do what needed to be done years ago and copy data from ZFS to EXT4 and then wipe ZFS as EXT4 and process the next drive until done.

Can Ubuntu be easily installed to a USB stick these days as I want to leave my internal SATA ports for Hard Drives that will be holding data, or will I need to install an internal drive (if so it will be an SSD which I have spare)

thanks

---

### Post by TheFu on 2015-08-28
[https://launchpad.net/~zfs-native/+archive/ubuntu/stable](https://launchpad.net/~zfs-native/+archive/ubuntu/stable)

Don't know anything else you asked about. Sorry.

---

### Post by lukeiamyourfather on 2015-09-09
> **mirdragon said:**
> My drives are all currently using ZFS and would like to know if Ubuntu can now fully read ZFS to make it easier for migrating or will I need to do what needed to be done years ago and copy data from ZFS to EXT4 and then wipe ZFS as EXT4 and process the next drive until done.

Yes. Use the PPA in the post above. That's for the kernel port of ZFS which is much faster than the old FUSE implementation. It's one of the participants of OpenZFS which aims to port features between platforms and make ZFS more or less the same on various platforms.

```
sudo add-apt-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get install ubuntu-zfs
```

Once installed you can import your pools. Typically the pool is called tank but your's might be something different. Just run the command without a pool name to check for all possible pools to import. The drive labels can be different things like /dev/disk/by-id if you want.

```
sudo zpool import -d /dev/disk/by-id tank
```

> **mirdragon said:**
> Can Ubuntu be easily installed to a USB stick these days as I want to leave my internal SATA ports for Hard Drives that will be holding data, or will I need to install an internal drive (if so it will be an SSD which I have spare)

Yes, but I wouldn't recommend doing that. Unlike FreeNAS, Ubuntu isn't optimized for install on a USB flash drive. I'd go with the SSD if you already have one. If the machine has PCI Express you can add more SATA ports easily and for pretty cheap. I use a AOC-SAS2LP-MV8 which is about $120 and has 8 SAS ports (IT mode so ZFS friendly).

---

### Post by TheFu on 2015-09-09
a) thanks for the model of a 8-port card. I've been looking at LSI for $350+. 
b) Newegg has the card for $110.
c) a 1-port SAS to 4-port cable is needed?  Yes?
d) Is that card, AOC-SAS2LP-MV8, recognized automatically by the Linux kernel? To me, that is easily worth $200. [http://ubuntuforums.org/showthread.php?t=1255535](http://ubuntuforums.org/showthread.php?t=1255535) is not encouraging.

Very helpful stuff.

---

### Post by lukeiamyourfather on 2015-09-09
If you don't need hardware RAID and just a HBA then the Marvell chipset is perfect for the job. Don't get me wrong, LSI is great and I use them at work but the price is a factor at home. Yes, cables will be needed because it doesn't come with them. I found these to be a great value and they work perfectly (assuming straight to the drives with no backplane).

[http://www.amazon.com/gp/product/B001L9DU88](http://www.amazon.com/gp/product/B001L9DU88)

Yes, the driver for the AOC-SAS2LP-MV8 is in the kernel and recognized out of the box by Ubuntu 14.04 LTS and also CentOS 7. Maybe others but those are the only distributions I've tried it with.

---

### Post by TheFu on 2015-09-09
Golf clap - added to my wishlist for the next order.  Typical throughput?  With single drives, I'm seeing just under 80Mbps here.  With softwareRAID, mdadm, it is much lower.  Would like to get into the 100+Mbps per device and have it scale linearly ... almost as more drives/stripes are added.

---

### Post by lukeiamyourfather on 2015-09-09
Sorry to the original poster, we've thoroughly hijacked this thread. With 8 drives in a VDEV with RAID Z3 and an older host (circa 2006) I'm getting between 200MB/s and 250MB/s throughput for asynchronous writes and sequential reads. That's with the AOC-SAS2LP-MV8 controller which is my machine at home.

At work with a LSI 3008 based controller with 6 drives in a VDEV with RAID Z2 and 6 total VDEV I'm getting 2,000MB/s and beyond so ZFS on Linux scales very well. Both of these are with LZ4 compression enabled and otherwise unmodified configurations. It's maybe not the best performance out there compared to high end hardware RAID controllers but it's pretty good or at least good enough for my uses, plus all the benefits that come with ZFS. Either way it's better performance than software RAID on Linux. The one gotcha is ECC memory.

---

### Post by iulian X on 2015-09-10
> **mirdragon said:**
> Hi,

I currently have a freenas setup running from a 16GB USB 3.0 stick and am looking to switch to Ubuntu.

The reason for the switch is because I want to be able to use VM's a lot more (moving away from desktop pc's and using tablets) and Freenas has problems implementing them, plus some features of Plex are not supported on Freenas and I can't use the standard updates for it.

Have you tried Open Mediavault?

Its a distro made for NAS based on Debian .

---

### Post by lukeiamyourfather on 2015-09-10
> **iulian X said:**
> Have you tried Open Mediavault?

That's a decent option for a NAS but that doesn't meet the goals of the original poster. They're looking for more of a fully featured server than a NAS (hence moving away from FreeNAS). It also doesn't support ZFS which is what the existing drives are.

---

