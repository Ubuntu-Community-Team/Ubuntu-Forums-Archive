---
title: "boot error: file '/boot/grub/x86_64-efi/normal.mod' not found."
date: 2015-09-12
forum: Installation &amp; Upgrades
---

### Post by parker-hugh on 2015-09-12
I have DELL Inspiron 15 3543 and I triple boot Linux Mint, Debian 8 and Windows 10 it has 8GB or RAM.

It  has been working well up till now, I could boot into any of the operating  systems without any problems, both linux distros were installed in UEFI mode, I verified this during the install by running...

```
$ ls /sys/firmware                        
  acpi  efi  memmap    # Output is good. If "efi" is listed, 
                              # succeeded in booting in EFI-mode. 
```


 I have been using laptop for past few months with no problem, but today I just switched on and find following  error message...

```
error: file '/boot/grub/x86_64-efi/normal.mod' not found.
entering rescue mode...
grub rescue> _

```
when i press enter nothing happens.

my Boot mode is set to: UEFI with Legacy OPROM; Secure boot: OFF

Is  it safe to boot into Boot Repair USB and click Recommended Repair? I  have used this in the past but never on a UEFI boot system.

I tried pressing F12 boot options during boot process and I can see 

```
UEFI OPTIONS:
ubuntu
debian
Windows Boot Manager
Onboard NIC (IPV4)
Onboard NIC (IPV6)
USB1 - UEFI OS(KingstonDataTraveler 2.OPMAP)   # this is my boot-repair-disk USB
```

So I selected USB1 boot-repair-disk and it booted boot-repair-disk ok

I clicked 'Create BootInfo summary' and following is the output.... [http://paste.ubuntu.com/12381284/](http://paste.ubuntu.com/12381284/)

I  haven't seen this before so not sure what I can do.  I am still  learning linux and am not sure how best to fix this with UEFI etc, so  any help would be appreciated.

---

### Post by parker-hugh on 2015-09-14
I decided to boot into Boot-Repair-Disk USB and clicked Recommended Repair, but got this message....
```
An error occurred during the repair.

Please write on a paper the following URL:
http://paste.ubuntu.com/12407404/

In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com 

Locked-ESP  detected. You may want to retry after creating a /boot/efi partition  (FAT32, 100MB~250MB, start of the disk, boot flag). This can be  performed via tools such as gParted. Then select this partition via the  [Separate /boot/efi partition:] option of [Boot Repair].
```
I'm not sure of the best way to proceed as I'm quite new to linux. I thought I already had a /boot/efi partition, I don't want to do anything that might make my laptop unbootable, does anyone have any suggestions? any help would be appreciated.

EDIT: I was wondering would it be a good idea to re-install Linux? would that create a new grub menu?

---

### Post by oldfred on 2015-09-14
Somehow you have a boot flag on sda13?
You should only have one ESP - efi system partition per device, formatted FAT32 with boot flag if using gparted or code ef00 if using gdisk. Actual code is really a very long GUID that tells UEFI to go there to find efi boot files. But if you have two where is it going?

>  /dev/sda13  1,933,342,720 1,935,439,871     2,097,152 EFI System partition



Use gparted and remove boot flag from sda13, keep it on sda1 only.

Then Boot-Repair may correctly work, if system does not boot. But you may need to run it twice? Once for each install. If not booting run the advanced grub uninstall/reinstall fix in Boot-Repair.

---

### Post by parker-hugh on 2015-09-15
> **oldfred said:**
> Somehow you have a boot flag on sda13?
You should only have one ESP - efi system partition per device, formatted FAT32 with boot flag if using gparted or code ef00 if using gdisk. Actual code is really a very long GUID that tells UEFI to go there to find efi boot files. But if you have two where is it going?



Use gparted and remove boot flag from sda13, keep it on sda1 only.

Then Boot-Repair may correctly work, if system does not boot. But you may need to run it twice? Once for each install. If not booting run the advanced grub uninstall/reinstall fix in Boot-Repair.

Thanks for your feedback, I removed the boot flag and I managed after running Boot-Repair twice to get boot working correctly. It has saved me a lot of work, I thought I would need to start from scratch again which would be a bit job. Very happy with the result. 

Thanks again for taking the time to help solve my problem. It is much appreciated.

Hugh

---

