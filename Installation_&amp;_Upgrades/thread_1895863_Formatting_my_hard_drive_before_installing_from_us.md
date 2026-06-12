---
title: "Formatting my hard drive before installing from usb"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by Lyalpha on 2011-12-15
I was wondering if wiping my hard drive before installing 10.04 would prevent me from installing it?  Would it delete the BIOS and screw me over?

---

### Post by N00b-un-2 on 2011-12-15
> I was wondering if wiping my hard drive before installing 10.04 would prevent me from installing it? Would it delete the BIOS and screw me over? 

That depends on what you mean.  I'm going out on a limb here, but I'm assuming you have a late model Dell laptop.  If you have like I've seen on Dell laptops in particular where there is a small (like 30MB) partition that stores the Dell system configuration environment, probably not.  But err on the side of caution.  Before wiping it, I would either A) make a full disk backup using a utility like clonezilla, or B) write down exactly how big the partition is, what file system type it is, any flags there may be (like "boot", etc.) and then I would back up that partition.  the easiest way to make a perfect bit for bit copy would be to use the dd command and save it as an iso.  I suppose tar would work too, but I would probably go with iso if it were me.

ex:
```
sudo dd if=/dev/sda1 /home/your-username/dell-system-configuration.iso
```

If I recall correctly, the Dell System Configuration environment basically acts as a graphical front end for the BIOS, and if you remove it, the computer should fall back to the default BIOS that is hard coded onto the motherboard.

I suppose the easiest way to test if it would work or not would be to remove the hard drive from the computer and turn it on.  if it boots up into BIOS which it should, then you should be able to wipe your hard drive without any issues.

---

### Post by Lyalpha on 2011-12-15
I'm actually using a lenovo thinkpad.  And backing up is a problem because the reason I want to format the drive is that somehow the .init file got corrupted during a failed update and now I can't mount a kernel to the filesystem.  No kernels work.  I can't even install from a boot disk because it can't mount.  I have nothing on the drive I want to keep so I just need to be sure that the BIOS will not be erased when I format the drive (which I plan to do with knoppix).  Will I be able to use my usb installer after the drive is wiped clean?

---

