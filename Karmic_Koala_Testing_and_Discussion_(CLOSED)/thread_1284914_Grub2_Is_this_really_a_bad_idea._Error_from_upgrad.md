---
title: "Grub2: Is this really a bad idea. Error from upgrade."
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-10-07
Grub2 is installed to sdb1 partition. It works fine and I chainload to it from Jaunty on sda1.

```
Setting up grub-common (1.97~beta3-1ubuntu8) ...
Installing new version of config file /etc/init.d/grub-common ...

Setting up grub-pc (1.97~beta3-1ubuntu8) ...
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  **This is a BAD idea**.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

```

---

### Post by MALEADt on 2009-10-07
A regression has entered the Grub2 codebase which could prevent users from installing it on the PBR (partition boot record), quoting [from here](http://grml.org/grml2usb/#mbr-vs-pbr).
I haven't tested it, but based on that site (and some other bug reports I can't seem to retrieve nright ow) I decided to remove Grub2 and revert to the legacy one for another few months. However, you seem to be able to chainload a PBR-based grub2 fine?

---

### Post by philinux on 2009-10-07
> **MALEADt said:**
> A regression has entered the Grub2 codebase which could prevent users from installing it on the PBR (partition boot record), quoting [from here](http://grml.org/grml2usb/#mbr-vs-pbr).
I haven't tested it, but based on that site (and some other bug reports I can't seem to retrieve nright ow) I decided to remove Grub2 and revert to the legacy one for another few months. However, you seem to be able to chainload a PBR-based grub2 fine?

Yes been chainloading to the PBR since alpha1. If someone is multibooting you really want one "master" grub on the MBR of disk1. This could be grub or grub2. It then controls the boot of the other OSs from their PBR grubs, whether on the same disk or another drive.

---

### Post by DougieFresh4U on 2009-10-07
Just updated 3 partitions. All had updates, but not all had the same updates. Added the .12 kernel to all. 
Had to run **sudo update-grub2** on all partitions to get grub menu straightened out, but all is booting great and no drama this morning

---

### Post by philinux on 2009-10-07
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)

Can someone pop along here and change the status to confirmed. Cheers.

---

### Post by MALEADt on 2009-10-07
> **philinux said:**
> Yes been chainloading to the PBR since alpha1. If someone is multibooting you really want one "master" grub on the MBR of disk1. This could be grub or grub2. It then controls the boot of the other OSs from their PBR grubs, whether on the same disk or another drive.
Which is what I'm doing indeed :) Too bad most distro's (including ubuntu) tend to overwrite my masterbooter on each install.
I think I'll skip grub2 though untill that "regression" is fixed for sure, I don't want to end up with a dis-functional system somewhere in the future. FYI: grub-legacy is still fully functional in karmic.

---

### Post by VMC on 2009-10-07
I ran across this yesterday at PartedMagic site. Someone had issue using grub2 on a partition.

Thanks for bringing this topic up and the reference to that bug report.

---

### Post by philinux on 2009-10-07
Can someone change the status to confirmed. Cheers.

You should be able to install grub to a partition without this weird warning message. Grub legacy never gave such messages.

---

### Post by sports fan Matt on 2009-10-07
it was a bad idea for me but then it was my fault..i failed to follow all the instructions.  :lolflag:

---

### Post by oldfred on 2009-10-07
I downloaded Karmic Sept 9 and I think it was alpha5. I knew I wanted to chainboot, so I installed grub2 to the partition. You have to click on the advanced button at the point it wants to install grub2 to the MBR. Install to the MBR is standard so anything else must be advanced?

I did not notice the warning when I installed grub2 to the partition, but every time I update it seems to run the grub2 update 2 or 3 times and I see the warning message 2 or 3 times that I have installed it in the partition and it is not recommended. I chainboot from grub legacy and it has worked fine for me.

I will always want to chainboot so if grub2 will not be determined to be reliable I will not want to use it.

---

### Post by philinux on 2009-10-07
> **oldfred said:**
> I downloaded Karmic Sept 9 and I think it was alpha5. I knew I wanted to chainboot, so I installed grub2 to the partition. You have to click on the advanced button at the point it wants to install grub2 to the MBR. Install to the MBR is standard so anything else must be advanced?

I did not notice the warning when I installed grub2 to the partition, but every time I update it seems to run the grub2 update 2 or 3 times and I see the warning message 2 or 3 times that I have installed it in the partition and it is not recommended. I chainboot from grub legacy and it has worked fine for me.

I will always want to chainboot so if grub2 will not be determined to be reliable I will not want to use it.

Agreed.
Would you care to add your comment to my bug report and change it's status to confirmed. Cheers

---

### Post by ranch hand on 2009-10-07
I think that warning should probably be on anything you do in pre-release OS', like installing in the first place.

I am sure that all of us have some of our fondest memories around things that were a BAD IDEA.

---

### Post by snkiz on 2009-10-07
I did an update to grub2 from grub-legacy installed in a pbr. The test went fine but when I try to replace grub-legacy, grub2 informs me that it will install to to mbr. Fine for most, but I do not wish to disturb the orignal mbr for warranty purposes. I use partition flags to manage the bootloaders. So the point is how did you install to the pbr in the first place?

---

### Post by philinux on 2009-10-07
> **snkiz said:**
> I did an update to grub2 from grub-legacy installed in a pbr. The test went fine but when I try to replace grub-legacy, grub2 informs me that it will install to to mbr. Fine for most, but I do not wish to disturb the orignal mbr for warranty purposes. I use partition flags to manage the bootloaders. So the point is how did you install to the pbr in the first place?

At the last bit of the livecd install I clicked advanced and chose sdb1. Been doing this ever since I got my pc 2 years ago with 2 HD's.

You can reinstall from the livecd to a partition or mbr.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by snkiz on 2009-10-07
I did an upgrade in place ```
sudo update-manager -d
``` Witch went surprisingly well considering all the PPA's I have, only had to clean about a dozen packages after. I found this as well [http://grml.org/grml2usb/#mbr-vs-pbr]("http://grml.org/grml2usb/#mbr-vs-pbr") but both your solution and the one I found appear to fix an existing grub2 install would they work to replace the legacy-grub?

---

### Post by oldfred on 2009-10-07
Some, particularily the one's working on Grub2 do not like block lists and installing in a partition. Its just that this is how we who are chainbooting have always done it. I did find a few comments saying blocklists were not bad and may be good in some cases.

Explanation of why blocklists are bad:
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

---

### Post by snkiz on 2009-10-08
> **oldfred said:**
> 
Explanation of why blocklists are bad:
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
My boot partition is seperate from my filesystem for all of the reasons listed there and I never had an issue. I have 2 systems with managed pbr's

---

