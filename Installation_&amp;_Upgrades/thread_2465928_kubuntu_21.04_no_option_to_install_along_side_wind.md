---
title: "kubuntu 21.04 no option to install along side windows"
date: 2021-08-15
forum: Installation &amp; Upgrades
---

### Post by billb32 on 2021-08-15
I have a win10 machine with 80 gig unused ( not formated)

kubuntu 21.04 only offers to overwrite windows, not to install seperately

help

---

### Post by monkeybrain20122 on 2021-08-15
Does it have a manual/advanced install option?

---

### Post by ajgreeny on 2021-08-15
Assuming the installer of Kubuntu is the same as Ubuntu I think you will find it easier to select the "Something Else" option at the disk formatting stage.
This should show all disks, partitions and unallocated space available in the computer, giving you the option of pointing the install to wherever you want it.

As you have Windows 10, which will undoubtedly be installed in UEFI mode, it is essential that your USB used to install Kubuntu is booted in UEFI mode; are you certain that was the case?

---

### Post by yancek on 2021-08-16
What options do you see when you click the Install Kubuntu icon?  Generally, there will be an option to overwrite the drive and install Kubuntu, use encryption which will also overwrite the drive or a manual option, ususally called Something Else.  If windows is installed and recognized by Kubuntu, there should be an Install Alongside windows.  If windows is not recognized it may be that windows is hibernated which will have to be turned off first.  Best to indicated which option you selected and the specific results if you have not resolved this issue.

---

### Post by ActionParsnip on 2021-08-16
Run a full fsck on the NTFS.

---

