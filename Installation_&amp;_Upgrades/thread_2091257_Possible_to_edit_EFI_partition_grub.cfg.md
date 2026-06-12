---
title: "Possible to edit EFI partition grub.cfg?"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by teastman on 2012-12-04
Thought I'd better start a new thread for this. Searched the forums for this but didn't find it. With these new UEFI GPT disks do we have access to the EFI partition to edit the boot menus?

We used to (pre-GPT and UEFI days) be able to edit a grub file and recompile grub after the edit and boom off we'd go. Can we still do that on these new EFI partitions or do we have to boot to a Ubuntu 12.10 Remix 64bit ISO and run BootRepair every time we want to change a boot default or timeout?

---

### Post by gordintoronto on 2012-12-04
I think your answers are here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

After making changes, the secret sauce is: 
sudo update-grub

---

### Post by oldfred on 2012-12-04
Quick answer is Yes.

The efi partition and boot loaders in the efi partition are really more the replacement of the MBR. And you now can have more than one boot loader in the efi where with MBR you only could have one. 

But you can still edit 40_custom and add chain load entries or other custom entries to grub or edit /etc/grub.

Some UEFI's have an efi shell or Intel offers a generic efi shell. That really is more for checking on efi not grub nor Windows. 
       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by teastman on 2012-12-05
> **oldfred said:**
> Quick answer is Yes.

The efi partition and boot loaders in the efi partition are really more the replacement of the MBR. And you now can have more than one boot loader in the efi where with MBR you only could have one. 

But you can still edit 40_custom and add chain load entries or other custom entries to grub or edit /etc/grub.

Some UEFI's have an efi shell or Intel offers a generic efi shell. That really is more for checking on efi not grub nor Windows. 
       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Okay - thanks for the response.
At the risk of sounding obtuse I have a couple additional questions. My System Setup (<F2> key to enter System Settings at bootup) is set to boot to Ubuntu loader first and Windows loader second. So does this point the boot process to /etc/grub still? Or is this "grub" file now in a sub directory on the EFI partition? (like /EFI/etc/grub )

I'm sure the /etc/grub structure is there on the disk - I'm still uncertain though where the bootup process is pointing when Ubuntu Loader is first in the System Settings boot sequence. 
/EFI/etc/grub? or
/etc/grub?

---

### Post by oldfred on 2012-12-05
Grub has not changed what is not mentioned as part of grub below is in BIOS you have the MBR and core.img which you never really see nor edit. With UEFI you do have visibility of efi files in the efi partition. If you run Bootinfoscript or BootInfo from boot repair you see some of the details of MBR or efi files.

 GRUB 2 - GRand Unified Bootloader has three main parts 

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

I have multiple drives, so I have multiple MBRs. So from my BIOS or one time boot key f12 I get an option to boot from any drive (really MBR).

With efi, it is like my multiple drives as you have the efi boot loaders for every system installed. You still can have an efi partition on every drive. The boot loader code is just part of the boot process. From the UEFI menu you are selecting options from the efi folder on your drive. 

Someone posted a BootInfo with many systems. He had lots of efi files and each vendor had folders in it. He also wanted separate folders for kubuntu from ubuntu which is not the case, so he filed a bug.

---

### Post by trogdor1138 on 2012-12-06
> **teastman said:**
> I'm sure the /etc/grub structure is there on the disk - I'm still uncertain though where the bootup process is pointing when Ubuntu Loader is first in the System Settings boot sequence. 
/EFI/etc/grub? or
/etc/grub?

I'm actually booting Kubuntu 12.10 in EFI mode on my Mac, so I can help a little. There are two main ways that GRUB 2 can be configured for EFI.

The first is to put GRUB, its configuration files, and all of its required modules into the boot folder. This is located at /EFI/ubuntu from the root of the partition. On a GPT disk this will often be the first partition, the EFI system partition, but it doesn't have to be. Your EFI boot manager should allow you to select any EFI application from any location, but it probably only automatically checks the /EFI/ folders.

The second way is to simply put the actual GRUB 2 EFI binary at the above location, with all modules and configuration files located on your root partition. This is how my installation set itself up, and I believe it is the default action for Ubuntu to take.

Ubuntu should also auto-mount GRUB's EFI partition at /boot/efi. Inside this directory you should find /EFI/Ubuntu/grub.efi as explained above.

The handy thing about the second way is that you can continue to use 'update-grub' as normal without worrying about keeping files in sync. I'm not sure if this holds true for the former.

So basically:

- You turn on your PC
- The EFI loads, checks for EFI applications, and checks its boot configuration
- Your EFI points to /EFI/Ubuntu/grub.efi on a partition and GRUB loads
- GRUB reads its configuration files, either in the same folder or at /boot/grub on your root partition depending on your setup

As for configuration, oldfred is exactly right. Continue to edit /etc/defaults/grub and /etc/grub.d as you would before, then run 'update-grub' to generate grub.cfg as normal.

On my EFI system, that's all it takes. At most you would need to manually copy your new grub.cfg to the GRUB EFI folder.

---

### Post by oldfred on 2012-12-06
@trogdor1138
I typically avoid Mac issues, as I do not have one nor know much. But it was my understanding that since they used a combination of UEFI 1 & 2 that the Windows & Ubuntu using UEFI 2 did not work in UEFI mode on a Mac?

Question is also related to MBR hybrid vs. gpt partitioning. I prefer gpt now even with my BIOS system and thought Macs used the hybrid MBR/gpt to accomodate Windows BIOS based booting? Windows only booted from gpt with UEFI and if UEFI did not work then you had to use BIOS and MBR with Windows on the Mac.

---

### Post by YannBuntu on 2012-12-07
**@trogdor1138:** wow! you're the first one i see using grub-efi on Mac! as i am not sure if teastman is using Mac, please could we talk about your experience on this other thread? [http://ubuntuforums.org/showthread.php?p=12392290#post12392290](http://ubuntuforums.org/showthread.php?p=12392290#post12392290)

---

### Post by trogdor1138 on 2012-12-07
> **oldfred said:**
> @trogdor1138
I typically avoid Mac issues, as I do not have one nor know much. But it was my understanding that since they used a combination of UEFI 1 & 2 that the Windows & Ubuntu using UEFI 2 did not work in UEFI mode on a Mac?

Question is also related to MBR hybrid vs. gpt partitioning. I prefer gpt now even with my BIOS system and thought Macs used the hybrid MBR/gpt to accomodate Windows BIOS based booting? Windows only booted from gpt with UEFI and if UEFI did not work then you had to use BIOS and MBR with Windows on the Mac.

Well, yes and no. Windows won't boot on a Mac in EFI mode, at least versions prior to Windows 8. I actually was running Windows 8 under EFI on my MacBook Pro for a time, but Apple's drivers don't work very well yet, so I went back to BIOS emulation. You're completely correct though about Apple's EFI being a mix of EFI 1.1 and 2.0, but not completely implementing either.

In order for Windows to boot in EFI, it requires:

- A GPT partition scheme
- 64-bit flavor of Windows
- Version of Windows newer than and including Vista SP2

However, Vista and 7 appear to rely on a video card call not supported by Apple's (U)EFI implementation. Windows 8 can work around this, and the others can be made to with hacks, but in my opinion Windows in EFI on a Mac is not quite there yet.

Ubuntu, on the other hand, runs just fine under Apple's EFI. This may not have been the case with older versions of Ubuntu, but the 12.x versions work very well. I was surprised by how easy it was to install on my Mac.

The only caveat is that Apple uses their own device, the so-called g-mux, to switch between the Intel integrated GPU and the discrete GPU on newer MacBooks. Generally, this requires a little configuration to get up and running. Using 'outb' one can disable the Radeon GPU to boot. Then it's just a matter of feeding the i915 driver built into kernel 3.5 and newer the right parameters.

This makes it easiest to install Ubuntu using 12.10, since it includes kernel 3.5 out of the box. Previous versions can be made to work, but they're a little more involved. The other thing to remember too is that Apple is constantly changing their EFI and internal hardware, since they don't have to adhere to any external standards, so each Mac is different and there are no universal answers.

As for the hybrid MBR, you are correct there also. I already posted a summary of this in another thread you've responded to, but so that it's here too:

- OS X boots in EFI from a GPT disk (can use MBR with some work-arounds). The Boot Camp Assistant writes the GPT spec's protective MBR with a "real" MBR usable by Windows

- Linux generally boots in BIOS mode from the GPT disk. It can boot just fine from a GPT disk in BIOS, but the hybrid MBR confuses it. Linux installers will often overwrite the hybrid MBR with a single, protective EFI system partition. Linux can be booted in EFI on at least some Macs

- Windows boots from a MBR disk in BIOS and a GPT disk in EFI, as explained above. Although Windows understands GPT disks since XP, Windows on a Mac pretends it's not a GPT disk and instead works only with the hybrid MBR created for it

It's VERY important to note that neither Windows nor OS X synchronize the hybrid MBR with the GPT partition tables when partitioning changes are made. This can lead to big problems if partitions are moved or resized, so the Boot Camp Assistant and OS X's Disk Utility only allow removal of Windows, not resizing or changing of number of partitions if a Windows install is found.

To get the GPT and MBR in sync, one needs to either use an EFI manager that has this ability, such as rEFIt, or gdisk, a GPT version of fdisk. I personally prefer the latter.


EDIT:

@YannBuntu Ah, your link works now. For some reason it didn't work from your PM. I'll respond in that other thread concerning all this

---

