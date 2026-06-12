---
title: "mdadm superblock size change"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by pertheusual on 2012-04-20
I'm running into some weirdness with mdadm that I was hoping someone might be able to help me with. I replaced old drives with new ones and expanded the device, and after rebooting the md device is smaller than it was originally.

Basically, have 2 1TB drives in raid1. I get two new 3TB drives to upgrade my storage.

1. Installed 2 new drives
2. Added them as spares in the array
3. Failed over each drive and allowed time to resync between each.
4. At this point, all is well, 'mdadm --detail /dev/md0' registers old drives as faulty spares
5. Ran 'mdadm /dev/md0 --remove failed' twice
6. --detail now shows only two new drives, md size ~1TB
7. Ran 'mdadm --grow /dev/md0 --size=max'
8. --detail now shows size of ~3TB
9. Reboot
10. --details now shows size of ~750GB

I'm at a bit of a loss, any thoughts?

---

### Post by pertheusual on 2012-04-20
Solved, in case someone else comes across this.

I had noticed, but failed to remember something weird. When running --detail on the array, the "Used Device Size" after I ran the  the '--grow' showed up as '-1'.

This was because my array was old, and the metadata was version 0.9. You can check this if you run 'mdadm --examine /dev/sda1' and look at the version displayed. Version 0.9 has a maximum size of 2TB. Apparently grow in my version of mdadm wasn't smart enough to warn me about this, though maybe newer versions do.

Thankfully I found the solution here:
[http://comments.gmane.org/gmane.linux.raid/34471](http://comments.gmane.org/gmane.linux.raid/34471)

Basically, you need to remove and recreate your RAID array with the new metadata version. You need to use version 1.0 instead of 0.9. Apparently version 1.2 would cause data loss, so don't do that.

mdadm --stop /dev/md0
mdadm --create /dev/md0 --metadata 1.0 --raid-devices=2 --level=1 --assume-clean /dev/sda1 /dev/sdb1

That will remove and recreate the raid superblocks with metadata v1.0, which happily supports way more space.

Beware this will change the UUID of the raid, so you'll probably need to update exported raid values and maybe change your boot setup if these are boot drives.

---

