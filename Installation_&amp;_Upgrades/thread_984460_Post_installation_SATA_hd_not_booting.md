---
title: "Post installation SATA hd not booting"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by markthecarp on 2008-11-16
Some background:
IDE channel 2: DVD/RW, CD/RW
SATA1: 160 gig

The system formerly worked fine with an IDE hd and optical devices as they are now. LiveCD's, of many varieties, don't seem to see the SATA hd. The usual commands fail to find/mount/etc what should be /dev/sda...

The install seems to go fine but on the first reboot it fails to find the SATA hard drive.

My last straw is to switch the optical drives to IDE 1. 

BIOS and mobo info available if that helps.

I'm stumped :(

-mark

---

### Post by cariboo on 2008-11-16
Are you getting a grub error? Does it say boot disk not found? What exactly is the error?

If you boot from the LiveCD and select boot from hard drive can you boot into Ubuntu. If you can boot Ubuntu using the LiveCD. could open a Applications-->Accessories-->Terminal and paste the output of the following 2 commands in your next post:

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

Jim

---

### Post by markthecarp on 2008-11-17
> **cariboo907 said:**
> Are you getting a grub error? Does it say boot disk not found? What exactly is the error?

No grub errors, apparently it's not getting that far in the bootup process. Here's what I get booting w/o a LiveCD...
```

Scan Devices, Please wait...
Press <Tab> Key into User Windows!

HardWare Initiate failed, Please Check Device!!!
The Bios does not be installed. Press <g> to continue!

```
> 
If you boot from the LiveCD and select boot from hard drive can you boot into Ubuntu. 

That fails with the following error message...
```

Booting from local disk...
isolinux: Disk error 01, AX = 0201, 80

Boot failed: press a key to retry...

```

I have been able to boot to the hard drive one time. I was in the BIOS and selected "Upgrade Bios". This lead to a Dialog that failed as it requires a floppy drive which the system doesn't currently have. I pressed ESC to exit the dialog and the system booted to the hard drive. I have _not been able to replicate this.

-mark

---

### Post by toddedw on 2008-11-17
On the screen that says the 'BIOS does not be installed' does it say anything about RAID at the top of the screen? If so you need to go into the BIOS and disable RAID. If that doesn't work I read another post where a guy fixed this problem by switching his cable.

Hope this helps.

---

### Post by markthecarp on 2008-11-18
> **toddedw said:**
> On the screen that says the 'BIOS does not be installed' does it say anything about RAID at the top of the screen? If so you need to go into the BIOS and disable RAID. If that doesn't work I read another post where a guy fixed this problem by switching his cable.

Hope this helps.

Yes, something about a Bios SATA Raid controller with a version number. I haven't found anything in the Bios relating to RAID at all or anything relating to SATA. I did try switching cables which didn't help.

Now in a post to the #ubuntu-northcarolina IRC channel toddedw sent two links to offsite forum posts. One of these had the clue. The motherboard only supports SATA I but the hard drive is SATA II; setting a jumper on the hard drive makes it SATA I data rate.

So problem is 90% solved. The system still doesn't make it to grub until I press F1. I'm thinking this is the Bios looking for hard drives on IDE channel 1. One more experiment on that and I'll post back the results.

Thanks guys...

-mark

Edit: changing the IDE channels didn't help.

---

