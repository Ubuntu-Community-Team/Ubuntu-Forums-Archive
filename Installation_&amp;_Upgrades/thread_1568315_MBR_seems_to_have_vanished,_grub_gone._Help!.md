---
title: "MBR seems to have vanished, grub gone. Help!"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2010-09-05
I had just gotten dual boot to work yesterday (had tried both OSs and they both worked). Then I went into Ubuntu to install apps. When I was done, I tried to load windows again and it told me there was a problem that needed to be fixed with the recovery disk. I put it in, it fixed the problem and windows started. Then I did some routine windows updates and now the MBR seems to be gone. I get the message (no grub shows up anymore!):

no module name found
Aborted. Press any key to exit.

When I press a key I get:
Press any key to boot from CD or DVD

If I don't press a key I get:

Press any key to boot from CD or DVD.....no module name found
Aborted. Press any key to exit.
Broadcom UNDI PXE-2.1 v11.0.9
Copyright (C) 2000-2008 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM
Operating System not found

and then I have to restart by holding off for 5 secs. Is there some way to restore the grub from the Ubuntu live installation disk? Would this even work?

Please help!

---

### Post by sharathcshekhar on 2010-09-05
Boot from a live cd and give ```

sudo grub-install /dev/sda
sudo update-grub

```
This will reinstall grub on your MBR of the first HDD. Post back if this doesn't solve your problem.
PS: As always, back up your imp data when playing with things like GRUB!

---

### Post by sharathcshekhar on 2010-09-05
Also go through this howto
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by EricDallal on 2010-09-05
I actually found another tutorial about reinstalling the grub and it seems to work. Unfortunately, it just results in another problem. As soon as I try to enter Windows, it begins starting up, but then goes to a screen that tells me it has to check for errors to one of the disks (or partitions - I forget the exact message). If I allow the check, it "fixes" the problem and I lose the grub again and am back to where I started. If I press a key to cancel the test, it just stays stuck and does nothing, after which I have to shut down the computer by holding the power key for 5 secs. After re-reinstalling the grub, I decided to try a memory test instead. Maybe the memtest that shows up in the grub can solve this problem? If not, then the only other thing I can think of is to use the Windows recovery disk until Windows is satisfied that all is well, then try to reinstall the grub from live installer again. Any suggestions?

---

### Post by dino99 on 2010-09-05
i suppose you are talking about grub2 (grub-pc into synaptic) right ?

when windows mbr is fixed, start ubuntu again, open synaptic and remove/purge (right click) grub-pc, then reinstall it where ubuntu is installed (not over the windows mbr again  ;)), so if ubuntu is on /dev/sda5, install grub-pc on /dev/sda5, that it.

---

### Post by presence1960 on 2010-09-05
If I remember correctly from another thread you have a Dell OEM computer. Your utility partition may be the source of the bootloader problem. It continually writes to the MBR. You may have to get rid of that utility partition, but keep all the others especially the Recovery Partition (unless you made a set of bootable recovery disk(s).

---

### Post by coffeecat on 2010-09-05
> **presence1960 said:**
> If I remember correctly from another thread you have a Dell OEM computer. Your utility partition may be the source of the bootloader problem. It continually writes to the MBR. You may have to get rid of that utility partition, but keep all the others especially the Recovery Partition (unless you made a set of bootable recovery disk(s).

Indeed, this needs to be more widely known on the forum, just so that members know that Windows software can be the cause of a failure of grub. And not just Dell utilities either. 

Link:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable").

Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

