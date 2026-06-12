---
title: "Ubuntu and JBOD?"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by mazzizo on 2011-08-04
Just curious if there is any sort of issues with Ubuntu and JBOD assignments. I had my 2 500GB hdd's as JBOD through my mobo BIOS/RAID Config and it didn't like it. It installed just fine and showed the hard drives separately. I really didn't think anything of it so I continued on. 

After the install completed successfully, and I rebooted the system, it came to a blank screen with a blinking cursor and wouldn't continue on. So I tried restarting a few times, no luck. Finally I was like "okay screw this, going to install with no RAID setup or JBOD setup." (had RAID issues last night. rabble rabble) Removed RAID configurations and BAM started right up.

So yeah, just curious is all. Also sorry if this isn't the appropriate section for a post like this, although help on the issue would be appreciated.

Thanks
P.S. Semi-new to Linux/Ubuntu. Know the basics and what not, just not some of the more advanced stuff.

Edit: Okay, so I restarted my computer and removed my USB drive (which I had installed Ubuntu from) and it didn't boot. So it was NOT an issue with JBOD. Guess I'll look for a resolution for that, though.

---

### Post by dino99 on 2011-08-04
[http://www.openegg.org/forums/posts/list/88.page](http://www.openegg.org/forums/posts/list/88.page)

---

### Post by mazzizo on 2011-08-04
So as I got back into Ubuntu, I went and checked out the Disk Utility and I see /dev/sda as Usage: Filesystem, but Partitioning: Unknown Scheme:. I looked at the USB drive and it said it was the MBR. 

Tried formatting sda to the MBR, but low and behold disk is in use. dur. So, is there a way to I can format it to be the MBR before loading in or am I boned and going to have to reinstall once again? Think I'll just burn to a disk this time, if I have to.

---

