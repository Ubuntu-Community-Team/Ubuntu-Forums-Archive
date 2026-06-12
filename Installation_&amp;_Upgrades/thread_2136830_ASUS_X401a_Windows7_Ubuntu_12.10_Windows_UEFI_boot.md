---
title: "ASUS X401a Windows7 Ubuntu 12.10 Windows UEFI boot broken"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by socialconquest on 2013-04-18
I've tried everything I could think of and been through every post I could find related to this and still haven't found a solid answer so I thought it might be time to bring it to the community. Basically, I installed Ubuntu 12.10 (which I love) alongside the domestic windows 7 on this machine and I went through hell and a handbasket getting grub to work. Long story short, grub works but it won't let me boot windows. I've tried running disk repair (with my limited knowledge) and it does nothing. Here is the link if it suits you: [http://paste.ubuntu.com/5720094](http://paste.ubuntu.com/5720094)

The catch, because there always is one, is that I can't exactly run a repair cd because this particular model of notebook doesn't have a cd drive, it comes with a preinstalled recovery partition. That partition seems to be intact but I can't load from that one either. This is the error I receive when I try to load windows:

       "Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

       [3 options I don't have - no disk drive]
            File:\EFI\Microsoft\Boot\BCD
            Status: 0xc000000f
            Info: An error occurred while attempting to read the boot configuration data."

and when I try to load recovery partition:

     "error: can't find command 'drivemap'.
      error: invalid EFI file path.
      Press any key [for blinding rage]..."

And that's about it. I am most appreciative of any help you can provide. If you need any more info just let me know and I apologize I don't have it upfront because I'm a big dumb newb :)

---

### Post by oldfred on 2013-04-19
Both Windows & Ubuntu have to be same boot mode either both UEFI or both BIOS/Legacy/CSM.

It looks like you originally installed Ubuntu in BIOS mode as it will work on gpt partitions in BIOS mode. How you boot installer is how it installs.
Boot-Repair converted your BIOS install to UEFI install, but it looks like it left a (second) boot flag on the Windows main partition. In BIOS mode you have a boot flag on the Windows partition with boot files. But in UEFI with gpt partitioning the boot flag can only be on the efi partition. And you can only have one efi partition per drive.
Use gparted and click on sda3, right click and remove boot flag.

It may just then work as UEFI has to see correct efi partition to boot.

You may have to choose ubuntu from UEFI and grub menu should let you also boot Windows. Boot-Repair added new UEFI entries as grub has a bug and only still creates BIOS boot entries that will not work in UEFI.
Or you may have to choose the Windows entry as some computers only boot Windows efi file. It looks like Boot-repair did the second stage rename function for those type systems, so the original Windows file is really grub's shim file that has the Microsoft key to let it secure boot.
Some only boot with secure boot on also. So you may have to experiment with that setting.

---

### Post by socialconquest on 2013-05-05
Well, it has been some time since I got this response and I've tried every variation of everything that oldfred suggested without any results. Boot repair recently upgraded so I thought, I'll give that another shot too. At this point I'm shot. I've even tried booting with a bootable uefi usb drive (which btw is an arduous task to create) only to find that some mystery version of windows 7 home premium is on the computer because it has told me (w/multiple versions of this OS) that it is incompatable and it won't even let me run repair tools. Then I tried throwing the files from my actual recovery partition onto the bootable usb only to get the same errors as before. I wouldn't even bother but I need adobe suite on my travel machine for the freelance web dev I do. Any help would rock my socks. Oh, and here is the latest [http://paste.ubuntu.com/5634504/](http://paste.ubuntu.com/5634504/)

---

### Post by oldfred on 2013-05-05
You are still showing two efi partitions. You can only have one. Gparted uses the boot flag to set the efi partition, and in BIOS booting it would put the boot flag on the Windows partition with boot files. But in gpt partitioning the boot flag can only be on the efi partition.

Use gparted, click on sda5 and right click manage flags and remove boot flag. Make no other changes to partition or you may damage Windows.

Was system originally Windows 8? Boot-Repair has converted you to the secure boot version of grub and signed kernels. If UEFI with Windows 7 you should not need the signed versions if just UEFI with Windows 7.

Boot-Repair has also made a change to the Windows efi file. On many Windows 8 system with secure boot the UEFI has been modified internally to only boot the Windows efi file. The work around is to use the grub shim file that has the Microsoft signed key so it will still boot, but rename it to the Windows filename, then from grub you boot the backed up Windows efi file. Again if you have Windows 7 you should not need the renaming. Grub should boot from UEFI and Windows boot from UEFI or from grub menu.

You want to undo this:
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
**To undo & to rename files to their original names**, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by socialconquest on 2013-05-06
I don't actually have an option for secure boot in the BIOS. Whatever the case, I followed that whole instruction list and it still didn't work. I had all but given up and I was about to start from base one and install windows fresh and ubuntu again and behold, the bootable drive recognized an OS and let me run the repair utility. Everything works now! Thanks oldfred! I hope I'll get the opportunity to repay the favor.

---

### Post by oldfred on 2013-05-06
Glad you got it working. :)

---

