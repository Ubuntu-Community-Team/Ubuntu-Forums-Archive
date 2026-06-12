---
title: "Ubuntu won't boot after install"
date: 2019-03-14
forum: Installation &amp; Upgrades
---

### Post by rodrigoma on 2019-03-14
Hi. Can anyone help me?
I have an SSD where I had win10 installed. Now I've installed Ubuntu 18.04 LTS and I chose to delete everything from the SSD during installation but now Ubuntu only boot from liveUSB. I've already tried to boot repair but it didn't work. here is the output of boot repair: [paste.ubuntu.com/p/yDVdrQnqQN]("http://paste.ubuntu.com/p/yDVdrQnqQN")

---

### Post by yancek on 2019-03-14
Your boot repair link is broken.

---

### Post by rodrigoma on 2019-03-14
Working fine here 



[IMG]https://i.imgsafe.org/af/af70d15978.png[/IMG]

---

### Post by sbnwl on 2019-03-14
> Please do not forget to make your BIOS boot on sda (ATA KINGSTON SUV400S) disk!

The boot files of [The OS now in use - Ubuntu 18.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


Did you have a boot partition? Apparently not, as is reported in your logfile.

---

### Post by oldfred on 2019-03-14
Please use clickable link:
[http://paste.ubuntu.com/p/yDVdrQnqQN/](http://paste.ubuntu.com/p/yDVdrQnqQN/)

       BIOS is EFI-compatible, but it is not setup in EFI-mode for this installed-session. 

You have installed in the now 35 year old BIOS/MBR configuration. 
The far from start of drive is an old error primarily with IDE drives and old BIOS that could not boot from beyond the first 137GB of a drive. Have yet to see a newer UEFI system using AHCI for drives have that issue.

What brand/model system?

But you should be able to boot in the old mode as UEFI has that as CSM:
      
  CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Do you have your UEFI set to boot in the old BIOS/Legacy/CSM boot mode?

---

### Post by rodrigoma on 2019-03-15
> **sbnwl said:**
> Did you have a boot partition? Apparently not, as is reported in your logfile.

I installed again, this time with a boot partition. Same problem. Run boot repair and didn't work as well. Here is the log: [http://paste.ubuntu.com/p/rv6kGtc8N8/](http://paste.ubuntu.com/p/rv6kGtc8N8/)[URL="http://paste.ubuntu.com/p/rv6kGtc8N8/"]
[/URL]
> **oldfred said:**
> Please use clickable link:
[http://paste.ubuntu.com/p/yDVdrQnqQN/](http://paste.ubuntu.com/p/yDVdrQnqQN/)

       BIOS is EFI-compatible, but it is not setup in EFI-mode for this installed-session. 

You have installed in the now 35 year old BIOS/MBR configuration. 
The far from start of drive is an old error primarily with IDE drives  and old BIOS that could not boot from beyond the first 137GB of a drive.  Have yet to see a newer UEFI system using AHCI for drives have that  issue.

What brand/model system?

But you should be able to boot in the old mode as UEFI has that as CSM:
      
  CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Do you have your UEFI set to boot in the old BIOS/Legacy/CSM boot mode?

My mother board is a [Gigabyte GA-78LMT-USB3 rev5]("https://www.gigabyte.com/us/Motherboard/GA-78LMT-USB3-rev-50#sp").  I looked for some UEFI in my BIOS but found nothing. I'm completely lost. 

[URL="http://paste.ubuntu.com/p/rv6kGtc8N8/"]
[/URL]

---

### Post by rodrigoma on 2019-03-15
One more thing, every time I try to start Ubuntu from GRUB I have the message above repeated some times:

> ACPI Error: AE_NOT_FOUND, While resolving a named reference package element - LNKC (20180531/dspkginit-414)

Ubuntu won't start in 90% the times after this message.

---

### Post by oldfred on 2019-03-15
Have you updated UEFI/BIOS for your motherboard to latest available?

Gigabyte AMD based boards need IOMMU turned off in UEFI and perhaps boot parameter.

       Gigabyte E2200 Killer Set grub IOMMU first, then UEFI setting or mouse/keyboard will not work
[URL="https://ubuntuforums.org/showthread.php?t=2347115"]https://ubuntuforums.org/showthread.php?t=2347115
      [/URL]
 Some Gigabyte boards need acpi=off boot parameter also
Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 
    [URL="https://ubuntuforums.org/showthread.php?t=2347115"]
[/URL]

---

### Post by flyn633 on 2019-03-15
Is everything fine with BIOS and Bootloader? Do check with them!

---

