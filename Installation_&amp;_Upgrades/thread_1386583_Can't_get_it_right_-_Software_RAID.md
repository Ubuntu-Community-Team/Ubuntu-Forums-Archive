---
title: "Can't get it right - Software RAID"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by rcap_jason on 2010-01-20
Hey guys,
 
First off, let me say "thank you" for all the information contained here. Just a few short months ago, I embarked on the journey to learn Linux. I have since installed it to multiple systems, gotten wine working with multiple programs, and replaced most of my need for windows with free alternatives. Thank you all.
 
On to my new problem. Software RAID in 9.10...
 
I have setup a virtual machine in virtualbox. I created two 8GB virtual hard disks. I boot off 9.10 x64 CD. I launch the live CD and at the desktop I use built in software to setup the two virtual drives as RAID 0. After creating the RAID, I cannot successfully install Ubuntu. I configure three partitions on the RAID, one for filesystem, one for swap, and one for boot. But the install always fails. Any suggestions?
 
I have searched around and can't seem to find a complete guide, or anything close to complete, for setting up the RAID and installing the OS. Any help would be appreciated. I'd like to get this right in a virtual machine before I move on the real hardware.
 
Thanks,
 
Jason

---

### Post by rcap_jason on 2010-01-20
I can get it to install, but once I reboot it won't load... I've tried placing the the / and /boot and swap on various disks and partitions. Never seems to work as long as the RAID is present.  
 
Jason

---

### Post by ttoilleb on 2010-01-20
According to [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) - you can not install Ubuntu on any software Raid other than Raid 1.

---

### Post by rcap_jason on 2010-01-20
Actually, if I'm reading it correctly, you just have to place /boot on RAID 1 or non-RAID partition. I tried this and it didn't work for me.
 
*Warning: the /boot filesystem cannot use any softRAID level other than 1 with the stock Ubuntu bootloader. If you want to use some other RAID level for most things, you'll need to create separate partitions and make a RAID1 device for /boot.* 
 
???
 
Jason

---

### Post by marmida on 2010-01-21
Did I read this correctly?  Are you trying to install Ubuntu as a guest OS, inside the virtual machine?  The "built-in" software is either motherboard/fakeraid, or maybe a VirtualBox thing for creating virtual RAIDs?  Either way, I'm guessing that the answer is simply: don't do this; there's not much point in making a RAID unless it's on the bare metal.

---

### Post by rcap_jason on 2010-01-21
[I]Did I read this correctly? Are you trying to install Ubuntu as a guest OS, inside the virtual machine? The "built-in" software is either motherboard/fakeraid, or maybe a VirtualBox thing for creating virtual RAIDs? Either way, I'm guessing that the answer is simply: don't do this; there's not much point in making a RAID unless it's on the bare metal.

[/I]I disagree... As I already stated, the reason is so I can test software RAID in Ubuntu BEFORE attempting it on actual hardware. Thanks for the input, it really helped...

The disk utility software, palimpsest, in Ubuntu will let you take hard drives/partitions and build software RAID. I am trying to see if this will work in my home environement for storage/sharing with multiple drives in one machine. Any helpful suggestions out there?

J

---

### Post by ttoilleb on 2010-01-22
I am not convinced that palimpsest is the right tool to accomplish the task.  I would suggest reading the following links and then walking thru the steps.

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

The 1st one I referenced in an earlier post.

Also, are you sure that 2 x 8gb virtual disks are enough space for testing.  You mention at least 3 partitions that would appear to be defined within those vds.

If you could boot the live cd from within your test virrtual guest then post the output from *sudo fdisk -l* it might help.

---

### Post by darkod on 2010-01-22
You said you tried /boot to be RAID1. Did you try to have /boot partition outside the array? It's not in fact an array, the OS is combining partition into software raid devices.

PS. Are you only trying to use palimpsest or you have tried the Alternate Install CD too? For LVM and/or RAID you need to use alternate cd image. No palimpsest action needed.

---

