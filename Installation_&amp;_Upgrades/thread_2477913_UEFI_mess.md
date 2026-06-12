---
title: "UEFI mess"
date: 2022-08-10
forum: Installation &amp; Upgrades
---

### Post by f00dl3 on 2022-08-10
I'm having a nightmare with UEFI. Long story short I got a new build - i9 12900K + MSI B660-a board that strictly appears to enforce UEFI.

I had a working clean install but then messed it up using CloneZilla to try to back up the drive. Somehow in the process of mirroring the disks it threw a GPT MBR error. After rebooting it appeared that it wiped grub or corrupted EFI.

I followed steps to try to repair the grub bootloader by using boot-repair - but it said NVRAM is locked. I then attempted to reinstall grub, but it stated it was unable to "set" EFI - even though efivars was already mounted and not empty.


So clean install time again - but now it appears that is not even able to get EFI working. I tried clean installing from USB twice wiping the disk, but it won't boot and does not detect any UEFI partition.

I'm at the point where I'm going to have to buy a new $200 SSD because it appears somehow the EFI is hosed.


Anyone else have this happen have any ideas? I'm at a loss.

---

### Post by ubfan1 on 2022-08-10
Have you checked for any firmware updates for the B660 MB?  What version of Ubuntu are you trying to install and what kernel version (you probably need the latest available).  The SSD i probably fine, it just needs a 300MB EFI partition to hold shimx64.efi, grubx64.efi, and a stub grub.cfg which imports the maintained g rub.cfg off your root. Those three files go into the EFI's EFI/ubuntu directory, and a copy of grubx64.efi and shimx64.efi go into EFI/Boot (with shimx64.efi renamed to bootx64.efi).  The device should then boot even without an nvram entry.

---

### Post by oldfred on 2022-08-11
NVRAM locked sounds like an UEFI setting.
Are you dual booting with Windows?

---

### Post by f00dl3 on 2022-08-11
> **oldfred said:**
> NVRAM locked sounds like an UEFI setting.
Are you dual booting with Windows?

I have not used Windows for personal use since 2013 so it's nothing to do with Windows.

---

### Post by f00dl3 on 2022-08-11
> **ubfan1 said:**
> Have you checked for any firmware updates for the B660 MB?  What version of Ubuntu are you trying to install and what kernel version (you probably need the latest available).  The SSD i probably fine, it just needs a 300MB EFI partition to hold shimx64.efi, grubx64.efi, and a stub grub.cfg which imports the maintained g rub.cfg off your root. Those three files go into the EFI's EFI/ubuntu directory, and a copy of grubx64.efi and shimx64.efi go into EFI/Boot (with shimx64.efi renamed to bootx64.efi).  The device should then boot even without an nvram entry.

I'm going to go ahead and get a new drive today probably a M.2 form factor and just RMA the drive in question. I'm pretty sure now it's a drive issue as the live CD can not even mount it with write access. It's just weird this all happened when trying to back the drive up. It's under warranty as it's only 11 months old and well under the TBW rating.

---

### Post by ubfan1 on 2022-08-11
You might have just overwritten the partition table, so then of course, nothing would be mountable (without the loop option, ha).  What does the output of sudo gdisk -l /dev/sda or /dev/nvme0n1 or whatever your disk is.  First thing might be to then use gdisk to make a partition, then mkfs on the partition, then you may mount it.

---

