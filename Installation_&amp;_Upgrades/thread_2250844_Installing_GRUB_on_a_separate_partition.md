---
title: "Installing GRUB on a separate partition ?"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by Alexander_Paunovsk on 2014-10-31
How do I install Ubuntu so that GRUB will be on a separate partition ?

In short, I want my HDD to look like this:

```

Partition 1 WINDOWS 8
Partition 2 UBUNTU
Partition 3 SWAP
Partition 4 GRUB

```

My disk is GPT and I am using UEFI to boot (no MBR).

I Googled a lot and I can't seem to find an accurate answer.

Any help will be greatly appreciated.

---

### Post by Dennis N on 2014-10-31
Installing in UEFI mode, grub has to be installed to a special partiton called the EFI System Partion. It should already be there because Windows 8 in UEFI mode uses it, but you don't show it. You should be able to install grub to another EFI System partiton if you can create one - I don't believe there is a rule that you can only have one. But I've read reports that with ubiquity (Ubuntu's installer), you can't specify where it goes beyond indentifying the disk to be used (sda, for example). I haven't tried using a 2nd EFI system partition on a single disk myself so don't know if it will work.

I've also read that other distros will create a new EFI system partition for itself when installed. Either Fedora or Open Suse, or maybe both?

---

### Post by yancek on 2014-10-31
If you are using GPT/UEFI for windows 8, then Ubuntu also must be installed as EFI.  The efi files for both windows and Ubuntu should be on the same partition and it is usually the first partition on the drive formatted as FAT32.

---

### Post by Bucky Ball on 2014-10-31
> **Dennis N said:**
> I don't believe there is a rule that you can only have one. 

As far as I know you can only have one, for logical reasons.

---

### Post by Dennis N on 2014-10-31
> **Bucky Ball said:**
> As far as I know you can only have one, for logical reasons.

No, looks like you can have several, according to these:

> "the EFI specification imposes no limit on the number of ESPs that may be present on a computer or on a hard disk; you could have dozens of them if you wanted to, and that would be fine from the EFI's perspective."

[http://superuser.com/questions/688617/how-many-efi-system-partitions-esp-can-a-computer-have](http://superuser.com/questions/688617/how-many-efi-system-partitions-esp-can-a-computer-have)

> "Most distros will use an existing EFI system partition if there is one, though it’s perfectly valid to create a new one and use that instead: as we’ve noted, UEFI is a permissive spec, and if you follow the design logically, there’s really no problem with having just as many EFI system partitions as you want."

[https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

### Post by oldfred on 2014-10-31
I thought you could only have one efi partition per device. But was corrected that the spec does allow more than one (by the author of gdisk) but usually does not work. 

AND every UEFI implementation we have seen has not worked with more than one efi partition per drive/device. When drive has two efi partitions, then system has not booted and removing the second, it did work.

The efi partition can be considered more like the MBR in BIOS installs. Or just where grub2's boot loader is. It just has a chain load grub entry to the real install of grub in the Ubuntu install.

I have used a grub partition on flash drives, have not yet configured one with UEFI, yet. But there is little advantage and several disadvantages. You have to manually install grub, have to manually create and maintain your grub.cfg or menu. Generally easier just to add custom boot entries into the one install you use to boot into a 40_custom script.

---

### Post by Bucky Ball on 2014-10-31
@Dennis N: You stopped at the part you wanted to see on [THIS]("http://superuser.com/questions/68861...-computer-have") link. If you'd have read on you would have noticed that, as far as ESPs go,

 > Unfortunately, Microsoft is not so flexible;_* Windows officially supports just one ESP per disk *_(maybe per computer; I'm a bit foggy on that detail). I don't know about Windows 8, but the Windows 7 installer will flake out if it sees more than one ESP on a disk; the installation will proceed part of the way and then fail. 

As far as I know Win8 is no different. Happy to be proved wrong. So as I said, with a caveat, if you're running Windows and Ubuntu, you can only have one EFI partition.

---

### Post by Dennis N on 2014-10-31
> **Bucky Ball said:**
> @Dennis N: You stopped at the part you wanted to see on [THIS]("http://superuser.com/questions/68861...-computer-have") link. If you'd have read on you would have noticed that, as far as ESPs go,

 

As far as I know Win8 is no different. Happy to be proved wrong. So as I said, with a caveat, if you're running Windows and Ubuntu, you can only have one EFI partition.

The link doesn't work, but point taken on the restriction by Windows on the number of ESP partitions. So, OP won't be able to do it with Windows on his disk. I'm  interested in the use of two or more EFI system partitions on multiboot Linux-only systems to avoid the overwriting of the ESP boot folder when they have the same name (ubuntu) during installation - otherwise, some OSes on the disk can't be booted directly from the UEFI boot manager as intended by the UEFI scheme of doing things.

---

### Post by Bucky Ball on 2014-10-31
The first one you posted:

[http://superuser.com/questions/688617/how-many-efi-system-partitions-esp-can-a-computer-have](http://superuser.com/questions/688617/how-many-efi-system-partitions-esp-can-a-computer-have)

Sorry, unsure why it didn't work. This one should. It is copied directly from your post. ;)

---

### Post by Alexander_Paunovsk on 2014-11-01
Alright, so if I stick GRUB in the EFI partition as suggested, won't this destroy the Windows 8 bootloader, causing Windows 8 to stop booting at all ?

---

### Post by Bucky Ball on 2014-11-01
If Windows is installed in EFI then you:

* shutdown the machine;
* boot into the BIOS;
* switch off secureboot/fastboot;
* make sure you are installing Ubuntu in EFI;
* install Ubuntu and don't tell it to install grub anywhere: as it is being installed in EFI it will look for the existing EFI partition and use that.

And that should be it. You don't need to create a partition or tell Ubuntu where to put grub. Not in my experience and not with 14.04 LTS. 

An EFI partition stores ALL bootloaders for installed OSs. Ubuntu installing grub to the partition won't delete your Win bootloader.

---

### Post by oldfred on 2014-11-01
If you run this it will show your distributor:
  lsb_release -a

And UEFI uses the distributor as the efi folder. So if whatever system based on Ubuntu does not change it name like it really should, then you may have issue. 

Kubuntu had that issue before, should be fixed now:
      UEFI install broken when GRUB_DISTRIBUTOR!=Ubuntu (e.g. Kubuntu/UbuntuStudio) Mostly fixed in Saucy & Trusty
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417)

I have seen in Boot-Repair this which creates the ubuntu entry in UEFI:
grub-install: info: Registering with EFI: distributor = `ubuntu', path = `EFIubuntushimx64.efi', ESP at hostdisk//dev/sda,gpt2.

One advantage of UEFI is that every installed system, creates its own folder in the efi partition and UEFI then offers each as a boot option (when Vendor has not modified UEFI to only boot Windows).

Typical default folders dual booting with also rEFInd. The /EFI/Boot is a entry to boot hard drive.
/EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu
/EFI/refind/

But in all cases you should be backing up efi partition to another drive before and after any updates. No install like old grub to MBR is required. You can just copy files back into efi partition to reset boot. You may have to boot once or twice to get UEFI to re-read efi partition.

---

### Post by Bucky Ball on 2014-11-01
> **oldfred said:**
> 

 You can just copy files back into efi partition to reset boot. You may have to boot once or twice to get UEFI to re-read efi partition.

Nice tip at the end, oldfred, and thanks for all the good info, as usual.

---

### Post by Alexander_Paunovsk on 2014-11-01
> * shutdown the machine;
 * boot into the BIOS;
 * switch off secureboot/fastboot;
 * make sure you are installing Ubuntu in EFI;
 * install Ubuntu and don't tell it to install grub anywhere: as it is being installed in EFI it will look for the existing EFI partition and use that.

> * boot into the BIOS;
* switch off secureboot/fastboot;
I don't have such options at all in the BIOS. I am using the DX58SO motherboard, if this means anything.

> * make sure you are installing Ubuntu in EFI;
What do you mean ? How do I make sure I am installing it in EFI ? 

> * install Ubuntu and don't tell it to install grub anywhere: as it is being installed in EFI it will look for the existing EFI partition and use that
Actually, Ubuntu asks me somewhere at the end of the install process where to install the Bootloader and displays a long list of all of my partitions. Note that dev/sda is not an option on this list. The list is something like this:


```

/dev/mapper/isw_difechbgae_Volume0               Linux device-mapper(striped)(3.0TB)
/dev/mapper/isw_difechbgae_Volume0p1            Linux device-mapper(linear)(786.4KB)
/dev/mapper/isw_difechbgae_Volume0p2            Linux device-mapper(linear)(314.6MB)            
/dev/mapper/isw_difechbgae_Volume0p2
/dev/mapper/isw_difechbgae_Volume0p3            Linux device-mapper(linear)(104.4MB)
/dev/mapper/isw_difechbgae_Volume0p3
/dev/mapper/isw_difechbgae_Volume0p4            Linux device-mapper(linear)(134.4MB)
/dev/mapper/isw_difechbgae_Volume0p5            Linux device-mapper(linear)(3.0TB)
/dev/mapper/isw_difechbgae_Volume0p5
/dev/mapper/isw_difechbgae_Volume0p6            Linux device-mapper(linear)(21.0GB)
/dev/mapper/isw_difechbgae_Volume0p6
/dev/mapper/isw_difechbgae_Volume0p7            Linux device-mapper(linear)(17.8GB)
/dev/mapper/isw_difechbgae_Volume0p8            Linux device-mapper(linear)(8.6GB)  

```

Also, some entries like Volume0p6 seem to appear twice in a row on this list. I have no idea why tho.

---

### Post by Bucky Ball on 2014-11-01
In that case, use 'Something Else' when installing and the window after the partitioning section should ask where you want to instll grub. That may happen if you choose Install Alongside but I never use that option.

Also, if you've installed, easy way is with Boot Repair>Advanced Options and you can direct it to install grub to any partition you like.

Just reread your post. Are you running RAID or LVM or something? That's what that mapper stuff is all about I think. Outta my area of knowledge. You can only really go by the sizes.

---

### Post by oldfred on 2014-11-01
I look up that motherboard and do not see any reference to UEFI, just BIOS. It looks that it is from 2009 which was before most systems used UEFI?

And all the /mapper means you are using RAID or LVM. Both use the /mapper for partitions.
Is this a server install?
How many hard drives?

Post this from live installer:
sudo parted -l

---

### Post by Alexander_Paunovsk on 2014-11-02
> I look up that motherboard and do not see any reference to UEFI, just BIOS. It looks that it is from 2009 which was before most systems used UEFI?

Still, it supports UEFI. No option for Secure/Fast Boot tho.

> And all the /mapper means you are using RAID or LVM. Both use the /mapper for partitions.

Yes, I am using a fakeRAID 0.

> How many hard drives?

2

> Is this a server install?

No, a regular desktop install.

> Post this from live installer:
 sudo parted -l

If I run Ubuntu in LiveCD mode, the display driver crashes after like 1 minute and the system hangs. 

> 
In that case, use 'Something Else' when installing and the window after the partitioning section should ask where you want to instll grub. That may happen if you choose Install Alongside but I never use that option.

Yes, I am using the Something Else option, problem is I am not sure where to install Grub. I will try the EFI partition as suggested and post back.

>  Also, if you've installed, easy way is with Boot Repair>Advanced Options and you can direct it to install grub to any partition you like.

I tried that, but if I boot in LiveCD mode the system quickly hangs and becomes totally unresponsive due to the display driver crashing.

---

### Post by Bucky Ball on 2014-11-02
Well, you should probably get on top of why the display is crashing before doing anything else as you won't be able to install Ubuntu anyway.

When you get to the 'Try Ubuntu' 'Install Ubuntu' options, hit F6 and choose 'nomodeset' from the list that pops up. Proceed. Still crashing? Don't think this is the issue, but worth a try.

---

### Post by oldfred on 2014-11-02
I did see one install where the efi partition was inside the RAID, I had not expected that to work as I did not know that the UEFI would mount & read an efi partition inside RAID. But if UEFI/BIOS has built in RAID (fakeRAID) that would make sense that it should read the efi partition.
Most installs seem to have both an efi partition and a boot partition before the RAID in standard partitions.

With RAID you normally specify the root of the RAID not an MBR or the drive as the install location or:
 /dev/mapper/isw_difechbgae_Volume0

But the Ubuntu installer has not yet been updated to fully support RAID ( I think.). It does more than it used to.
With 12.04 we had the alternative installer for desktop RAID & LVM installs. Then with 12.10 they stopped doing the alternative installer and said to just use server installer and add desktop or upgrade from 12.04. They added that in the future they would add LVM & RAID to the Desktop installer. I do see LVM as an option in installer now, and several that have installed seem to have RAID drivers as system sees the RAID partitions. But most have reported issues with the install of grub, so maybe not fully implemented yet?

Boot-Repair usually adds the correctly drivers and installs grub also. 

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

