---
title: "Replace 20.04 with 24.04 and efi partition 100M"
date: 2024-07-19
forum: Installation &amp; Upgrades
---

### Post by forceofgravity on 2024-07-19
Currently I've W10/20.04 dual boot system with /boot/efi partition (/dev/sda2) size 100M. It's 35% full. I'm going to do clean install and replace 20.04 with 24.04. In manual installation it's possible to set mount point /boot/efi and choose the current efi-partition. In this case what happens to the old files of 20.04 in efi? Does the Ubuntu desktop installer replace the old files or should they be removed manually? The size 100 M is apparently minimun so is there risk to get it full?

There is also separate /home partition. Should it be formatted or could it just to be mounted to new system?

What else should be taken in to account in this case?

---

### Post by tea for one on 2024-07-19
> **forceofgravity said:**
> What else should be taken in to account in this case?
Have you backed up Windows 10 and Ubuntu 20.04 personal data?

100MB ESP was the default size for Windows 10
Ubuntu 24.04 ESP will default to 1GB

Are both installations on one disk?

---

### Post by forceofgravity on 2024-07-19
Yes, I've backed up personal data but I don't have disk images.

Both installations are on the same disk:
Device         Size Type
/dev/sda1    529M Windows recovery environment
/dev/sda2    100M EFI System
/dev/sda3    16M Microsoft reserved
/dev/sda4    100,3G Microsoft basic data
/dev/sda5    603M Windows recovery environment
/dev/sda6    28,6G Linux filesystem
/dev/sda7    7,7G Linux swap
/dev/sda8    95,4G Linux filesystem
/dev/sda9    698,4G Microsoft basic data

I know that recommended ESP size is more than 100 MB, but is it enough for 24.04? Now dual boot W10/20.04 use only 30 MB of 100 MB.

I have understood that resizing ESP is not easy and straightforward thing and I will go that only if it's mandatory.

---

### Post by yancek on 2024-07-19
If you install 24.04 over 20.04 (using the same partitions) it will overwrite all EFI files on that partition and use the new EFI files to boot 24.04.
If you have a separate /home partition and select to format it, that will delete everything on the partition so select to use/mount it as /home but do not format.
If you only have windows and ubuntu in the directory, 100MB might be enough if you do not install other systems.

---

### Post by Dennis N on 2024-07-19
My Ubuntu 24.04 ESP size is 100 MB and ESP usage is just 13 MB on this machine. But this 24.04 is an upgrade from 23.10. I'm not sure the new installer will accept an ESP smaller than 1 G with a new installation, even with an existing ESP. You will have to try that and see.

---

### Post by forceofgravity on 2024-07-19
I'm not planning to install any other systems, just ubuntu and windows. So there are reasonable changes to success with 100 MB ESP.

Now when running live ubuntu from usb, I got constantly errors "System program problem detected" from package subiquity 171. Is that warning signal and I shouldn't try installation?

edit. Actually installation stops to the Disk setup window which just ask "How do you want to install Ubuntu?" without any options (on white background). Is this hint to wait until 24.04.1 or is there some other solution? The platform is Thinkpad T460.

---

### Post by tea for one on 2024-07-19
> **forceofgravity said:**
> edit. Actually installation stops to the Disk setup window which just ask "How do you want to install Ubuntu?" without any options (on white background). Is this hint to wait until 24.04.1 or is there some other solution? The platform is Thinkpad T460.
Do you not see two options:-
(a) Erase disk and install Ubuntu
(b) Manual installation
[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)

---

### Post by forceofgravity on 2024-07-19
> **tea for one said:**
> Do you not see two options:-
(a) Erase disk and install Ubuntu
(b) Manual installation
[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)

No, just white below the question. That might be related to the error "System program problem detected" (subiquity 171).

---

### Post by forceofgravity on 2024-07-19
> **forceofgravity said:**
> I'm not planning to install any other systems, just ubuntu and windows. So there are reasonable changes to success with 100 MB ESP.

Now when running live ubuntu from usb, I got constantly errors "System program problem detected" from package subiquity 171. Is that warning signal and I shouldn't try installation?

edit. Actually installation stops to the Disk setup window which just ask "How do you want to install Ubuntu?" without any options (on white background). Is this hint to wait until 24.04.1 or is there some other solution? The platform is Thinkpad T460.

Problem solved! The issue with Ubuntu installer was due to wrongly generated usb-stick - my bad. First I did it with Disk tool and second time with Startup Disk Creator.

ESP usage is 32 MB of 100 MB, so the size is enough for dual boot system.

---

### Post by grahammechanical on 2024-07-19
I have three installs of Ubuntu - 20.04, 24.04 & 24.10 (development version). The EFI System partition is 537 MB and is only 1.4% full. I guess if I was dual booting with Windows its boot files would take up some space. 

Regards

---

### Post by coffee-enthusiast on 2024-08-23
> **forceofgravity said:**
> Problem solved! The issue with Ubuntu installer was due to wrongly generated usb-stick - my bad. First I did it with Disk tool and second time with Startup Disk Creator.

ESP usage is 32 MB of 100 MB, so the size is enough for dual boot system.

@forceofgravity I'm in the exact same position as you.
To make sure I got this right, in the new Ubuntu installer, you set the mount point for /dev/sda2 to /boot/efi and for /dev/sda6 to / is that right?
I've attached a picture of my partition table. So for me
/dev/nvme0n1p2 would have the mount point set to /boot/efi and /dev/nvme0n1p7 set to / correct?

---

### Post by oldfred on 2024-08-23
@coffee-enthusiast
If you want help better to start your own thread.
Your partitions show exactly which partition is ESP, / (root) & swap.
Little key icons show mounted partitions from your running system from your install, and you cannot edit mounted partitions. You can use gparted from live installer.

---

### Post by coffee-enthusiast on 2024-08-23
@oldfred, I know which partition is the ESP, the screenshot was taken when booted into the Ubuntu installation that I'm trying to replace. I will be editing those partitions from the installer, but I just wanted to confirm whether I should manually set the mount point to the EFI partition as /boot/efi. I didn't make a separate thread because I expect people would just link me back to this thread. I haven't used the new installer yet and I'm unfamiliar with it so please bear with me.

---

### Post by oldfred on 2024-08-24
@coffee-enthusiast
If installing to the same / (root), you have to choose the existing / partition.
You show p7 as swap.

I have dual boot Ubuntu installs & install LTS version to one partition and 2 years later install next LTS to other / partition. All data in data partition that is mounted in /home. I may also have other / partitions for test installs. So I only use Something Else/manual as any autoinstall option may  not chose what I want. I now use Kubuntu which has changed to the Calmares installer which I like.

---

