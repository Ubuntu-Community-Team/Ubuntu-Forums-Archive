---
title: "How to run pre-installed Windows 7 as a virtual machine without installation discs?"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by Ohio on 2011-07-10
I just bought a shiny new laptop which came with Windows 7 pre-installed. I now want download Ubuntu and run Windows 7 in virtual box. Can it be done without the installation discs? I don't want to dual boot it, unless it can be done that way.

---

### Post by Quackers on 2011-07-10
Welcome to UF.
I'm not sure that you can do that. I'd like to know the answer myself though.
Have you made the recovery dvd's and tried them?

---

### Post by Ohio on 2011-07-10
I did make the recovery DVD, but I was under the impression that you can't use a recovery CD to install Windows from a blank slate. I'm kinda afraid to install Ubuntu then find out I can't get Windows installed.

I think I might just try partitioning the drive, install Ubuntu, leave Windows 7 on my computer with minimum partition, then see if the recovery CD can be used in virtual box to install Windows 7. Is this wise?:confused:

---

### Post by haqking on 2011-07-10
There are a few ways to convert a partition to a VM.

here is a link

[http://www.softpanorama.org/VM/conversion_of_harddrive_partition_into_virtual.shtml](http://www.softpanorama.org/VM/conversion_of_harddrive_partition_into_virtual.shtml)

there is alos some stuff in the FAQ on VMWare website and Virtual box i remember from doing it a few years back.

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

So i am sure methods have improved by now

---

### Post by Quackers on 2011-07-10
Yes, but with a couple of proviso's.
Firstly make sure you don't have 4 primary partitions already in use. 4 is the maximum on a mbr partitioned disc. Creating a 5th primary partition will cause big problems! Also bear in mind that with a swap partition you would need at least 2 new partitions to install Ubuntu (or an extended partition with logical partitions within it).
Secondly your Ubuntu partition has to be big enough to contain a virtual partition the size of your proposed Windows system plus enough space for Ubuntu itself.

---

### Post by haqking on 2011-07-10
> **Quackers said:**
> Yes, but with a couple of proviso's.
Firstly make sure you don't have 4 primary partitions already in use. 4 is the maximum on a mbr partitioned disc. Creating a 5th primary partition will cause big problems! Also bear in mind that with a swap partition you would need at least 2 new partitions to install Ubuntu (or an extended partition with logical partitions within it).
Secondly your Ubuntu partition has to be big enough to contain a virtual partition the size of your proposed Windows system plus enough space for Ubuntu itself.


actually what i though he meant was take his existing build/partition which has windows installed and take a copy of that to virtualise in a VM under Ubuntu.

Which he can and has nothing to do with the partitions, the current partition with Windows in it will become a VHD for use under whatever virtualisation software he wants to use.

he does not need to create or modify any partitions.

The simplest way apart from using any conversion software is how i did it which was to take a image of that partition, then blow it back into a VHD you have already created.  With windows there are some HAL issues which can be overcome fairly easily however.

---

### Post by Mark Phelps on 2011-07-11
Don't know if THIS is what you want to do ... but ...

Read a while back of folks trying to use Virtualization to run an EXISTING Win7 install but inside a VM -- by (somehow) pointing the VM to the existing install.

Good news -- it worked, kind of.

Bad news -- it forced reactivation every time you started the VM.  Eventually, you run out of reactivations and it won't start any more.

---

