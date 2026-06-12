---
title: "Grub fails to find Windows partition"
date: 2020-02-19
forum: Installation &amp; Upgrades
---

### Post by SurlyJest on 2020-02-19
First of all, I know this issue has been much discussed, but I have read and tried everything I can find so far with no relief.  Any help would be very much appreciated.

I haven't been able to dual-boot since downgrading to 18.04.4. I had been running 19.10 in dual-boot with Win 7 with no problems for some months (I upgraded from 18.04 last Nov).  I began to have stability issues after some recent update (after Feb 2) or bone-headed move on my part (dunno) and, finding no obvious issue in the OS (other than cupsd running wild on memory - another story) or hardware, I decided to try downgrading; that's when the real fun started.

First I couldn't boot at all (error: file '/grub/i386-pc/normal.mod' not found).  The help I found on this indicated I needed an EFI partiion, so I re-partitioned and re-installed using the "something else" option, creating an EFI partition at the beginning of the ssd (there was a 100 MB partition there that MAY have been left over from a previous install).   I got this to work, but then I had no dual-boot option. 

Commands sudo os-prober;sudo update-grub don't help and neither does Grub Customizer. I tried everything I could find in the Ubuntu forums and AskUbuntu. 
Boot Repair also failed to help.

Then I find this advice from OldFred ([https://ubuntuforums.org/showthread.php?t=2320894):](https://ubuntuforums.org/showthread.php?t=2320894):)
[INDENT]You have to convert Ubuntu from UEFI to BIOS to dual boot. (or reinstall Windows in UEFI mode).

Add a 1 or 2MB unformatted partition anywhere on sdc with gparted and add the bios_grub flag.
Then use Boot-Repair's advanced mode to un-install/reinstall grub. You want it to uninstall the UEFI version grub-efi-amd64 and install grub-pc for BIOS boot.
Do not run any auto fix in Boot-Repair. 
[/INDENT]

I've done this (deleting the EFI partition in the process) and now I at least get a grub menu, but still no Win7 option.  
_Current Boot Repair info at:_ [http://paste.ubuntu.com/p/cNVWq34r6N/](http://paste.ubuntu.com/p/cNVWq34r6N/).  I am not running UEFI mode from BIOS ("Other OS" option on boot) and all the disks are MBR.    

Note, I have all the OS files (Win and Linux) on the sda device (ssd). I also have 3 hard disks used for bulk storage and backup (as sdb,-c and -d). System is Asus M5A97 R2.0 with AMD FX6350 and 7850 (Pitcairn) graphics.  Nothing exciting there. 

Thanks very much for any help you can give.

---

### Post by yancek on 2020-02-19
>  I began to have stability issues after some recent update 

A recent update of what, Ubuntu, windows?  Is there any sign in any way that your computer is UEFI capable?  Rarely the default for windows 7 but it is possible to do.  In your case, it is NOT what you want to do.

>   The help I found on this indicated I needed an EFI partiion 

I expect you misunderstood what was written or it was poorly written.  Windows 7 is generally not UEFI, so that was a factor to be considered.  Windows requires UEFI on a GPT disk (which you don't have) and on a GPT disk, windows must be installed UEFI.  Neither is your situation.  Creating the EFI partition was a mistake.

The 1-2MB unformatted partition is for the purpose of installing Ubuntu in Legacy mode on a GPT disk which should have been indicated.  You don't have GPT disks so that is irrelevant in your case. 

> I've done this (deleting the EFI partition in the process)  

Your boot repair output contradicts this (lines 54-64 clearly show an EFI partition with Ubuntu files).  Did you delete it after running boot repair?  Might want to check again to verify.

If you have an EFI option in the BIOS of your computer, you need to verify that Legacy/CSM boot is available and enabled.

Lines 6-8 of boot repair show Grub in the MBR pointing to your Ubuntu partition (sda6) which is good.  Lines 91-94 show Grub installed on sda6 but unable to find the core.img file without which it won't boot. Have you tried to run sudo update-grub and has it failed to get a windows entry.

---

### Post by oldfred on 2020-02-19
You converted Windows boot partition on sda1 from NTFS with boot flag to boot Windows on sda2 to the ESP - efi system partition FAT32 with boot flag. Then it looks like you converted sda1 to a Linux partition.

Windows does not have to have a separate boot partition, but then you have to have all its boot files in the main partition, your sda2 and have the boot flag on that partition.

Grub2's os-prober does not use boot flag to find Windows but just looks for the boot files.  

You need to use your Windows repair flash drive to restore the missing Windows boot files. It looks like boot flag is on sda2, make sure it is. Then run the full set of Windows  repair tools and let it also install a Windows boot loader to sda. You deleted the boot files in sda1 when you converted it, and cannot restore Windows missing boot file from Linux, unless you have backups?

Leave Windows boot loader in sda and use grub from sdb or sdc to boot Ubuntu.
When you only have one drive in BIOS boot mode, you have to go back & forth  with grub & Windows boot managers when Windows needs repair. Grub only boots working Windows. But you can keep Windows boot loader in MBR of sda and if needed boot that and you may be able to repair Windows. But still keep working Windows repair flash drive. 
You just change BIOS from a grub drive to Windows as default & then change back once Windows repaired.

One advantage of UEFI (particularlly with one drive) is that ESP can have many boot loaders & you can easily switch which system you boot from within UEFI. It like having many MBRs with BIOS based systems.

---

### Post by dragonfly41 on 2020-02-19
> [COLOR=#000000]One advantage of UEFI (particularlly with one drive) is that ESP can have many boot loaders

Another advantage I found by experimenting is that rEFInd can be installed in the /boot/efi 
directory.

[/COLOR][https://forums.linuxmint.com/viewtopic.php?t=287353](https://forums.linuxmint.com/viewtopic.php?t=287353)

[COLOR=#000000]



[/COLOR]

---

### Post by oldfred on 2020-02-19
I like grub as I know it.

But I do have rEFInd on several old flash drives. Several are now so small as not otherwise useful, but rEFInd fits.
And I have rEFInd in ESP on my third drive in one system, but Asus UEFI seems to get confused if I have too many boot entries in its UEFI. I seem to have to totally unplug drives, reset UEFI and start over. It is ok for a while then needs rework again. 
And rEFInd booted when nothing else was working.

---

### Post by dragonfly41 on 2020-02-19
> [COLOR=#000000]It is ok for a while then needs rework again.

I agree that it has quirks which I'm trying to figure out. I now use refind.conf to configure menu options.[/COLOR]

---

### Post by SurlyJest on 2020-02-19
Thanks for the reply.  I had stability problems with Ubuntu 19.10 after the first February updates, that is the reason I tried re-installing to a cleared partition with 18.04. My Windows 7 install was done in mbr mode, with UEFI turned off (as far as I can tell - BIOS option is either Windows UEFI or Other OS, and I selected other from the start).  Since you mentioned it, I just noticed that my sda2 partition is NOT marked with the boot flag.  No idea how that happened, but setting the flag changed nothing and the Windows CD didn't repair the boot files, either.    

And now, 18.04 is coming up with an error dialog ("System program problem detected") shortly after boot and I don't see any obvious issues in syslog.  I wonder if I am having hardware problems so I'll run memtest overnight and see if that shows anything. The drives all seem healthy per fsck, anyway.

At this point, I think my best course is to do a clean windows install - might as well get Win 10 anyway, but I hate to spend that money.  My last re-install was intentionally done BIOS since I didn't want to deal with UEFI, but I guess I need to re-create the drive as GPT and start over with the "modern" setup. I used to know what I was doing with ancient PC-DOS back in the day, but I'm retired now and this is all too much like work.

Again, thanks very much for your time replying.

Mike

---

### Post by SurlyJest on 2020-02-20
Finally, successful.  It turned out that the issue was really that my Win boot had been trashed. So, finally, after running the mbr restore from my recovery disk, I could just boot windows. It still took a bit of finagling to get grub to find it, but eventually update-grub worked after re-installing from Boot Repair.  

Still may rebuild the system since I think I haven't gotten my stability issue fixed, though.

Thanks again very much for your help.

---

