---
title: "Ubuntu sometimes does not boot correctly"
date: 2020-06-26
forum: Installation &amp; Upgrades
---

### Post by justanto on 2020-06-26
Hi!

I have a Thinkpad T495 and I decided to install Ubuntu alongside Windows 10.

To install Ubuntu I followed the instruction presented by the installer and selected the option "Install alongside Windows 10" when the installer asked me in which disk to install Ubuntu.

GRUB seems to work fine and 100% of the times I can boot into Windows 10 without any issues, the problem comes when I try to boot into Ubuntu, sometimes works and sometimes it doesn't and just freeze in a black screen after selecting Ubuntu in GRUB.

I tried running boot-repair tool and it when i click on auto-repair and I got this message:

"Please create a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as Gparted. Then try again."

The boot info summary info is available here: [https://paste.ubuntu.com/p/nY7j8qKnpJ/](https://paste.ubuntu.com/p/nY7j8qKnpJ/)

Any idea of what is the cause of the problem? I don't understand why sometimes it boot in seconds and some it's just a black screen :S
Thanks

---

### Post by CelticWarrior on 2020-06-26
Welcome.

Thank you for making the effort and presenting Boot Repair's summary report, it's always good to have a look at those things, but if "GRUB seems to work fine" then there's no point in using Boot Repair. The problem comes *after* Grub and the purpose of Boot Repair is exclusively install or reinstall Grub.

Knowing that the T495 line is AMD Ryzen based I suggest updating UEFI before anything else. Also update firmware of any SSDs, if applicable. Then, as usual for any dual-boot with Windows 8 or newer, disable Fast Startup in Windows.

---

### Post by justanto on 2020-06-26
Thank you very much for the answer, could you tell me how to update UEFI and SSD firmware?

---

### Post by CelticWarrior on 2020-06-26
Go to the vendor's and find if there's an update - "BIOS" (although it really isn't and hasn't been for 10 years +) - UEFI or "UEFI BIOS" is the section you should be looking for.
The same for the SSD manufacturer.

---

### Post by justanto on 2020-06-28
Both seems to be updated to the newest version, Fast Startup is also disabled.

 I thought it could be an ACPI problem and tried to boot with the command acpi=off but that makes it unable to boot into Ubuntu. Any more ideas?

Edit:

It seems to be a general problem, after searching in Reddti for a while I found this post: [https://www.reddit.com/r/thinkpad/comments/gbk1zq/new_t495_upgraded_to_24_gig_ram_and_1_tb_ssd_now/](https://www.reddit.com/r/thinkpad/comments/gbk1zq/new_t495_upgraded_to_24_gig_ram_and_1_tb_ssd_now/)
and this comment:
[I]
"Love my t495. I will have to caution you on booting into ubuntu based  distros on this thinkpad. There is a continual and annoying issue with  booting while on battery on kernels older then 5.6 or 5.7. The laptop  wont always boot in linux on battery and is very inconsistent. There is a  work around setting some video setting to immosoft or something like  that that has worked. I&#8217;ve tried elementary, mint  and even ubuntu  20.04."[/I]

My kernel version is 5.4 but this seems to be the issue since I have been trying and every time I boot with the power cable connected it works :S

---

### Post by CelticWarrior on 2020-06-29
> *there is a  work around setting some video setting to immosoft or something like  that that has worked. *

It's actually ```
IOMMU=soft
``` but NOT a video settings and yes, you should definitely try it although I wouldn't bet on it. This used to be needed for some AMD based boards with broken IOMMU from around 6 years ago (?). At least for the old ones something at the kernel level was added and the boot parameter was no longer needed. I installed Ubuntu 18.04 in one of those without any additional parameter.

---

