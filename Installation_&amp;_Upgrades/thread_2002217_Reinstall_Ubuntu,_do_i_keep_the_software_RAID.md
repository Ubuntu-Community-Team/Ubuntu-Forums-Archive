---
title: "Reinstall Ubuntu, do i keep the software RAID?"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by stefve on 2012-06-12
Hi

I'm running ubuntu desktop on a hard disk. In the same computer, I have 4 other disks with a software RAID 5 running (using mdadm).
I want to reinstall my OS, but after the reinstall, can I just mount the raid back when i installed mdadm?

Thanks in advance!

---

### Post by darkod on 2012-06-12
Yes, if the OS is not on the array, you can install the OS first and then assemble and mount the array.

Just make sure you use the --assemble option to assemble existing array, and NOT the --create option which creates new blank array (your data is gone).

To autodetect everything, it would be like:
sudo mdadm --assemble --scan

That will scan the disks and assemble all working md devices. After that you would need to make an entry in /etc/fstab if you want it to automount at boot.

---

### Post by stefve on 2012-06-12
Thanks darkod!

The OS is not on the array, it's located on another disk.
Because i have no important data on the raid on this moment i will test it sudo mdadm --assemble --scan.

Thanks again!

---

### Post by steeldriver on 2012-06-12
I recently added RAID to a prior install just like you describe - the only thing that went wrong for me is I forgot to append the newly assembled array details to the mdadm.conf file and update initramfs - after that it would boot and mount the array OK but kept coming up as a different device (e.g. /dev/md127 instead of the original /dev/md0)

```
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf

sudo update-initramfs -u
```I *think* that's because mdadm re-scans on boot and attempts to auto assemble any 'unknown' arrays using the RAID superblock info - but I'm no expert on these things.

---

### Post by stefve on 2012-06-12
Thanks Steeldriver!

At this moment, i have this in my mdadm.conf:

DEVICE /dev/sdb /dev/sdd /dev/sdc
ARRAY /dev/md0 level=raid5 devices=/dev/sdb1,/dev/sdd1,/dev/sdc1,/dev/sde1

So if i place those 2 lines in my new configuration, it should also work? (if the discs get the same letters)

---

### Post by steeldriver on 2012-06-12
hmm... I don't know... personally I would let mdadm generate that info and just append the output as described above 

that way it's sure to be in the format that the currently installed mdadm version is expecting - for me, it generates the device info in UUID form for example - I don't think you should rely on the /dev/sdXn device designators remaining the same

---

