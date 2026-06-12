---
title: "Missing Operating System/No Operating System Found"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by Chris_Groutage on 2014-04-08
I have just installed Ubuntu 13.10 64 Bit onto my computer. I have it installed into 4 partitions on my main hard drive (1TB).
/boot 500mb
/ 300GB
Swap 10GB
/home What is left

Ubuntu is my only operating system currently as I want to use it as my primary OS. I intend to install windows 7 home premium onto my 500GB HDD once I get this working. My problem is that the BIOS either tells me no operating system can be found or when I set the boot flags from gparted using a live CD that the operating system is missing. I am a noob to linux so have no idea what I may need to do to fix this.

Boot-repair told me that I required an EFI partition so I sorted that out and still had no success and got given this report

Boot-repair report: [http://paste.ubuntu.com/7220817/](http://paste.ubuntu.com/7220817/) 

 Thanks,

Chris

---

### Post by TheFu on 2014-04-08
Welcome to the forums.

Installing Windows first is the normal method. Microsoft will not pay any attention to previous installed OSes and **WILL** wipe the boot information from any Linux machine.

At this point, 14.04 is scheduled to be released next week. If you install the "beta2" release, it can be updated to the full, real release by normal patch methods.

Onto the attempted fix. If you plan to stay on 13.10, 
* boot from 13.10 from a flash drive - make certain it is the same version that you installed to the hdd
* run gparted w/ sudo and change the flag for /dev/sda1 to say "grub_boot"; close gparted
* sudo mount /dev/sda2 /mnt
* sudo grub-install --boot-directory=/mnt/boot /dev/sda
Reboot. In theory, everything should be fine.

If things don't work, then read the UEFI ubuntu page carefully and ensure things like secure boot are disabled in BIOS.

---

### Post by oldfred on 2014-04-08
You show a Windows boot loader in the MBR. Are you trying to boot in Legacy/CSM/BIOS mode not UEFI?

Also if installing Windows 7, the DVD is BIOS/MBR partition install only. But you now have Ubuntu in UEFI/gpt partitioning. Installing Windows 7 from DVD will reformat drive to MBR and erase Ubuntu. And it does the conversion incorrectly leaving gpt backup partition table so Linux sees both MBR & gpt and does not work until you houseclean old gpt data.

You can convert a Windows 7 DVD to a flash drive and make some updates to make it a UEFI installer.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
      
 Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)


  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

   Convert Windows BIOS to UEFI - Also command line install of files to efi partition
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

