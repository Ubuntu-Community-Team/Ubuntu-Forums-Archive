---
title: "Boot issues, mulit-booting, eSATA in the mix"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by reiki on 2010-04-13
I have my primary internal hard drive set up with Win7 and Karmic (100GB for windows, 650GB for Karmic)

I've installed 10.04 Ubuntu and Kubuntu on an external eSATA (640GB)

Lately I've had issues trying to boot where I never get to the grub OS selection screen, but get errors instead. Things like messages that some symbol "???????????????????<heart>" is not found. I eventually get to a grub rescue> prompt. This happens whether I have the eSATA powered up before booting or not. I've had to boot from a live CD, mount my Karmic root, reinstall grub2 to /dev/sda each of the last 2 mornings. I have now powered off the eSATA, booted to Karmic, and did an update-grub without that eSATA connected. It remains to be seen if this is going to solve the problem.

Where would I look for the log of issues when this happens? I'd like to be more helpful but I'm at work right now. If I break it again i n the morning I'd like to know how to properly report what's happening. 

then again.... if it DOESN'T break... maybe I'll just not run 10.04 from the eSATA. :)

---

### Post by ranch hand on 2010-04-13
If you want both of them to work from your internal I think that you will need to have the external turned on.

I would do that and then go to bios and turn off the internal and boot to the external and make sure that grub there is install on that MBR.

You should also check the device map (if you still have one) on your internal installation and make sure that it is correct for what you are booting from it.

I have an internal that has some OS' on it booting from 9.10 64bit and it is also set up to boot my external enclosure (USB).  The device map for it is;
> 
(hd0)    /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

You also might want to check
```

blkid

```
to make sure that you do not have conflicting uuids.  I had that problem.  I have found that formating with all drives live is the only safe thing to do to avoid that problem.

---

