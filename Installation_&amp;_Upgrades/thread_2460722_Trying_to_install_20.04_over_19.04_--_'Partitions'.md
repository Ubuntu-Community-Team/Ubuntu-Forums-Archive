---
title: "Trying to install 20.04 over 19.04 -- 'Partitions' problems"
date: 2021-04-16
forum: Installation &amp; Upgrades
---

### Post by alanralph on 2021-04-16
Linux newbie here. 

I have a Lenovo 120S Ideapad that ran slow on Windows so I removed it and somehow managed to put Lubuntu 19.04 disco dingo on, and the laptop then worked great!  That was October 2019, and I used it for about 5 months, but I haven't used it in a year, so now I would like to upgrade it to 20.04 LTS and start using it again. I would like to completely erase everything on the HDD and do a fresh install of 20.04. I used Rufus to create a USB boot drive and the installation is giving me some problems that I have no idea how to get past....

I am following the installation tutorial at lubuntu.me. I am on Step 1.3. Within this step is 'Setting up partitions'. Here's where I am stumped.... the screenshot in the tutorial shows an option for 'Erase disk' (which is what I want to do!) but on my laptop, I am not given this option :(

tutorial:
[ATTACH=CONFIG]288323[/ATTACH]

my laptop:
[ATTACH=CONFIG]288324[/ATTACH]


In order to get the 'Next' button, I have to select 'Manual partitioning' but I don't know what to do next...

[ATTACH=CONFIG]288326[/ATTACH]

I have tried almost everything I can think of that is offered on this screen. Create. Edit. Delete. New Partition Table. It even shows 2 nearly identical 'Storage Devices' but there is only one HDD in the laptop??  Everything I do does not open up the 'Next' button so I end up pressing 'Revert All Changes' and I am basically forever stuck.

I searched through the forum and could not find any post that was similar to my issue here. I apologize if I missed any post or if this has already been solved elsewhere. 

Do I have to remove 19.04 first? Can I just format the HDD to start fresh? I actually tried that first, but I was unable to install 'wipe' for some reason, it got some errors. A lot of things seem to, which is why I want to get a fresh install!

Any help would be appreciated.  Thank you very much.

---

### Post by guiverc on 2021-04-16
If you don't have the *Erase Disk *option, it's because of a reason, such as mounted partition (ie. part of the disk is being used).

I'd check for a in-use *swap* partition for example, which is covered in the manual at [https://manual.lubuntu.me/lts/1/1.3/installation.html](https://manual.lubuntu.me/lts/1/1.3/installation.html)

> 
If you had a previous Linux install with swap you will need to unmount the swap. To do this run

  sudo swapoff -a

 
 which will unmount them and any swap partitions. This will not work  if you have data partition mounted open PCManFM-Qt and press the upward  pointed arrow on each partition in the Places sidebar to unmount all data partitions.



Looking at your partition details, if you wanted to use the Manual Partitioning option, you'll need two

/dev/mmcblk0p1 is /boot/EFI   (as it's a 300MB FAT32 partition used as ESP partition)
/dev/mmcblk0p2 is /  (ext4 format is default)

You can select those (as were used by your 19.04/*disco* installation) and select FORMAT or not, and the install should complete successfully.

FYI:  I don't see any swap partition, and 19.04/*disco* did not setup swap file by default, so I don't see a reason why your Erase Disk option didn't show on your `calamares` (*calamares is the installer used by Lubuntu; ie. your partitions setup*) screen

---

### Post by Dennis N on 2021-04-16
I think you could continue the manual partitioning - based on your last image, select the partition containing the existing Lubuntu (it's formatted ext4) - then click "Edit". I think that will allow you to specify this as the root partition for your new install, which is what you want to do. That may be all that's necessary on partitioning. Then click Next to finish the install.


You don't need to remove the Lubuntu 19.04 first. The installer will overwrite it.

---

### Post by guiverc on 2021-04-16
Sorry I didn't see or missed  the "Do I have to remove 19.04 first?" bit.

If you used & liked your old 19.04 system, and had added packages, made changes that you liked, I'd for sure use manual partitioning and install into the same partitions without format.

If you don't format the partitions, the following occurs

- system packages are noted (particularly those you installed yourself)
- system directories are erased
- new system is installed 
- packages noted earlier you had installed are attempted to be installed (if available in the new release)
- no user file is touched (unless you formatted)
- you are asked to reboot

I refer to this as *upgrade via re-install* and is a very quick method of upgrade, plus allows you to skip releases (or re-install the same or older release actually; I use it a lot).

Note: you may get a warning that some packages could not be restored... This happens (particularly with 3rd party packages you've added, but can include some Ubuntu packages that are no longer available; eg. python2 & Qt4 were removed during 2019 & won't exist in 20.04, so any packages that relied on those that weren't upgraded to python3 or Qt5 will cause this warning message). It doesn't impact the success of the install.

Of course you should backup any important files, but as Dennis N suggested - this would be what I'd do as well.  And no you don't need to remove the prior installation (be it Lubuntu or anything else).

I agree with Dennis N except I'd also use the /boot/efi partition too (see my prior post).  If your box is BIOS boot-up you won't need it, but if using uEFI you risk fail-to-boot without it (but using it on an older BIOS box doesn't have consequences).

---

### Post by alanralph on 2021-04-16
Thanks for the replies!

Guiverc: One of the first things I tried was to select ‘Format’ for those two 19.04 partitions, but after pressing ‘OK’, nothing happened.  I re-selected it and again it was like nothing happened, as the selector was back on ‘Keep’ and off of ‘Format’.

Dennis N: (see photo) I then went into the manual partitioning, chose the ext4, clicked ‘Edit’, but there is no option to specify ‘root’. Only ‘boot’ and ‘bios-grub’ are there.  I even tried to change the ‘Content’ to ‘Format’ but when I press ‘OK’, nothing happens. The ‘Next’ button still does not show up! 

[ATTACH=CONFIG]288327[/ATTACH]

Guiverc:  Finally, I did read that part in the tutorial about “swapoff”.  I tried it 2 different times, once within the installer (I was able to access q-terminal) and that didn’t do anything, so I restarted the laptop back to the 19.04 and wrote “sudo swapoff -a" in q-terminal and restarted into the USB boot, but that didn’t do anything either. So I gave up on that because I didn’t know what else to do or how else to do it.

After the 19.04 install in 2019, I tried to install other programs, packages, and things, and then it seemed like I would always get errors when I do “sudo apt update” so I just want to remove all of it, I don’t want any of the current installation.

I did wonder if this ‘swapoff’ was the reason for not being able to move forward though...

---

### Post by guiverc on 2021-04-16
There is a 'drop down' menu which selects the **Mount Point**.

You need to select the "/" there :) 

(*and/or for your other partition selecting /boot/efi/*)

The "Keep" option = *no format* and is what I was talking about.

I don't believe swap is your issue, but if you disable swap via command, then reboot, you'll need to disable it again (*it takes effect immediately and rebooting it will cause it to return to the default setting*).

*Your 19.04 install should have worked as expected until it reached EOL (then errors on packages are to be expected as repositories get moved from archive.ubuntu.com to old-releases.ubuntu.com as users are expected to upgrade before the EOL to the next release, ie. 19.10, which would have been offered (but note: there is a dismiss & not bug me again option, which works but that also means users tend to forget to upgrade until after it's too late). 19.04 meant 2019-April release; it had 9 months of support, but the upgrade window closed when the next release (19.10 or 2019-October) reached EOL 9 months after it's release... knowing the release lets you do these date calculations).*

---

### Post by alanralph on 2021-04-17
Thanks again for the response Guiverc!  

I want to re-learn what I learned in 2019 with 19.04, it's just important to me to flash the system and start over fresh.

The 'Next' button has appeared!

However, I have one final (hopefully this will be the last one) question....

After:
1. I edited mmcblk0p2 (ext4), changed to 'Format', 'mount point' to '/' 
2. I edited mmcblk0p1 (FAT32), change to 'Format', mount point to '/boot/efi' 

When I pressed 'Next', this prompt happened -- "EFI system partition flag not set":
[ATTACH=CONFIG]288328[/ATTACH]

I went 'Back'. mmcblk0p1 (FAT32) does not have an 'esp' flag option:
[ATTACH=CONFIG]288330[/ATTACH]

So I deleted mmcblk0p1 and pressed 'Create' to create a new FAT32 file partition in that 'Free Space', but in the full list of 'Flags', there is still no option for 'esp'!
[ATTACH=CONFIG]288329[/ATTACH]


The prompt says I can continue "without the esp flag but the system may fail to start." 

Do I have any other choice here?  Should I continue with mmcblk0p1 & mmcblk0p2 (with the correct 'mount points') and ignore the 'esp' flag prompt?

I feel like I am sooo close.....!

Thank you.

---

### Post by Dennis N on 2021-04-17
> So I deleted mmcblk0p1 and pressed 'Create' to create a new FAT32 file partition in that 'Free Space', but in the full list of 'Flags', there is still no option for 'esp'!
_Option 1:_ Try setting 'boot' flag on the fat32 partition and continue the install.  
Setting the 'boot' flag may automatically set 'esp' flag as it does with Ubuntu's installer (Ubiquity). But if not, I would continue install anyway with boot flag set and see how it works.

_Option 2:_ Back out of the install and use gparted on the live media to set the boot flag on the fat32 partition. It will automatically set an 'esp' flag as well. Then restart the installation.

---

### Post by oldfred on 2021-04-17
Rufus creates a UEFI only UEFI/gpt or a BIOS only CSM/MBR installer.
Did you create the UEFI version?

Other install tools create the installer that can be booted in either boot mode UEFI or BIOS/CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Then how you select to boot installer UEFI or BIOS, is then how it installs. Rufus installer will only have one option.
But if you have system set for UEFI boot, but install in BIOS, you later when rebooting will have boot issues as install does not match the mode UEFI is set to boot.

Just always select UEFI and use gpt partitioning.

---

### Post by alanralph on 2021-04-17
[COLOR=#000000]oldfred: I used Rufus with the GPT/UEFI option. My system is set for UEFI.

[/COLOR]Dennis N: I did your 'Option 1': I set the [COLOR=#000000]'boot' flag on the fat32 partition, ignored the 'esp' prompt, and continued the install.

[/COLOR][ATTACH=CONFIG]288336[/ATTACH]

This is the summary that I installed... and so far.. so good!

Thanks everyone!

---

### Post by guiverc on 2021-04-17
I'll provide some detail from my last comment

With regards the ESP (EFI system partition) flag not being set, I'll provide a link to an answer which shows what I do - [https://askubuntu.com/questions/1273421/lubuntu-installer-giving-error-after-partition-creation-your-system-may-or-may/1276789#1276789](https://askubuntu.com/questions/1273421/lubuntu-installer-giving-error-after-partition-creation-your-system-may-or-may/1276789#1276789)

Note:  some boxes require that to be done, others do not (thus the **may fail to start** warning)

Yeah the ESP (EFI system partition) message isn't helpful for end-users given no check box is present to select that (*correct names are used which results in a mis-match between what is called ESP in one later standard; but as the concept of ESP didn't exist when the prior standard was written it's called something different by that standard being flag names on partition table dialog*).  I'm hoping my askubu link will suffice.

Hopefully you got it sorted by the help others provided...

FYI: if you follow the manual link (on askubu page); *stable* refers to the latest release which currently is *groovy* or 20.10, so replace the "stable" in the URL to say "lts" and you'll get the manual page for *focal* or 20.04 LTS

---

