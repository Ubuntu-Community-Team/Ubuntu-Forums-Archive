---
title: "How to get Kernal on extenal drive"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by urdrwho on 2009-11-21
Several weeks ago I installed Ubuntu using the "install as windows application"

I choose to install to my external 250 gig HD, which is F drive on my laptop.

Yesterday I got a new 500 gig HD.  It will be the new external F drive.

I copied all the ubuntu stuff from the old external to the new 500 gig.

When I went to do a dual boot I got an error message.  The message was something about needing to install the kernel.

So how do I install the kernel to my external F drive.  While booting I think it looks for HD (0,0)  but it that line is needed to write script I can get the exact thing.

---

### Post by lmarmisa on 2009-11-21
I don't know if I understand you.

Do you want to install Ubuntu in your external drive?

I think that a fresh installation in that external disk is the best solution.

I don't know if you want to use the full external disk for Ubuntu or not. If not, define the partitions for Ubuntu during or before the installation process. Gparted is a good tool for that purpose starting the system from a CD Live of Ubuntu.

An important recommendation: during the step 7/7 of the installation, tick advanced options and select install the grub loader in the external disk. 

When the installation finishes, change the boot order priority of the BIOS: 1) CD/DVD; 2) USB disk; 3) internal disk.

Regards,

Luis

---

### Post by urdrwho on 2009-11-21
Several weeks ago Ubuntu was installed.  I have a laptop that is runnign XP.  Ubuntu was installed to the smaller external drive and a dual boot is now available on the XP laptop.

Now I would like to copy everything ubuntu that resides on the smaller external HD, everything that I did, everything installed., etc. to the new bigger HD.

I copied everything to the new HD except the kernel.  The kernel must be installed on the new external drive.

My first thought was to uninstall and do a new install but don't want to loose all my setup information.  It took long enough to get the audio to stream online radio and I don't want to go through it again.

> **lmarmisa said:**
> I don't know if I understand you.

Do you want to install Ubuntu in your external drive?

I think that a fresh installation in that external disk is the best solution.

I don't know if you want to use the full external disk for Ubuntu or not. If not, define the partitions for Ubuntu during or before the installation process. Gparted is a good tool for that purpose starting the system from a CD Live of Ubuntu.

An important recommendation: during the step 7/7 of the installation, tick advanced options and select install the grub loader in the external disk. 

When the installation finishes, change the boot order priority of the BIOS: 1) CD/DVD; 2) USB disk; 3) internal disk.

Regards,

Luis

---

### Post by steveneddy on 2009-11-21
> **urdrwho said:**
> Several weeks ago I installed Ubuntu using the "install as windows application"

I choose to install to my external 250 gig HD, which is F drive on my laptop.

Yesterday I got a new 500 gig HD.  It will be the new external F drive.

I copied all the ubuntu stuff from the old external to the new 500 gig.

When I went to do a dual boot I got an error message.  The message was something about needing to install the kernel.

So how do I install the kernel to my external F drive.  While booting I think it looks for HD (0,0)  but it that line is needed to write script I can get the exact thing.

The UUID # (unique user identification number) of the old external HD is different from the new external HD.

Either go into the grub files and change it or just do a new total reinstall.

It would probably be easier to Install Ubuntu in a Virtual Machine like VirtualBox. Use the external drive for data storage.

The kernel is there but is identified by the ID of the old HD.

Like I said, **just use a VM and be done with it**. Running an OS from an external drive isn't the best solution, in fact, it is a bad solution, speed being a determining factor.

If you get lost, just look at the links in my sig.

---

