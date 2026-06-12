---
title: "MBR/partition Issues on netbook &amp; win7"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by krylonultraflat on 2010-10-21
OK so it would seem borking your MBR/Grub while trying to delete an Ubuntu partition is a common problem.  My circumstances don't seem to be so common and I was wondering if I could get some help.  

Using an EEE netbook w/ Windows 7.  I Installed Ubuntu from a bootable thumb drive a while back.  

Here's a somewhat simplified chain of events:
1. Booted onto said thumb drive and deleted the Ubuntu partition using gparted
2. GRUB goes into recovery mode and panics 
3. I boot off the thumb drive into ubuntu and Install/run Lilo before using the following command:
*sudo lilo -M /dev/sda mbr*
(note: sda1 appears to be my windows partition but Lilo gives me an error when I try to use the above command with it)
4. Upon rebooting, get a Windows Boot error message & a request for a recovery disk, specifically:
[I]Status 0xc0000225
Info: The boot selection failed because a required device is inaccessible[/I]

So I am very far away from my recovery CD and furthermore don't even have a CD drive as (again) this is a netbook.  

Does anyone have any advice at this point for restoring my Windows MBR?  Is this even an MBR issue or a partition issue at this point?  

Thank you in advance for any advice!!!

---

### Post by ronparent on 2010-10-21
In a way it is a MBR issue. Plus when you deleted the Ubuntu partition it must be the one where your grub was located. If you have another Ubuntu/Linux partition you could reinstall grub there. You might be able to restore the Win MBR with the live cd - but someonelse will have to tell you how.

The grub code in the MBR is in effect only a pointer to where the grub program and configuration data is located. If that location no longer exists grub is useless.

---

