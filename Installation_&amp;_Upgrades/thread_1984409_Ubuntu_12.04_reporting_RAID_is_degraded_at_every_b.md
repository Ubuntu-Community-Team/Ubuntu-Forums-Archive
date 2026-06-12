---
title: "Ubuntu 12.04 reporting RAID is degraded at every boot"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by Erk1209 on 2012-05-21
Hello, first time poster on the forums here.

I am using Ubuntu 12.04 desktop as a file server for my network. I have a 160GB drive containing the OS and 3 500GB drives making up a software RAID 5. I am using samba to share the RAID across my network and everything there is going swimmingly.

However, I noticed that my RAID path changed from /dev/md0 to /dev/md127 mysteriously and I suspect that is the cause of Ubuntu constantly informing me the RAID is degraded at boot. Disk Utility does not report an errors in the array.

Is this something you all can help me clear up? I want to be able to use the server headlessly which of course would be difficult if I have to tell the OS to boot with a degraded array each time.

Thanks in advance for your help, I'm new enough to Linux that quirks like this are fairly baffling.

---

### Post by bretcb on 2012-07-05
I am having the same issue and have yet to find a complete solution.   [Neil Brown's (writer of the mdadm software to create/manage RAID) blog article]("http://neil.brown.name/blog/20120615073245") mentions a nasty bug that seems to cause these symptoms ("*The bug will only fire if, while the machine is shutting down, and array is partially assembled but not yet started. If the array is started and running it is safe ... as long as it stays that way.*") and mentions, I believe, when the bug was introduced and when it was fixed.   However ... I am not familiar enough with Linux kernels and/or Ubuntu at the level that I can correlate "commit" strings with version numbers.

So, I upgraded the kernel to the newest non-release-candidate one available on kernel.ubuntu.org, "3.4.0-030400-generic_3.4.0-030400.201205221131", and upgraded mdadm to the latest stable version 3.2.5, just to be sure.  It hasn't seem to have made any difference so far, but I keep reading and discovering new things I may have to do.  Any additional input or help would be most helpful.  So far, my process is:

[LIST=1]
[*]Reboot
[*]Click "y" to boot the degraded array
[*]Run "Disk Utility"
[*]Unmount my logical volume
[*]Stop my logical volume group
[*]Stop the RAID array
[*]Issue an mdadm create command, as per Neil Brown's "What should I do if I have already been bitten"
[*]Note that the RAID and Volume Group are now started again
[*]Recreate the /dev/md folder, and chgrp it to "disk"
[*]Create a symlink file called "[hostname]:0" (where I actually substitute my machine's hostname) to /dev/md0 (the name of my array)
[*]Stop my logical volume group in Disk Utility again
[*]Click my array, and use "Disk Utility" to "Check and Repair" it.
[/LIST]

The repair is running right now, and will take all night.  Tomorrow I will run the logical volume group, mount the logical volume, and reboot again ... and see if I have to repeat and try to find a new step.

I'm hoping someone can tell me if, based on Neil Brown's article, the kernel version I installed is vulnerable and I've spent all this time banging my head against a brick wall for nothing:
> The bug was introduced by


     commit c744a65c1e2d59acc54333ce8
         md: don't set md arrays to readonly on shutdown.
 

and fixed by


     commit 30b8aa9172dfeaac6d77897c67ee9f9fc574cdbb
         md: fix possible corruption of array metadata on shutdown.
 

These entered the upstream kernel for v3.4-rc1 and v3.4-rc5 respectively, so no main-line released kernel is vulnerable.

Someone please help Erk1209 and I!  Thank you!

---

### Post by bretcb on 2012-07-08
Apologies for the delay.  Repairing takes time, and I've been busy with other things as well.  So, in addition to the above list, I then realised that 2 of the 3 drives in my RAID still appeared on my desktop as mountable drives, and appeared to have non-raid partitions on them in Disk Utility - clicking "Edit Partition" and attempting to change the disk label resolved this.

I then ran a repair again, just to be sure.

More reading suggested to me that the output of the command "mdadm --examine --scan" that I was using to generate the configuration for mdadm.conf no longer generated compatible output, most notably it called the array "/dev/md/0", not "/dev/md0".  It also generated a "name" for the array, which apparently should no longer go into the mdadm.conf.  So, the definition of existing arrays in my mdadm.conf now looks like:

```
ARRAY /dev/md0 metadata=1.2 UUID=[my UUID]
```

Next, I read that after redefining an array, I need to run command "update-initramfs -u" so that the initial ramdisk created for booting has the correct array information; I also added the "-v" switch, just so I could see all the info.

Now, I'm going to reboot again.  I wanted to type everything out beforehand so I didn't forget, or lose it if I manage to hose my whole system :eek:.  Stay tuned in for another update in a few minutes ...

---

### Post by bretcb on 2012-07-08
OK, here's the update.  I *didn't* get the request to continue with the degraded array ... 

... but my logical volume has completely vanished.  Maybe that's because I keep messing with the array that's underneath.

So,
 - I deleted the fstab entry for my logical volume
 - I use logical volume manager to recreate my volume group and volume
 - It's mounted, and a new fstab entry has been created.
 - I ran "update-initramfs -u -v"

There still seems to be some activity on the drives / array / volume, presumably some background formatting or some such, so I'm going to let that settle, then reboot again.

More updates to follow.  I will also post my bibliography, in case others need to do some reading.

---

### Post by bretcb on 2012-07-09
Success!

I've rebooted, the array still exists and is not degraded; the volume still exists on the array, and the data still exists on the volume.

OK, summary and bibliography; your mileage may vary:
[LIST=1]
[*]Upgrade my kernel to the latest non-RC release[LIST]
   [*]Download from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
   [*]How to upgrade: [http://www.unixmen.com/upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint/]("http://www.unixmen.com/upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint/")[/LIST]
[*]Reboot, y to boot with degraded array
[*]Download and install latest mdadm (make; make install)[LIST]
   [*]first: apt-get install binutils-dev
   [*]Download from:[http://www.kernel.org/pub/linux/utils/raid/mdadm/]("http://www.kernel.org/pub/linux/utils/raid/mdadm/")[/LIST]
[*]Reboot, "Y" to continue booting with the degraded array[LIST]
   [*]On boot[/LIST]
[*]Unmount my volume, stop my volume group[LIST]
   [*]Logical Volume Management[/LIST]
[*]Stop my array[LIST]
   [*]Disk Utility[/LIST]
[*]Recreate the array, duplicating all previously set parameters in the command line[LIST]
   [*][http://neil.brown.name/blog/20120615073245#4]("http://neil.brown.name/blog/20120615073245#4")[/LIST]
[*]Check that all array component drives show as "RAID Component" when clicked on in Disk Utility.  They didn't, so use "Edit Partition" to try to change the label.
[*]Use the Check Array button to repair the array
[*]Use mdadm --examine --scan to generate the parameters for my array, but edit the output data[LIST]
   [*] See June 2nd, 2011, 02:08 PM post in [http://ubuntuforums.org/archive/index.php/t-1772692.html]("http://ubuntuforums.org/archive/index.php/t-1772692.html")
   [*] Ensure /dev path to array matches, delete "name:" attribute[/LIST]
[*]Issue a "update-initramfs -u -v" command[LIST]
   [*] Reference URL is the same as previous step[/LIST]
[/LIST]

At this point, I rebooted, and my logical volume was gone.  I didn't care, because it's a new system, but for anyone else, you may want to look at Disk Utility and Logical Volume Management and Google and figure out how to save your logical volume before you reboot.  Or backup.

As an aside, I had originally formatted my logical volume with ext4, but discovered after it mounted, that something would access the mount every couple of seconds - I could see the light/hear the activity, and JBD2 was popping up in iotop.  It's the journalling software, and there may or may not be a bug, but since it only affects ext4, I formatted my volume to ext3 and it's fine.

Good luck to Erk1209, and anyone else who encounters this problem.

---

