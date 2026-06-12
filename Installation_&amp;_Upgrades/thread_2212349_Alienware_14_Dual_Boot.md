---
title: "Alienware 14 Dual Boot"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by Reivajxxx on 2014-03-20
Dear all,
I know this thread have been in everywhere as in almost everywhere I have searched for it too so this is a long specific question that I don’t know how to ask in short :shock:. So please don't go mad .

Trying to dual boot Ubuntu 12.04 64 bits and Win 8 pre-installed This is what I have don’t until now hoping that some nice soul over there guide me in the process. ...

The problem here is UEFI . Using live cd of Ubuntu 12.04 64 bits on the Alienware 14 (trying UEFI boot and secure mode  first): 

1) I'd resized the disk using the win 8 utility. ( didn't touch any other partitions that belongs to recovery or uefi )
 
2) Booting from Ubuntu live cd, as we know first, there is a menu asking to try or install Ubuntu directly and in my case both options lead me to an error saying,  that I need to load the kernel first ?? . 

2) Now, If I disable Secure boot and UEFI mode ( back to legacy boot) the live cd works and it boot normally , guessing that when the installation process ends grub will take care about windows boot and it should but...

3) When I reach the moment to select the partition already prepared for Ubuntu , I need to create a swap area (no problem), and place for my Ubuntu Installation on / (no problem). 

4) In this part, what I don't understand from other workarounds  is that I should use the same space reserved for UEFI that Windows use which is no more that 500 mb which is like a boot partition, so I don't know If I should mark this UEFI partition which windows use as /boot flag or not because the true is that Ubuntu does not recognize it automatically and it warn me that if I continue the installation can go wrong. Here is where I'm confused in a loop of doubts . Is ther a way to do this in the old "normal" way? .  Thanks any way for read this  :shock:   .

---

### Post by ubfan1 on 2014-03-20
Did you hashcheck the iso download with md5sum?  Did you burn the cd as slowly as possible and run media check on it?  At your initial boot of the CD, with secure boot on, if you got to the black grub screen, you have successfully run the secure boot gauntlet (until you get to trying to boot the installation off the hard disk anyway).  
  When you turn off UEFI mode (and secure boot), anything you install will incompatible with Windows which require UEFI mode and maybe secure boot.  Usually, boot-repair will fix these problems, but best to just try things in order, and when something fails (like if you live media wont boot) then try changing things like UEFI mode.  The EFI partition holds the UEFI bootloaders, ubuntu's included.  They are just put into a FAT filesystem, and usually, there's lots of space for the Ubuntu additions.  The UEFI machine has a list of bootloaders in memory (nvram), and the order they are tried may be changed (with a tool like efibootmgr).  Before actually changing their order, you can try them out from the efi menu, which is usually invoked with a function key (varies by machine) right after power on. UEFI Settings/BIOS usually have a user selectable delay at boot time to allow you to type such a key -- set it to something other than "0" or if delay seconds are not offered, use "normal" instead of "fast" on the "boot speed" choice.  This also assumes you have on the Windows side power settings turned off "fast startup", since that short circuits the boot process, and just restores a Windows system image from disk.

---

### Post by Reivajxxx on 2014-03-20
Thanks for the reply ubfan1.  
Ok, I didn't check with md5sum (never do), first  thing to do now then. I was just hoping that setting on legacy mode the boot, Ubuntu  installation and grub will do the trick ( lazy) but obviously more  things to understand and do before, thanks for the enlightenment :) . 
The honest truth is that in the end I will just install Ubuntu and nothing else. I wanted to keep Windows just for the warranty issue ( new laptop) . In the case I just wanted to wipe out Windows completely and just keep Ubuntu I suppose that with legacy boot mode will be enough ?.    ( thanks for the complete answer ;)  ).

---

### Post by Reivajxxx on 2014-03-21
For the record.
I managed to dual boot Windows 8 and Ubuntu 12.04 64 bits + Alienware 14 on this way :
( the Ubuntu live cd will not boot on UEFI mode on this laptop, the iso and cd are ok , is just like that for this laptop with 12.04 installation, in order to boot
on UEFI mode follow this, here I understand that you already resized the disk to let some space for Ubuntu installation)

1) Start computer press F2 for setup
2) From boot menu disable UEFI and secure boot and choose legacy .
3) Press F10 to save changes and reboot pressing F12 for boot options.
4) From boot menu choose boot options and select UEFI and Secure boot ( I know just keep reading).
5) Choose try Ubuntu and wait.
6) From desktop choose install Ubuntu and follow the usual steps until reach the part were you have to select "erase full disk" or do "manual partition."
7) Select the option that takes you to do the **manual partition**
8) From the free space you already created before, you must create a /swap area and the select the / mount point, don't mess with the other partitions already created for windows, just take not about the partition labeled as efi ( already created for Windows).

9) Now there is an option to choose the partition that have the  boot info for UEFI, in my case was /sd1, labeled from windows as efi, select this partition,
this will be were Ubuntu will add the boot information for UEFI.

10) now just select install and the all the next do is what you always do to install Ubuntu (before UEFI appeared in our world).

11) After the installation finish, remove the disk and go again to the BIOS pressing F2 . 
12) Here go again to boot menu and activate again UEFI and Secure boot ( I know I know)
13) Save the changes and restart , you will see now that Ubuntu boot by default and nothing happen with windows, don't panic.
14 ) Ones in Ubuntu follow this procedure to restore grub  and the possibility to select which OS will start  ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)),
I just selected the recommended repair from Boot-Repair .
15) When boot-repair finish his process will tell you that turn off Secure boot, which in my case did but I noticed that if I do not turn off this option it works anyway.


(Now, the other option is to fully install Ubuntu with no dual boot and you can skip all this mess :neutral:)  ... enjoy.

---

