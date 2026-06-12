---
title: "Installing Ubuntu alongside Windows 8 in UEFI"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by handsheldhigh on 2013-01-16
Hello, 
 
When I go to install Ubuntu 12.10, the partitioning step does not give me the option to install alongside Windows 8. Would I have to manually create a partition to direct Ubuntu to install on? I used Windows 8's built in disk management to shrink my Win8 partition, so do I just install Ubuntu on the free space?
 
Also, is there any advantage to using Windows' bootloader over GRUB with EasyBCD? I asked a different forum and someone mentioned it.

---

### Post by handsheldhigh on 2013-01-16
Should I just follow [https://help.ubuntu.com/community/UEFI#General_principle](https://help.ubuntu.com/community/UEFI#General_principle) and do that? 
 
P.S. I have secure boot turned off.

---

### Post by IncendiaryPyro on 2013-01-16
I'd like to know this also. Bought a new laptop a few weeks ago that came with Windows 8, and when I booted into the live disc, it didn't see my Windows 8 partition and only gave me an option to erase the partition or manually make a new partition.

---

### Post by grahammechanical on 2013-01-16
You both might want to read through this.

[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

with 12.10 we do not necessarily need to turn secure boot off because Ubuntu 12.10 has a kernel that has been signed with a key the Windows machines with secure boot will accept.

Regards.

---

### Post by handsheldhigh on 2013-01-16
> **grahammechanical said:**
> You both might want to read through this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

with 12.10 we do not necessarily need to turn secure boot off because Ubuntu 12.10 has a kernel that has been signed with a key the Windows machines with secure boot will accept.

Regards.

So if I free up some space by resizing down my WIn8 partition,  I can install Ubuntu on the free space left over? Can I use the Win8 bootloader?

---

### Post by oldfred on 2013-01-16
Grub2 is designed to multi-boot, Windows has no concept of multi-boot beyond another copy of Windows. I think they may have updated EasyBCD to work with UEFI but there is no need.

With UEFI you do not have one MBR with one boot loader. You have an efi partition and every system you install that works with UEFI adds a folder with its boot files. It is like having an unlimited number of MBRs. 

Grub does have a bug in its os-prober and needs fixes to chain load back to the Windows efi boot loader. Grub still creates MBR type chain entries. Bug report has ways to manually fix or you can run Boot-Repair and it will add correct entries to 25_custom.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by djmac on 2013-03-03
Hi handsheldhigh - what do you end up doing?? 

I have been able to boot ubuntu via a Live USB (as per [here]("https://help.ubuntu.com/community/UEFI") - but like you the partitioning step does not give me the option to install alongside Windows 8... (and unlike IncendiaryPyro I can see about 7 different partitions for windows...) 

If you did manually partition, did you do it through windows 8 first? (or perhaps gparted??) Or did you end up finding a way to "install alongside Windows 8"

Cheers

---

### Post by oldfred on 2013-03-04
@djmac
Better to have your own thread. Boot issues vary a lot by type of system.
What hardware, and is it an UltraBook? That uses RAID so standard desktop installer does not see drives.

---

### Post by s-manuj545 on 2013-08-19
Hi ,even i was stuck with this for some time. Actually after installing ubuntu on machine which has windows 8 pre installed with UEFI (as oppose to those with LEGCY BIOS) ,you need to update the grub for ubuntu.
Here is a link which shows how to do this stepwise.
[http://binarybyte.blogspot.com/](http://binarybyte.blogspot.com/)

Hope it helps..

---

