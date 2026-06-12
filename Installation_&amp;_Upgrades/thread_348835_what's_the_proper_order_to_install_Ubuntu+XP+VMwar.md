---
title: "what's the proper order to install: Ubuntu+XP+VMware?"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2007-01-29
I have ubuntu installed,
now I want to reinstall XP which crashed recently.
I also want to install Vmware.

I am not sure whether I should install XP first or Vmware first, or doesn't matter.

Is there some detailed HOWTO about this topics?

Thanks

---

### Post by Tanker Bob on 2007-01-29
> **hopestorm said:**
> I have ubuntu installed,
now I want to reinstall XP which crashed recently.
I also want to install Vmware.

I am not sure whether I should install XP first or Vmware first, or doesn't matter.

Is there some detailed HOWTO about this topics?

Thanks

What's your setup like?  Do you have a dedicated NTFS partition for XP on the same disk with your ubuntu, or a separate hard drive, or did you have it running in a VM under VMWare?  Does your VMWare run on linux or Windows?

---

### Post by hopestorm on 2007-01-29
Now I have NTFS partion (/hda1) with XP installed, but it was crashed and I need to reinstall.
the Ubuntu is on partition /hda6.  other partions are for /home and my working directory respectively.

The Vmware will be installed in linux. Do I need specific partion for Vmware?

Thank you for your help.

---

### Post by Tanker Bob on 2007-01-29
> **hopestorm said:**
> Now I have NTFS partion (/hda1) with XP installed, but it was crashed and I need to reinstall.
the Ubuntu is on partition /hda6.  other partions are for /home and my working directory respectively.

The Vmware will be installed in linux. Do I need specific partion for Vmware?

Thank you for your help.

No, you do not need a specific partition for VMWare.  I have my VMs installed under /home/username/ on my Kubuntu installation.

You should be able to reinstall XP to its NTFS partition with no problem.  VM order doesn't matter since the VM cannot access the XP partition except through network sharing.

WAIT - I'm reading between the lines here.  Are you using the XP partition as the disk for the VM?  This is a critical question.

As an aside (maybe), reinstalling XP over itself can recover your previous setup if you answer its prompts correctly.  Read each screen carefully.  Do not choose "R" (for the Recovery Console) in the first screen, but I think that it's the third screen where you hit "Enter" to recover an existing installation.

---

### Post by hopestorm on 2007-01-29
Yes, My XP and Ubuntu are on same physical drive.
I am thinking the Vmware is just one software and can be installed anywhere with Ubuntu.
I just want to use vmware to use some windows applications sometimes.

Sounds like I need to read some introduction of Vmware before go ahea?

Thanks anyway

---

### Post by Tanker Bob on 2007-01-29
> **hopestorm said:**
> Yes, My XP and Ubuntu are on same physical drive.
I am thinking the Vmware is just one software and can be installed anywhere with Ubuntu.
I just want to use vmware to use some windows applications sometimes.

Sounds like I need to read some introduction of Vmware before go ahea?

Thanks anyway

VMWare is indeed just a software package for your host OS (ubuntu linux).  Your virtual machine (VM) can be installed anywhere in your ubuntu partition.  I have all mine in my /home/username/ directory.

Sounds like your XP is a free-standing double boot setup.  That will work fine.  I was concerned that you were going to use that free-standing XP as the disk for a VM.  There are specific problems with that, so VMWare warns against using physical guest implementations like that.  Has to do with services and drivers that work natively on the PC but aren't available in the VM because of the virtualization environment, in which the host (ubuntu in this case) owns everything.  Chances are that such a setup would not work both as a double-boot and a VM.

A quick scan of the VMWorkstation manual (downloadable or readable online) can be most instructive on the ins and outs of VMs.  I would have benefited by skimming through it BEFORE I jumped in with both feet.  I use WinXP in a VM for the same reasons as you--to access those few things that I cannot do in linux, like sync my PDA to the desktop.  VMs are a great solution for this and are much more convenient than dual-booting all the time.

---

### Post by sstakes1 on 2007-01-29
There are two distinct things that are being mentioned here. You have a dual-boot setup. Therefore you can either boot XP or Ubuntu natively. 

Sounds like you want to run XP under VMWare under Ubuntu. You do not need a native XP installation in this case. All you need is to create a VMWare image for XP under Ubuntu.  There are many FAQs regarding creating VMWare images that will come in handy. Then you can point the VMWare Player to boot off of this image. This will be a distinct instance of XP than your native installation. 

If you are looking to run your native XP under VMWare, I do not know of any solutions personally, but I'm sure other members can help you.

Regards

---

### Post by Moulton on 2007-02-01
If you don't have a functional native installation of Windows, then you are in **good** shape.

The worst scenario is where you have existing installations of both Linux and Windows on different partitions on the hard drive.  While it's technically possible for VMware running in Linux to access the raw drive partitions with Windows, you really don't want to do that.  It's a technical nightmare and not for the casual user.

Using VMware in Linux, create a brand new installation of Windows, storing it on a standard .vmdk disk image that resides somewhere in your Linux file system.  If you are prepared to trash the old hard drive partition where you once had Windows, you can reformat that liberated partition as a clean new partition for Linux, and use it to house your VMware installation, including the .vmdk disk image for Windows.

---

