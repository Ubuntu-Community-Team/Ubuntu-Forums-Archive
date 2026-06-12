---
title: "Raid 1 Swap Issues"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by gmoreno on 2012-12-31
Hello,

I'm returning back from Debian.  I have two 1TB drives and will only have Ubuntu installed.  I've chosen server edition for better raid support.

Upon install it showed two 15.3GB raid partions and two physical 15.3GB partitions.  I though it was and it should have only shown one 15.3 raid partition.  I went a head and set both 15.3 partitions as swap since I have 8gb of ram.

Now at boot up it gives me an error and throws me into busy box.  How can I fix this?

TIA

gmoreno

---

### Post by Gone fishing on 2012-12-31
I'm assuming that you are using a mdadm software raid 1 (mirrored). If so I think you should have seen only 1 15.3GB raid partion. I would think that you need to remove the swap and extra raid device from fstab so the system boots. Then make sure swap is off using sudo swapoff -a. Then stop and rebuild the raid device by removing then adding the physical partitions have a look at this its old but looks helpful [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Do you need the swap on a mirrored raid? Presumably there is a performance hit - with out the swap on the raid the system may crash if a drive fails but should be bootable and fixable.

---

### Post by gmoreno on 2013-01-02
Yes, I would prefer raid 1/mirrored swap if it improves performance.  How would I fix it then.

---

### Post by Gone fishing on 2013-01-03
No I would say running a swap on a mirrored raid will reduce perforance as data will need to be written to 2 disks.

The advantage would be without it if a disk failed and the swap partition was being used the system would crash without the raid on swap (However it would restart OK). With the raid the system would keep going. Having said that I had a server without the swap on the raid and a disk died and the box just carried on until I stopped it to replace the bad drive.

To fix the problem I would remove the raid device from fstab so the system starts. Then I would remove and then re-add the physical partitions to the raid device as in the bottom of the link I posted. Once the raid is built and working add it to fstab.

---

### Post by darkod on 2013-01-03
It would have been helpful to post the error it throws you. It actually might tell you what is bothering it.

As mentioned, you can try commenting out the swap entry in fstab. To see if it will boot without it. There should not have been two raid devices of the same size, unless you created them. And if you are sure they were raid devices, not one raid device and one partition on it.

You can use the ubuntu live cd to look into the system and try to fix it, but don't forget that the live session doesn't have mdadm included. So first install it and assemble the arrays:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

After that you can check the devices with parted. Post the output so we can see it too:
```
sudo parted -l (small L)
```

If you decide to comment out the swap in fstab, you will have to mount the root md device to some temp mount like /mnt, and edit the /etc/fstab to comment out swap. After that you can try booting to see what happens. And note that when I say /etc/fstab that does not mean the fstab file of the live session. Be careful with that. You have to edit your server OS fstab.

---

