---
title: "Cannot Boot into New Linux Partition"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by jacob5 on 2013-09-02
Hi,

I recently attempted to install Linux Mint 13 alongside  Ubuntu 12.04 LTS and Windows 7. The medium that I used to do this was a  flash drive that I burned the Mint iso to using 
```
dd

```

 During the installation process, I meant to shrink my Ubuntu partition  in order to make room for Mint, but I formatted my Ubuntu partition by  accident. Now I cannot boot into Linux Mint, and I have re-installed it  several times in order to try different install options. I even tried  re-installing Ubuntu to see if it would fix the problem, but it didn't  work, and I could not boot Ubuntu either.

The old Ubuntu partition is still listed as a boot option  in the BIOS, even though I have tried to delete it. When I choose that  option, however, I only get the GRUB rescue screen. When I try ```
ls (hdx, gptx etc.)

```, trying all of the availible partitions, it outputs the message "no such filesystem."

I  have also tried using Boot Repair, first with the recommended options,  and then with some advanced options, including purging GRUB and  completely reinstalling it.

Here is my partition setup:

         [ATTACH=CONFIG]245934[/ATTACH]
         


The unallocated space is where Ubuntu used to be, and also where I have tried installing Mint several times.

Windows 7 still boots by the way.

In a nutshell, I just cannot access the GRUB menu to access any Linux partitions. I cannot access them from the BIOS either.

Any insight into this problem will be very much appreciated! [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by oldfred on 2013-09-02
Most Windows 7 systems were BIOS with MBR partitions, but you have an efi partition and the Microsoft reserved partition which indicates the new UEFI install with gpt partitioning. But you will not have any of the Windows 8 secure boot issues.
You have to install Linux in UEFI mode and have to boot installer in UEFI mode to get them to install in UEFI mode. You may be able to dual boot a BIOS install by going into UEFI menu, turn on the CSM/BIOS mode and boot in BIOS mode. But then to boot Windows you have to go into UEFI and turn on UEFI to boot in UEFI mode. Not the easiest way to dual boot.

With Ubuntu Boot-repair can convert a BIOS install to UEFI, but I have no idea bout Mint or how compatible it is with UEFI.

More info on UEFI in my signature. Review the first couple links as they have screen shots of UEFI installs.

---

### Post by jacob5 on 2013-09-03
> **oldfred said:**
> Most Windows 7 systems were BIOS with MBR partitions, but you have an efi partition and the Microsoft reserved partition which indicates the new UEFI install with gpt partitioning. But you will not have any of the Windows 8 secure boot issues.
You have to install Linux in UEFI mode and have to boot installer in UEFI mode to get them to install in UEFI mode. You may be able to dual boot a BIOS install by going into UEFI menu, turn on the CSM/BIOS mode and boot in BIOS mode. But then to boot Windows you have to go into UEFI and turn on UEFI to boot in UEFI mode. Not the easiest way to dual boot.

With Ubuntu Boot-repair can convert a BIOS install to UEFI, but I have no idea bout Mint or how compatible it is with UEFI.

More info on UEFI in my signature. Review the first couple links as they have screen shots of UEFI installs.

Hi, thank you for your reply!

I will try to install Linux in UEFI mode. 

I was dual dual-booting both Windows and Ubuntu with no problems before I accidentally formatted the Ubuntu partition. However, Windows will boot whether I have UEFI turned on or not.

---

