---
title: "Grub 2 dual boot issue with windwos 8"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by bandeszka on 2012-12-10
I have a samsung laptop with preinstalled windows 8. I installed ubuntu 12.10 without any error. After ubuntu install I could not boot ubuntu, so I started it from DVD and execute the boot repair. With recommended repaire the entire boot messed up - no ubuntu, no windows 8. Then I ran boot repair / advanced option and checked the secure boot flag in. Then grub boot ubuntu, but does not boot windows, although there are 4 grub entries for windows 8: 
Windows UEFI loader
- it stops with can't find drivemap command
Windows 8 (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda4)
- this two stops with inappropriate EFI path
Windows Recovery Environment (loader) (on /dev/sda6)

Then I went through on this entry: [http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
and created the custom grub 2 entry for windows 8 
menuentry "Windows 8" {   insmod part_gpt   insmod fat   insmod search_fs_uuid   insmod chain   set root='[COLOR=Red](hd0,gpt1[/COLOR])'   search --fs-uuid --no-floppy --set=root [COLOR=Red]4f84-ee2e[/COLOR]   chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi }

It results "secure boot forbids loading module from... " error message.



I attached the bootinfo output.

Any help would be appreciated - since I have no idea how to proceed.

---

### Post by khelben1979 on 2012-12-10
If the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") is messed up, then it doesn't look so good..

Have you considered getting a new harddrive and just replace the one you got? I think that would be the simplest option, and then avoid to not do the same thing all over again. I'm sure someone will reply in this thread with a better suggestion, though. :)

---

### Post by oldfred on 2012-12-10
@khelben1979
Since it is a new UEFI system it is a lot different than the older BIOS/MBR systems. MBR is not even used. Gpt partitions only have a protective MBR to prevent old tools from damaging new gpt as it often is not seen otherwise.

Post link to BootInfo report from Boot-Repair.

These will never work. Bug in grub2's os-prober. Your manual entry if you corrected UUID should work or Boot-Repair should add a similar UEFI chain entry.
Windows 8 (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda4)

So is it saying it will not boot Windows as Windows does not have the Windows secure boot signature? 

Ubuntu is using the Windows signature so it should work. But some have had to turn secure boot off, some have it work and some cannot get it to work.

Almost everyone that has gotten it to work has also had to turn off a quick boot or fast boot setting in UEFI/BIOS. I guess that bypasses some of the UEFI loading at startup.

---

### Post by bandeszka on 2012-12-10
> **khelben1979 said:**
> If the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") is messed up, then it doesn't look so good..

Have you considered getting a new harddrive and just replace the one you got? I think that would be the simplest option, and then avoid to not do the same thing all over again. I'm sure someone will reply in this thread with a better suggestion, though. :)

Disk check does not find error. However the bootinfo output starts with: "No boot loader is installed in the MBR of /dev/sda." This is interesting as I installed grub previously.

---

### Post by bandeszka on 2012-12-10
> **oldfred said:**
> @khelben1979
Since it is a new UEFI system it is a lot different than the older BIOS/MBR systems. MBR is not even used. Gpt partitions only have a protective MBR to prevent old tools from damaging new gpt as it often is not seen otherwise.

Post link to BootInfo report from Boot-Repair.

These will never work. Bug in grub2's os-prober. Your manual entry if you corrected UUID should work or Boot-Repair should add a similar UEFI chain entry.
Windows 8 (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda4)

So is it saying it will not boot Windows as Windows does not have the Windows secure boot signature? 

Ubuntu is using the Windows signature so it should work. But some have had to turn secure boot off, some have it work and some cannot get it to work.

Almost everyone that has gotten it to work has also had to turn off a quick boot or fast boot setting in UEFI/BIOS. I guess that bypasses some of the UEFI loading at startup.

I attached the bootinfo output. I have chacked the fast/quick boot option in the BIOS, but there is no such a settings. If the secure boot turned off then I got "IMAGE FAILED TO VERIFIED WITH *ACCESS DENIED*" BIOS error message.

I have no idea how can windows have the secure boot signature. Reading your response I searched for the secure signature: [http://www.pcworld.com/article/258153/windows_8_secure_boot_two_linux_distros_respond.html](http://www.pcworld.com/article/258153/windows_8_secure_boot_two_linux_distros_respond.html)
So the key can be the secure signature for windows...

---

### Post by YannBuntu on 2012-12-10
Your attached file seems invalid...

Please indicate your Boot-Info URL: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bandeszka on 2012-12-11
I can extract it. But is created a new archive ( It must be compressed about the size limit).

Thanks for check it out.

---

### Post by oldfred on 2012-12-11
Better to just post link that Boot-Repair creates when you run the BootInfo report. Makes it easier for users to see your info.

Was system UEFI originally? 
> 
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/shimx64.efi [COLOR=Red]/bootmgr /boot/bcd[/COLOR]


Typical Windows UEFI entry:

       /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
    
Your Windows boot files look like the standard BIOS/MBR files as the Windows efi files. But you have the standard UEFI/efi file structure with the hidden Microsoft reserved & efi partitions?

---

### Post by YannBuntu on 2012-12-11
**@Fred:** it's not the first time i see this, so i suspect some Windows to come with both EFI files and bootmgr in the ESP.

**@bandeszka:** instead of the script, please run Boot-Repair --> "Create BootInfo" button, and tell us the URL that will appear. This will provide us much more informations. See the link in my last post.

---

### Post by bandeszka on 2012-12-17
Thank you all for the help. Here comes the boot-repair output link:
[http://paste.ubuntu.com/1444950/](http://paste.ubuntu.com/1444950/)
Any help is still appreciated.

---

### Post by bandeszka on 2012-12-17
> **oldfred said:**
> Better to just post link that Boot-Repair creates when you run the BootInfo report. Makes it easier for users to see your info.

Was system UEFI originally? 


Typical Windows UEFI entry:

       /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
    
Your Windows boot files look like the standard BIOS/MBR files as the Windows efi files. But you have the standard UEFI/efi file structure with the hidden Microsoft reserved & efi partitions?


I bought this laptop with a preinstalled win 8. Then I installed Ubuntu 12.10, but I could not boot it. So I installed easybcd into windows, but that did not solved. So I had to forget about easybcd. 
Then I boot ubuntu from dvd then start boot-repaire -> that resulted that I can boot ubuntu but cannot windows 8.

---

### Post by oldfred on 2012-12-17
If you go into UEFI/BIOS and choose Windows from the UEFI boot menu does it boot? The chain load entry from grub will only work if booting from Windows directly works.

EasyBCD did not work with UEFI, have they upgraded it? Otherwise it may be better to remove it.

Also you have some entries that will not work in grub menu.
       Boot-Repair's correct chain load entries
Windows UEFI loader
Entries from grub (with bug so they do not work)
Windows 8 (loader) (on /dev/sda2)
    

It also looks like you moved sda5 & sda6, your recovery partitions. You need to run chkdsk on them or they may not work.

Did you make a Windows repair flash drive? You should have a liveCD/DVD or repair flash disk for the current version of every operating system you have installed.
       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by YannBuntu on 2012-12-17
> **bandeszka said:**
> Thank you all for the help. Here comes the boot-repair output link:
[http://paste.ubuntu.com/1444950/](http://paste.ubuntu.com/1444950/)
Any help is still appreciated.

Please disable SecureBoot (and QuickBoot if possible) in your BIOS. See [https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error)

---

