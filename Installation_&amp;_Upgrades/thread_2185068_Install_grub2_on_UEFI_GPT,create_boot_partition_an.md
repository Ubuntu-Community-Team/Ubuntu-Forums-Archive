---
title: "Install grub2 on UEFI GPT,create /boot partition and transfer clonezilla image"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by helloworld1215 on 2013-10-31
I would like to do the following:

Given:

A Windows system on GPT and UEFI with unallocated space on which one wishes to deploy Ubuntu
An ubuntu partition, and seperate partitions for /boot and swap

Deploy a clone of the ubuntu partition on said windows system. 

In order to do that, one has to presumably:

Install grub2 on the MBR
Create a /boot and swap partitions for the ubuntu
Transfer the ubuntu clone to the new partition

Assuming the workflow specified is correct, the following questions arise:

1. Does one deploy a cloned boot partition?
2. What software does one use to create the /boot or modify it if necessary? (It would appear that from screenshots, BootRepair can create a seperate /boot for partition, however, the question arises, can BootRepair facilitate creation of a fresh /boot?)
3. What steps does one need to perform link the /boot to the cloned partition
4. What steps does one need to perform to add the newly cloned Ubuntu to grub2?

5. Is there an automated way to install grub2 to replace the windows bootloader, including performing the steps specified here: [http://www.wensley.org.uk/gpt](http://www.wensley.org.uk/gpt) 

The reason I ask #5 is because:

1. I installed Ubuntu (/boot, swap, os) on unallocated space on a UEFI GPT windows system. However, it did not (appear to) install grub and switching between OS is performed by specifying the boot order in BIOS. 
2. It is specified as a general instruction in the wiki to run BootRepair to presumably facilitate a fix to this but it is not explicitly specified if that is the problem at which the instructions are aimed at (ie the language is, running BootRepair solves most issues)
3. So does BootRepair perform #5 in a complete manner?
4. It is further specified in various instructions to boot relevant live cds with UEFI. In my bios, the boot order is specified by simply hitting enter on the menu phrase "UEFI Boot". Presumably, media booted in said boot order is booted with UEFI. Please confirm this is what the instruction specifies.

---

### Post by oldfred on 2013-11-01
With UEFI you do not install to a MBR, but every system installs to the efi partition in a folder. But two ubuntu would not be different, but you would have two entries in the grub menu.

Normally /boot not recommended for desktops and definitely must be separate or unique for every install if separate. Severs, encrypted systems and a few other cases may need a separate /boot that you create during the install with Something Else or manual install.
Boot-Repair does not create a new /boot, but will recognize it if the check the box that you have it. 

How you boot installer is how it installs. Every UEFI seems to be different and not all are clear as many have posted. But one is UEFI and the other BIOS/CSM/Legacy. This shows both a BIOS boot and an EFI  boot screen so you know for sure.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your link uses LVM, which I know little about. 

I do not suggest cloning, but just another install. If you really understand the inner workings you can clone but have to update all the UUIDs to new partitions UUID and reinstall grub2 so it has the new UUID. Or if your clone also included UUID (not recommended with gpt as it also has internal GUIDs) you must immediately change it as you cannot have duplicates, especially with gpt.
It is really easier just to reinstall in another partition.

---

