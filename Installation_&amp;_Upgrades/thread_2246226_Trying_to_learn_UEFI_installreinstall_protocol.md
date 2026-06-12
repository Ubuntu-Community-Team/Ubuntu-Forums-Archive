---
title: "Trying to learn UEFI install/reinstall protocol"
date: 2014-09-29
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2014-09-29
I asked ***oldfred*** for some guidance in [another thread]("http://ubuntuforums.org/showthread.php?t=2242470") where I was trying to help out and he was kind enough to post some great links.

I know in that case that the / (aka; root) partition is on /dev/sda8 as shown in the [screenshot of Gparted]("http://ubuntuforums.org/attachment.php?attachmentid=256785&d=1411955740"). And I know that swap partitions always get reused unless specifically telling the installer not to.

But I knew nothing about UEFI until reading [this]("https://help.ubuntu.com/community/UEFI"), now I know just enough to ask a stupid question :)

[Here]("https://help.ubuntu.com/community/UEFI#General_principle") it says:

> if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition

Then reading a bit further [here]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition") it says:

> no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically

So would I be correct in telling that user to simply choose Something else, then select /dev/sda8 (which can also be identified as being the only existing ext4 partition) and reformatting it as ext4 again, and then just setting the mount point as / ............... and that's all?

---

### Post by Dennis N on 2014-09-29
If you are setting up the paritions in gparted, use Partition > Manage Flags to mark the EFI system partition with "boot".  The ubiquity installer will then detect that boot flag and automatically set the mount point, which will show in the "mount point" column as /boot/efi (on the same screen where you choose the / partition). If you don't set the boot flag with gparted, the installer won't set the mount point. Be sure to set the location for grub install as well.

---

### Post by kansasnoob on 2014-09-29
So looking at [this screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=256785&d=1411955740") I'd assume that /dev/sda2 is the /boot/efi partition. And that would be verified during installation in the mount point column?

I'm smart enough to know that the /boot/efi partition must NOT be reformatted, or am I mistaken about that?

---

### Post by oldfred on 2014-09-29
With UEFI, drive must be gpt partitioned. (may be an exception but do not for sure.)
Windows only boots in UEFI mode from a gpt partitioned drive.
Both Ubuntu & Windows only boot in BIOS mode from a MBR(msdos) drive.
Ubuntu can boot in UEFI mode if you have an efi partition or in BIOS mode if you have a biso_grub partition from a gpt partitioned drive. 

Only one efi partition per hard drive. All systems add folders with boot  files and UEFI reads each folder for booting. Somewhat like having many MBR all on one drive.

How Ubuntu installs is based totally on how you boot install media. Live install has both syslinux and /boot efi folder. And UEFI should have two boot options. Often one is clearly UEFI and the other is just the label of the flash drive. Many users boot flash drive and end up with a BIOS boot install of Ubuntu on a UEFI Windows system. Boot-Repair can convert install from BIOS to UEFI by uninstalling grub-pc and installing grub-efi-amd64.

We now often ask users to run both sudo parted -l and sudo fdisk -lu. the parted list will work with MBR or gpt. The fdisk only reports the protective MBR's single entry of the drive being gpt. With gpt they include a protective MBR so older tools like fdisk will not think drive is blank and offer to format it. And then MBR can be used for a BIOS boot loader.

I have used gpt partitioning on my new drives & flash drives since 10.10, but can only boot with BIOS.

If Windows is installed you can tell if BIOS as it usually has the 100MB boot partition and main install. With UEFI you have the efi partition and Windows has a unformatted space labeled msftres of usually 128KB. That is for all the hidden Windows likes to save and in BIOS mode saves after the MBR in the same area grub2 writes. With gpt there is no space after the protective MBR.

---

### Post by Dennis N on 2014-09-29
> **kansasnoob said:**
> So looking at [this screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=256785&d=1411955740") I'd assume that /dev/sda2 is the /boot/efi partition. And that would be verified during installation in the mount point column?

I'm smart enough to know that the /boot/efi partition must NOT be reformatted, or am I mistaken about that?

Yes, that's all correct. Windows and Linux will share the same EFI system partition - Ubuntu will place a folder EFI/ubuntu in there when you install, and mount it at /boot/efi. You don't format sda2 - if you did you would wipe out Windows files there.

---

### Post by Bashing-om on 2014-09-29
kansasnoob; Hey !

I am introduced to a good tutorial written up by an IRC guru of linux (TJ-):
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)
That I am sure you too will find informative.

[INDENT][INDENT]all in this together
[/INDENT][/INDENT]

---

### Post by slickymaster on 2014-09-29
> **Bashing-om said:**
> kansasnoob; Hey !

I am introduced to a good tutorial written up by an IRC guru of linux (TJ-):
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)
That I am sure you too will find informative.
[INDENT][INDENT]all in this together
[/INDENT]
[/INDENT]


Fabulous guide, Bashing-om. Thanks a lot for the tip.

---

### Post by Bashing-om on 2014-09-29
> **slickymaster said:**
> fabulous guide, bashing-om. Thanks a lot for the tip.

:)

---

### Post by ubfan1 on 2014-09-29
@oldfred
> With UEFI, drive must be gpt partitioned. (may be an exception but do not for sure.)
UEFI does not require a gpt drive -- e.g. the live media which is msdos partitioned.

---

