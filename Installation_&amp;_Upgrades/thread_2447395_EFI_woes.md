---
title: "EFI woes"
date: 2020-07-17
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2020-07-17
Hi, I just hit this nagging problem and hope one of the efi gurus can point me in the right direction to resolve it.

I have a HP Stream notebook with Win10 and Lubuntu 20.04 dual booting without any issues. 

Yesterday, I installed another 64GB microsSD card and installed UbuntuStudio on the new microSD card. Interestingly, during the installation process, I was asked to provide a password when I clicked on the option of wanting to install third party applications. The installation process went off without any issues.

When I rebooted, uefi menu popped up and asked to provide the password to continue which I did. Then after a few seconds, I was presented with the grub prompt.

When I do a ls command at the grub prompt I get shown only the partitions on the emmc card on the Stream laptop. The newly inserted microSD card does not get listed. 

I then thought of manually booting into Lbuntu but still I get thrown back to the grub prompt.  I disabled secureboot and tried to boot again without success.

Any pointers to fix this will be greatly appreciated.

---

### Post by oldfred on 2020-07-17
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gdesilva on 2020-07-18
@oldfred, the boot info summary can be accessed here [https://paste.ubuntu.com/p/nNwZCdn7kC/](https://paste.ubuntu.com/p/nNwZCdn7kC/)

Many thanks for your time.


EDIT: just found out that the SD card reader reads only < 32 GB on this system and I am trying to use a 64GB SD card! 

[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/HP-Stream-11-boot-from-SD/td-p/4864557](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/HP-Stream-11-boot-from-SD/td-p/4864557)

Perhaps this is the issue? However, this does not explain why I cannot boot from Lubuntu on mmcblk0p5 manually. I did a set root, set prefix, insmod linux and then loaded Lubuntu vmlinuz and initrd.img.

---

### Post by oldfred on 2020-07-18
That could be the issue.

You only have one UEFI boot entry for Ubuntu which is normal but it is set to boot install on mmcblk1. 
Report did not show the grub.cfg but it says you have one.

I prefer to have an ESP on every drive, even though Ubuntu's Ubiquity installer only installs the first drive's ESP. To install grub to a second drive you have to do a work around, or use Boot-Repair to install to the second drive's ESP, but you do not have an ESP on second drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by CelticWarrior on 2020-07-18
> **oldfred said:**
> 

I prefer to have an ESP on every drive, even though Ubuntu's Ubiquity installer only installs the first drive's ESP. To install grub to a second drive you have to do a work around, or use Boot-Repair to install to the second drive's ESP, but you do not have an ESP on second drive.


This has two main advantages:

[LIST]
[*]Additional redundant bootloaders, useful if the main drive fails or have the ESP corrupted or locked.
[*]Some portability to the OS installed in the microSD card. It won't boot on everything but it will boot on something.
[/LIST]

The only disadvantage is the additional steps.

If intended for use in the same computer there's nothing wrong with having only one ESP, the one that is already there. Make sure Fast Startup (Windows) is disabled and that Secure Boot (UEFI "BIOS") and Fast Boot (UEFI) are disabled. Then use "something else" to select the main drive's ESP as UEFI (it won't allow formatting), and / (root) at the microSD car (currently this is all you need, no swap partition; /home can be its own partition but in a 64GB drive there won't be that many user files to regularly backup so /home really doesn't need to be separated).

All the above assumes the drive can rw a 64GB card. If not please use a 32GB microSD, still perfectly fine to install the OS and programs and still a few gigas for personal files.

---

### Post by gdesilva on 2020-07-19
@oldfred and @CelticWarrior,

Many thanks for your time and valued suggestions. I did a fair amount of testing and found that the issue is in fact related to the hardware on this system. 

As per RockDoctor's comment in [https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/HP-Stream-11-boot-from-SD/td-p/4864557](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/HP-Stream-11-boot-from-SD/td-p/4864557) I created a 512MB ext4 partition for /boot in the primary emmc card and then created partitions for / and /home on the secondary 64GB SD card.  Grub was installed on the ESP on the emmc card. This allows me to boot Ubuntu Studio installed on the SD card. 

So, it does appear that boot images have to reside on the emmc card in these laptops.

@CelticWarrior, like your idea of having ESPs on both devices which makes a lot of sense. Will give that a go shortly.

Thanks again.

---

### Post by oldfred on 2020-07-19
You would need /boot if a separate partition on external. But do not clone it as you cannot have duplicate UUIDs.

Also if seen as an external drive, direct boot of a full install on an external drive is from /EFI/Boot/bootx64.efi, not an Ubuntu entry. Same as booting the live installer. The that full version of grub needs /EFI/ubuntu/grub.cfg and some of the additional files in those ESP folders.

---

### Post by gdesilva on 2020-07-20
> **oldfred said:**
> You would need /boot if a separate partition on external. But do not clone it as you cannot have duplicate UUIDs.

As per your comment, it appears the stream laptops consider the SD card as an external drive?



> **oldfred said:**
> Also if seen as an external drive, direct boot of a full install on an external drive is from /EFI/Boot/bootx64.efi, not an Ubuntu entry. Same as booting the live installer. The that full version of grub needs /EFI/ubuntu/grub.cfg and some of the additional files in those ESP folders.

Can you please point me to a good site which provides details on how this could be set up? I am happy with the work around at the moment but would like to get my head around on uefi booting. Many thanks.

---

### Post by oldfred on 2020-07-20
It is just manually partitioning to include an ESP and gpt partitioning on external drive.
ESP can be anywhere on smaller drives, but better if near beginning of drive.

Then when installing to external follow work around as posted in #4. It is only Ubuntu's Ubiquity installer that does not let you choose where to install grub in UEFI mode. The choices are there but only work in BIOS mode.
Or reinstall grub as grub can be installed just about anywhere.
Often easier to reinstall grub using Boot-Repair.

See link in my signature for more UEFI info and links to details.

---

