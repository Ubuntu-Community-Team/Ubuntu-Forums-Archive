---
title: "LVM2 / libdevmapper version mismatch?"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by ken.emerson on 2006-11-01
I recently upgraded to edgy bringing along my LVM, 3 disk volume group.  I wanted to substitute a larger faster disk for two of the smaller slower IDE drives.  After installing LVM2 support via apt-get and successfully importing my volume group, I added my new drive (pvcreate,vgextend) and then attempted to do a pvmove.  First I got the error "mirror: Required device-mapper target(s) not detected in your kernel" and learned I needed to do a modprobe dm-mirror.  The next attempt to do the pvmove resulted in the error: "device-mapper: reload ioctl failed: Invalid argument".

Once this error appears, any operation on the volume group hangs and only a hard reset will clear it.  The data appears to still be intact as if nothing was moved (or at least deleted).

I have found one other person who had the same problem AND got an answer back:  Version mismatch between LVM2 and libdevmapper.  I would have expected apt-get to circumvent such a problem.

I am also curious why the dm-mirror kernel module must be loaded by hand.  Not very intuitive for the (not an expert) user.

Do I need to download the source for LVM2 and manually compile against my kernel headers to get this to work?

I am running on an AMD64x2 platform and edgy eft loaded from the live CD chosing workstation.  Main use for system is mythtv plus training/development.

Regards,

Ken Emerson

---

