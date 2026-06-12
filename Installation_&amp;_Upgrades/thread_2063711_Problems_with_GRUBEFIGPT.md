---
title: "Problems with GRUB/EFI/GPT"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by fluteflute on 2012-09-27
Apologies for asking for you help, but I don't think I will get much further with this on my own. I have what should be a simple dual boot system, but things are never as simple as they seem! Even before today I have always been a bit confused as to how booting works on my GPT/EFI system.

Going through everything I've done today would probably just be confusing, so I'll give you the current situation.

Turning on the laptop gives ```
error: file not found.
grub rescue> _
```

Running ```
set prefix=(hd0,gpt8)/boot/grub
insmod normal
normal
``` gives me a GRUB screen for partition 8 (a fresh install of precise). However once booted into Ubuntu on partition hda8 I don't seem to be able to run any grub-install commands to bypass the grub rescue prompt.

Ideally I would be booting from partition 7 (an Ubuntu precise upgraded today to quantal). I don't seem to be able to this at the moment, even from the grub screen of partition 8 - I just get a black screen. I guess it's possible something went wrong in the upgrade. However I have not been able to boot into fresh installs of quantal (that I've installed this afternoon, and now replaced by the fresh precise) using the method in the above paragraph.

From "proper" GRUB, then typing c for command line enables me to type "exit" which then starts Windows 7. [This was how things were before today, and how things are now when I have access to the precise grub]

Oh and I've also tried using Boot Repair. That tells me "GPT detected. Please create a BIOS-Boot partition". I've tried creating one, but I still get the message in Boot Repair. And [looking at the wiki]("https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29"), it suggests I don't need one, as my machine has an EFI partition.

My Boot Repair summary is at [http://paste.ubuntu.com/1231033/](http://paste.ubuntu.com/1231033/)

Just to summarise my partitions (as I see them):
[LIST]
[*]sda1: EFI partition, came with windows laptop
[*]sda2: recovery partition, came with laptop
[*]sda3: another EFI partition... I think Windows uses it
[*]sda4: not quite sure what this is (possibly a bios boot partition I tried creating earlier, deleting something similar first, hence the low number)
[*]sda5: Windows 7 itself
[*]sda6: An ext4 partition I store files on
[*]sda7: Precise, upgrading to quantal development (upgrading today started my problems, or at least restarted my problems)
[*]sda8: An ext4 partition I use to backup the files on sda6
[*]sda9: A fresh precise install - the only thing I can actually boot to at present
[*]sda10: Not sure, same as sda4?
[/LIST]

Sorry if I've been confusing (and for the long post), please ask me to clarify if you need to. Many thanks in advance for the assistance.

---

### Post by YannBuntu on 2012-09-27
> **fluteflute said:**
> My Boot Repair summary is at [http://paste.ubuntu.com/1231033/](http://paste.ubuntu.com/1231033/)

sda1 has the 'hidden' flag, so it must be a Windows recovery EFI partition.
sda3 should be the EFI partition to use.

1) via Gparted, place the 'boot' flag on sda3
2) run Boot-Repair's Recommended repair and tell me the new URL that will appear
3) reboot and tell what you observe

---

### Post by fluteflute on 2012-09-27
> **YannBuntu said:**
> sda1 has the 'hidden' flag, so it must be a Windows recovery EFI partition.
sda3 should be the EFI partition to use.

1) via Gparted, place the 'boot' flag on sda3
2) run Boot-Repair's Recommended repair and tell me the new URL that will appear
3) reboot and tell what you observeAh the hidden explanation makes sense. However it seems Ubuntu is using sda1 for its EFI (at least my working precise install is).

1) Done. I also removed the boot flag from sda1.
2) [http://paste.ubuntu.com/1231138/](http://paste.ubuntu.com/1231138/)

I also was told the following but I didn't act on it.
```
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda3/EFI/ubuntu/grubx64.efi file!

The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

```

3) A working precise GRUB menu! Thanks! 

I do get three Windows entries, none of which work ("error: file not found. Press any key to continue..._") And then two Windows Recovery Environment entries (loader), neither of which work ("error: unkown command `drivemap'. error: invalid EFI file path. Press any key to continue..._". There's one of sda2 and one for sda5.

But the exciting is that the first Quantal boot entry is working! Thank you!

---

### Post by YannBuntu on 2012-09-27
> **fluteflute said:**
> I also was told the following but I didn't act on it.

You did well. You see GRUB, so you don't need to act on it.

> **fluteflute said:**
> I do get three Windows entries, none of which work ("error: file not found. Press any key to continue..._") And then two Windows Recovery Environment entries (loader), neither of which work ("error: unkown command `drivemap'. error: invalid EFI file path. Press any key to continue..._". There's one of sda2 and one for sda5.

The 3 first ones are custom entries created by Boot-Repair. I don't know why they don't work for you.
The 2 last ones are entries created by GRUB. (they are buggy, so you can mark yourself as "affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383) )

Please run Boot-Repair --> Advanced options --> tick "Restore EFI backups" --> untick "Reinstall GRUB" --> Apply --> tell me the new URL.
Then you should be able to boot Windows from your BIOS.

---

### Post by fluteflute on 2012-09-28
> **YannBuntu said:**
> The 3 first ones are custom entries created by Boot-Repair. I don't know why they don't work for you.
The 2 last ones are entries created by GRUB. (they are buggy, so you can mark yourself as "affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383) )Marked myself as affected.

Please run Boot-Repair --> Advanced options --> tick "Restore EFI backups" > **YannBuntu said:**
> --> untick "Reinstall GRUB" --> Apply --> tell me the new URL.
Then you should be able to boot Windows from your BIOS.[http://paste.ubuntu.com/1234677/](http://paste.ubuntu.com/1234677/)

As far as I can see as a user, there has been no change in what happens on boot.

---

### Post by YannBuntu on 2012-09-28
Your "Restore EFI" option was not ticked.

Please run Boot-Repair --> Advanced options --> untick "Reinstall GRUB" --> tick "Restore EFI backups" --> Apply --> tell me the new URL.
Then you should be able to boot Windows from your BIOS.

---

### Post by fluteflute on 2012-09-28
> **YannBuntu said:**
> Your "Restore EFI" option was not ticked.

Please run Boot-Repair --> Advanced options --> untick "Reinstall GRUB" --> tick "Restore EFI backups" --> Apply --> tell me the new URL.
Then you should be able to boot Windows from your BIOS.[http://paste.ubuntu.com/1247447/](http://paste.ubuntu.com/1247447/)

I am now back to my original situation, with ```
error: file not found.
grub rescue>_
```

I guess this is related to the fact that my sda7 partition mounts sda1 to /boot/efi?

Would deleting the non microsoft folders from sda1/efi/EFI/ be a bad idea?

---

### Post by YannBuntu on 2012-09-28
> **fluteflute said:**
> I am now back to my original situation, with ```
error: file not found.
grub rescue>_
```

How do you get this error exactly? which entry is selected in the BIOS boot order?

Which entries are available in your BIO boot order?


I guess this is related to the fact that my sda7 partition mounts sda1 to /boot/efi?  --> no

Would deleting the non microsoft folders from sda1/efi/EFI/ be a bad idea?  ---> yes

---

### Post by fluteflute on 2012-09-28
> **YannBuntu said:**
> How do you get this error exactly? which entry is selected in the BIOS boot order?

Which entries are available in your BIO boot order?


I guess this is related to the fact that my sda7 partition mounts sda1 to /boot/efi?  --> no

Would deleting the non microsoft folders from sda1/efi/EFI/ be a bad idea?  ---> yesI get the error simply by turning on the laptop, I don't touch anything.

1st boot priority: Internal Optical Drive
2nd boot priorty: External Device
3rd boot priority: Internal Hard Disc Drive

However, I just tried swapping the Internal Optical and Internal Hard Disc options, and I still get the same error.

---

### Post by YannBuntu on 2012-09-28
Please run Boot-Repair --> Advanced options --> tick "Reinstall GRUB" --> untick "Backup and rename EFI files" --> Apply --> tell me the new URL.
Reboot and tell me what you observe.

---

### Post by fluteflute on 2012-09-28
> **YannBuntu said:**
> Please run Boot-Repair --> Advanced options --> tick "Reinstall GRUB" --> untick "Backup and rename EFI files" --> Apply --> tell me the new URL.
Reboot and tell me what you observe.[http://paste.ubuntu.com/1248033](http://paste.ubuntu.com/1248033)

Everything is mostly the same. (run the commands below to get grub)
```

error: file not found.
grub rescue> _

set prefix=(hd0,gpt8)/boot/grub
insmod normal
normal
```

The interesting thing is that once in GRUB, the second "Windows UEFI loader" boots the repair partition. (As before, none of the other Windows Grub entries work)

---

### Post by oldfred on 2012-09-28
It seems like you are still booting in BIOS mode not UEFI mode.

In UEFI/BIOS should be a setting on which way to boot. Booting with BIOS loads the MBR which is not correct. But the UEFI looks like it should boot without any issue.

---

### Post by fluteflute on 2012-09-28
> **oldfred said:**
> It seems like you are still booting in BIOS mode not UEFI mode.

In UEFI/BIOS should be a setting on which way to boot. Booting with BIOS loads the MBR which is not correct. But the UEFI looks like it should boot without any issue.Changing to a non-UEFI boot just gives the message "Operating System Not Found" on startup.

I'm now trying running Boot Repair from my quantal install (as I am using this as my main OS).

Just so you know, I just got the following (slightly weird) instructions:
```
sudo apt-get install -fy
sudo dpkg --configure -a
sudo apt-get purge -y --force-yes grub*-common
```

Ooh, it seems Quantal may have not installed in EFI mode (possible the reason for the weirdness?)

> greg@greg-SVE14A1C5E:~$ sudo apt-get purge -y --force-yes grub*-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for regex 'grub*-common'
The following packages will be REMOVED
  grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*
0 upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
After this operation, 9,272 kB disk space will be freed.
(Reading database ... 204556 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing **grub-pc** ...
Purging configuration files for grub-pc ...
Removing grub2-common ...
Removing grub-pc-bin ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
greg@greg-SVE14A1C5E:~$ sudo apt-get install -y --force-yes grub-efi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed
  grub-common grub-efi grub-efi-amd64 grub-efi-amd64-bin grub2-common
0 upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/1,987 kB of archives.
After this operation, 8,571 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package grub-common.
(Reading database ... 204206 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_2.00-7ubuntu1_amd64.deb) ...
Selecting previously unselected package grub2-common.
Unpacking grub2-common (from .../grub2-common_2.00-7ubuntu1_amd64.deb) ...
Selecting previously unselected package grub-efi-amd64-bin.
Unpacking grub-efi-amd64-bin (from .../grub-efi-amd64-bin_2.00-7ubuntu1_amd64.deb) ...
Selecting previously unselected package grub-efi-amd64.
Unpacking grub-efi-amd64 (from .../grub-efi-amd64_2.00-7ubuntu1_amd64.deb) ...
Selecting previously unselected package grub-efi.
Unpacking grub-efi (from .../grub-efi_2.00-7ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Setting up grub-common (2.00-7ubuntu1) ...
Processing triggers for ureadahead ...
Setting up grub2-common (2.00-7ubuntu1) ...
Setting up grub-efi-amd64-bin (2.00-7ubuntu1) ...
Setting up grub-efi-amd64 (2.00-7ubuntu1) ...

Creating config file /etc/default/grub with new version
BootCurrent: 0006
Timeout: 2 seconds
BootOrder: 0005,0006,0007,0000,0001,0002
Boot0000* Windows Boot Manager
Boot0001* CD/DVD Drive 
Boot0002* Hard Drive 
Boot0005* Sony Original
Boot0006* Windows Boot Manager
Boot0007* Windows Boot Manager
BootCurrent: 0006
Timeout: 2 seconds
BootOrder: 0003,0005,0006,0007,0000,0001,0002
Boot0000* Windows Boot Manager
Boot0001* CD/DVD Drive 
Boot0002* Hard Drive 
Boot0005* Sony Original
Boot0006* Windows Boot Manager
Boot0007* Windows Boot Manager
Boot0003* ubuntu
Installation finished. No error reported.
Setting up grub-efi (2.00-7ubuntu1) ...
greg@greg-SVE14A1C5E:~$ 


I may as well also post [http://paste.ubuntu.com/1248333/](http://paste.ubuntu.com/1248333/) here. Now to reboot and see what happens!

---

### Post by fluteflute on 2012-09-29
> **fluteflute said:**
> I'm now trying running Boot Repair from my quantal install (as I am using this as my main OS). Now to reboot and see what happens!So the news is that all works as expected, with the exception of Windows from GRUB (have to do the c for command, then type exit thing). But as that was a problem before, I'm going to mark this thread as solved.

Thank you for the help, and for making Boot Repair!

---

### Post by YannBuntu on 2012-09-29
I'm glad you found a (semi)solution.

Apparently, you had the problem when using the grub-efi of Precise, but it works now because you are using the grub-efi of Quantal.
It would be nice if you could confirm this point, for example by:
1) using Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.04 --> Apply --> Reboot. --> you should get the "GRUB rescue" error.
2) using Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.10 --> Apply --> Reboot. --> you should recover the correct boot, like you have now.


I also detected a bug in the Ubuntu installer: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058609](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058609) (you can mark yourself "Affected")

---

### Post by fluteflute on 2012-09-29
> **YannBuntu said:**
> I'm glad you found a (semi)solution.

Apparently, you had the problem when using the grub-efi of Precise, but it works now because you are using the grub-efi of Quantal.
It would be nice if you could confirm this point, for example by:
1) using Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.04 --> Apply --> Reboot. --> you should get the "GRUB rescue" error.
2) using Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.10 --> Apply --> Reboot. --> you should recover the correct boot, like you have now.Hmm I tried doing this (from a 12.04.1 Live USB).

However the two didn't seem any different - both presented me with GRUB for 12.10.
1) Selecting 12.04: [http://paste.ubuntu.com/1249734](http://paste.ubuntu.com/1249734)
2) Selection 12.10: [http://paste.ubuntu.com/1249762](http://paste.ubuntu.com/1249762)

I got the message "Please do not forget to make your BIOS boot on sda3/EFI/ubuntu/grubx64.efi file!" again, is that an explanation for what I've just seen?

Is is it worth trying the same procedure from a 12.10 Live USB?

> **YannBuntu said:**
> I also detected a bug in the Ubuntu installer: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058609](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058609) (you can mark yourself "Affected")Done :)

---

### Post by YannBuntu on 2012-09-30
Interesting.
I think that Boot-Repair fails installing the grub-efi of your Precise, but succeeds in installing the grub-efi of Quantal.

I think that the result would be the same from a 12.10 Live USB, no need to test it.

What you could try is:
1) backup on a USB key the 2 following files which are located in your sda1 partition: /efi/boot/bootx64.efi and /efi/ubuntu/grubx64.efi
2) remove those 2 files from your sda1 partition. Reboot and check that your PC can't boot any more.
3) from a liveUSB, use Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.04 --> Apply --> Reboot. --> tell me what you observe (i guess the boot will fail). Also tell me if a new sda1/efi/boot/bootx64.efi and sda1/efi/ubuntu/grubx64.efi have been regenerated or not?
4) from a liveUSB, use Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.10 --> Apply --> Reboot. --> tell me what you observe (i guess the boot will succeed).

---

### Post by fluteflute on 2012-10-14
> **YannBuntu said:**
> Interesting.
I think that Boot-Repair fails installing the grub-efi of your Precise, but succeeds in installing the grub-efi of Quantal.

I think that the result would be the same from a 12.10 Live USB, no need to test it.

What you could try is:
1) backup on a USB key the 2 following files which are located in your sda1 partition: /efi/boot/bootx64.efi and /efi/ubuntu/grubx64.efi
2) remove those 2 files from your sda1 partition. Reboot and check that your PC can't boot any more.
3) from a liveUSB, use Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.04 --> Apply --> Reboot. --> tell me what you observe (i guess the boot will fail). Also tell me if a new sda1/efi/boot/bootx64.efi and sda1/efi/ubuntu/grubx64.efi have been regenerated or not?
4) from a liveUSB, use Boot-Repair --> Advanced options --> GRUB location --> OS to boot by default: 12.10 --> Apply --> Reboot. --> tell me what you observe (i guess the boot will succeed).Sorry this has taken me a while to look at, things are a bit busy at the moment, and I didn't want to risk playing with my bootloader too much!

I deleted all the files in /boot/efi/EFI/boot/ and those in /boot/efi/EFI/ubuntu/ leaving only /boot/efi/EFI/Microsoft/ But after rebooting, everything continued to work as before (see [http://paste.ubuntu.com/1279500/](http://paste.ubuntu.com/1279500/)). It turns out that /boot/efi is mounted to sda3, but you had wanted me to delete files from sda1.

What should I do now?

---

### Post by oldfred on 2012-10-14
You can only have one efi partition. With parted it shows as a boot flag but is really a gpt ef00 code.

But you have two partitions with boot files. Normally sda1 or the first partition is the efi partition as that is the standard. But we have seen one or two cases where it works as a second or even third partition as long as it is not too far into the drive, or must still be near front of drive.

If you can boot from sda3 then you can delete all the files in sda1 or you can move boot flag to sda1 and see if that boots and delete the files in sda3. System will only actually boot from the efi partition or boot flag or ef00.

This was from the author of gdisk which is the fdisk for gpt partitions. The must be first is the standard, but it may work from others we have found out.
> 
The efi system partiton should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.

---

### Post by YannBuntu on 2012-10-15
You have not done what i suggested, but it is interesting anyway.
I think you are booting on /EFI/Microsoft/Boot/bootmgfw.efi (which is indeed a grub.efi file, the real Windows file is /EFI/Microsoft/Boot/bootmgfw.efi.bkp , which was generated by the "backup and rename" option).
To check it, you can rename (not delete) the /efi folder in sda1 into /efi_old and check that your PC still boots. (if not, revert to /efi_old to /efi)

Don't do this test if you don't want to take any risk. Just enjoy Ubuntu now :)

---

