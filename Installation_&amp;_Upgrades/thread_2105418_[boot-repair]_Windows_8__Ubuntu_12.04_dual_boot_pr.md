---
title: "[boot-repair] Windows 8 / Ubuntu 12.04 dual boot problem"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by RANDOM_HERO_87 on 2013-01-16
Hi all,
Recently got a new Dell XPS15 laptop. The laptop came with Windows 8 by default (no provided installation media). Have been having some real difficulties with dual booting Ubuntu 12.04 and Windows 8. Running on EFI, in installed ubuntu, after which grub would not boot into Windows, I used a Ubuntu systems disk and followed the steps to restore grub via boot-repair, after which everything was working correctly.

For two weeks this was working, then today suddenly I could not boot into windows, I decidedly ran boot-repair again, however this did not solve the issue. This time, I noticed in the grub boot menu some differences in the item names, now have:
- Windows UEFI recovery bootmgfw.efi
- Windows Boot UEFI recovery
- EFI/Dell/Boot/bootmgfw.efi
- EFI/Dell/Boot/bootx64.efi

The first two options are producing a blue windows 8 screen with the follwing message:
"The boot configuration data file is missing some required information 0xc0000035"

The EFI/Dell lines produce a similar blue windows 8 screen with the following message:
"A required device isn't connected or can't be accessed 0xc0000225"

None of the above options are working. The only thing that has changed over the past days or so was ubuntu was updated to 3.2-36 kernel, but I was still able to access windows just yesterday.

Below in a link to my boot-repair BIS:
[http://paste.ubuntu.com/1536560/](http://paste.ubuntu.com/1536560/)

any help would be appreciated.

---

### Post by RANDOM_HERO_87 on 2013-01-16
Further attempts. still having access to ubuntu, I have checked the grub file at /etc/grub.d/25_custom

I mounted the EFI partition and confirmed that the respective files for the EFI/Dell items do indeed exist.

However, when the system was operating correctly i distinctly remember the Windows 8 boot item included the .bkp extension.

another thing I noticed, looking at the /etc/grub.d/25_custom and /boot/grub/grub.cfg files was that the ubuntu boot items
correctly associate the root flag to the drive partition. looking at the pastebin in the first post.

each ubuntu/linuxmem test points root at:
--set=root 15fc002e-15d6-4d1c-9a80-93a0dbc487bd
this corresponds the the ext4 partition

however the windows 8 items in the above mentioned files are pointing root at:
--set=root 5665-3E93
this corresponds to the EFI partition, tried changing this to the Windows 8 partition, but I only assume this will not boot in EFI mode, as a result this did not work.

A little lost right now, could it be that somehow the Windows 8 EFI boot record has become corrupt? is there something else I might be able to try?

---

### Post by RANDOM_HERO_87 on 2013-01-16
Anyone have any insight. I'm starting to think that maybe it's a windows boot problem. I believe there are some EFI boot files on the windows partition \Windows\Boot, could these be corrupt?

would appreciate any help

---

### Post by YannBuntu on 2013-01-16
I think so too. 
Use a Windows8 disc this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) until you get direct access to Windows. Then use Boot-Repair to recover GRUB.

---

### Post by RANDOM_HERO_87 on 2013-01-17
thanks, I will give this a try when i get my hands on a Windows 8 Installation disc

---

### Post by oldfred on 2013-01-17
It looks like you have the Intel SRT?

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

            Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

---

### Post by RANDOM_HERO_87 on 2013-01-17
That is correct, the system is using Intel SRT. However, I did not have a problem installing ubuntu, and everything (dual boot) had been working fine with SRT enabled. Current status, ubuntu is still operational, but windows has the previously mentioned boot errors.

For this windows 8 boot issue I did try booting with SRT disabled, but the result was the same.

However, thinking about it, could it be possible that SRT is the root cause of the boot error/corruption? I believe this ties in with Intel Rapid Storage Technology, of which my windows 8 system was running in 'Maximise Mode'. The reason for this assumption, battery life can be abit flaky with this laptop, sometimes quickly run till down to single digits percentage wise. I believe i've shutdown cleanly each time, but cannot be 100% sure.

Anyway, I will attempt to use the installation discs to perform a repair when I have acquired them.

---

### Post by RANDOM_HERO_87 on 2013-01-18
Managed to get my hands on a windows 8 iso file. Thanks for the help YannBuntu and oldfred, my dual boot system is now operational again.

the following links were valuable:
- [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
- [http://answers.microsoft.com/en-us/windows/forum/windows_8-system/window-8-doesnt-boot/996937e6-8103-4752-be26-03c900ed5d5d](http://answers.microsoft.com/en-us/windows/forum/windows_8-system/window-8-doesnt-boot/996937e6-8103-4752-be26-03c900ed5d5d)
- [http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx](http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx)

including the links posted by oldfred

If anyone is interested these are the steps I followed to resolve this issue:
1. obtained an iso of windows 8
2. format a usb stick in FAT32 using gparted
3. mount the windows 8 iso and copy it's contents to the formatted usb stick
4. *important* if intel smart response technology (SRT) is enabled in the bios, please disable it, it will allow the following commands/steps to see your harddisk
5. follow the steps in the fist link to open the command prompt
6. using disk part check to see if your disk is visible, from link 3, type the following in command prompt.
> Diskpart can also be used to mark the partition as active from the Windows RE.
Diskpart
LIST DISK
SELECT DISK (followed by the number of the disk . most likely 0)
LIST PARTITION
SELECT PARTITION (followed by your partition number. most likely 0)
ACTIVE
EXIT
Windows startup recovery should now work.
7. run the commands shown in link 1
8. reboot, this did not work right away (windows still would not boot)
9. follow the steps again to return to command prompt
10. run bootrec.exe /scanos (it should see your windows partition, for me the partition displayed D rather than C, double check by entering the displayed drive, and listing the dir)
11. run bootrec.exe /rebuildbcd (should list your drive, confirm and continue)
12. exit the command prompt, return to 'Advanced Repair Options' and run 'Startup Repair' (it should not display the customary 'Windows could not repair your etc..', instead your pc should reboot automatically)
13. windows boot loader should load windows
14. load Ubuntu-Secure-Remix and restore grub using boot-repair
15. test all installation (should now be working)
16. if your previously disable it, you may now re-enable intel smart response technology (SRT)

Again, thanks for the help!

---

### Post by jslegge on 2013-04-18
I posted something here without really reading anything. Damn Google.

---

