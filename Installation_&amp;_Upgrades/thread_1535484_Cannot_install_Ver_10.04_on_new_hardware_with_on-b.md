---
title: "Cannot install Ver 10.04 on new hardware with on-board raid controller"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2010-07-20
Trying to install Ubuntu 10.04 on a brand new computer with the following specs:
Motherboard - Intel BOXDQ57TM
Ram - 4 Gb
Processor - Intel Core i3 540 3.06 CPU
Hard drives - 2  WD3200AAKS Sata being used as a RAID 

During (32bit) installation (using guided partitioning) the drives showed up as Serial ATA RAID isw_hdhhjdeeh_Volume0 (stripe) - 640.1 Gb Linuxd 

The installation failed at partitioning with the error message "Failed to Create a file system.  The EXT4 file system in partition #1 of Serial ATA RAID isw-hdhhjdech_Volume 0 (stripe) failed" 

I found a posting that claimed Ubuntu 10.04 cannot install on a system using a RAID, and it suggested installing an earlier version of Ubuntu then updating to Ver 10.04.  So I tried installing Version 9.10.  That installed with no errors until the end when it would not install a boot loader.
  
The message was "No boot loader installed because your specific architecture doesn't support a boot loader yet.  You will need to boot manually with /vmlinuz kernel on partition /dev/mapper/isw_hdhhjdeeh_Volume01 and root=/dev/mapper/isw_hdhhjdeeh_Volume01 passed as a kernel argument"

Have tried installation with both desktop and alternate installation disks.

What can I do to get this system up and running without having to boot manually?

Tried installing Ubuntu Server 10.04 (64 bit) as suggested in Ubuntu Wiki but still could not get drives configured.

---

### Post by ronparent on 2010-07-22
Currently 10.04 cannot be installed to a raid without using workarounds. I have previously advised people of this and further advise that it was doable if they used gparted in a prior version to create a target formatted (ext2, ext3, or ext4) partition to do the 10.04 install to. It is not necessary to first install 9.10 and there may be some 10.04 upgrade complications if you do so.

I have since discovered that you can also install if you 1) 1st run the live cd 2) open gparted from a terminal with the command (in your case):

> sudo gparted /dev/mapper/isw_hdhhjdeeh_Volume0

and create a target raid partition to install to. Note if you have another operating system on your computer you should create  your needed raid partitions in an extended partition (to avoid exceeding a max primary partition count of 4 - if there is nothing else on the drive or you don't plan a windows install this is not necessary). 3) Continue and run the installer from the live cd session, select the third option to manually select your install location, and, select the target you created for the install for /. Do not select to format it and continue with your install.

Following he above instructions you will eventually get to step 8 of 8 in the install process. In this step you need to select the 'advanced' box to opt for installing the grub boot loader to the raid. If this last step results in a 'fatal error', it can be fixed with a grub 2 rescue disk.

You can probably complete on your own. But if you need help post here. Good luck.

A final note: I you don't intend to dual boot with windows you also have the option of installing to a software raid. It is no more daunting than the 'fakeraid' which you intend. however, I wouldn't be able to help.

---

### Post by MacDuff on 2010-07-22
Thanks for the reply.  I kept trying different installs and found that when the installation process tells you it found a raid controller (I forget the actual term) and asks if you want to actuate it, if I answered "NO" the installation would continue without problem.  It ended up with a system having two drives but no raid, naturally. 

You mention a "fake raid".  The term is new to me.  My motherboard contains a raid controller.  Is that a "fake raid"?  I would have thought that a "fake raid" was something done with software.

Regarding your question about other operating systems, only Ubuntu will be installed on this machine.   There will be a virtual Windows installation rather than dual booting.

I will follow your instructions and see what happens.

Mac

---

### Post by ronparent on 2010-07-23
I just discovered the fix for our problem yesterday posted to my bug report.  That is to just to add a package that was omitted from the 10.04 distribution. Apparently 10.04 doesn't install without workarounds because the distribution omitted the package kpartx! It could be easily added to a 10.04 live cd session with the Synaptic Package Manager and then 10.04 easily installed by the 10.04 installer run from that same session. That would eliminate the need for the work around I outlined previously.

---

### Post by MacDuff on 2010-07-23
> **ronparent said:**
> I just discovered the fix for our problem yesterday posted to my bug report.  That is to just to add a package that was omitted from the 10.04 distribution. Apparently 10.04 doesn't install without workarounds because the distribution omitted the package kpartx! It could be easily added to a 10.04 live cd session with the Synaptic Package Manager and then 10.04 easily installed by the 10.04 installer run from that same session. That would eliminate the need for the work around I outlined previously.
That is interesting!  Thank you for posting that work-around.

---

### Post by crotale on 2010-09-08
> **ronparent said:**
> I just discovered the fix for our problem yesterday posted to my bug report.  That is to just to add a package that was omitted from the 10.04 distribution. Apparently 10.04 doesn't install without workarounds because the distribution omitted the package kpartx! It could be easily added to a 10.04 live cd session with the Synaptic Package Manager and then 10.04 easily installed by the 10.04 installer run from that same session. That would eliminate the need for the work around I outlined previously.

I'm trying your fix but I can't seem to get it to work.

Start Live session, then:

```
sudo aptitude install kpartx
```Then running the installer and letting it use the entire disk or creating my own partitions, but it still failes with the same message; "Failed to create a file system".

You don't happen to have any other suggestions, please?

***EDIT*** Just because I wrote this post I got it working right afterwards... Perhaps I hadn't restarted gparded or something, but I got it working now. Thanks **ronparent**!

---

### Post by ronparent on 2010-09-08
Your welcome. Glad to hear it's worked out.

---

