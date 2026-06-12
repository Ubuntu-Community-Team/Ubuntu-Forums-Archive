---
title: "Cannot access Win8 after installing Ubuntu"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by SomeColorMage on 2013-04-07
Hello,

I recently installed Ubuntu 12.04.2 64-bit on my laptop (Asus F501A), configured to dual boot with Windows 8, following the instructions given at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). After installing, Ubuntu worked perfectly, however I could not access Windows from GRUB, giving the errors "unknown command 'drivemap'" and "invalid EFI file path". I ran boot-repair with the recommended repair, and this added extra Windows options to GRUB (Windows UEFI bkpbootmgfw.efi and Windows Boot UEFI loader), but these do not work either, giving errors "no such device: FACC-1C23" and "file not found".

Paste of the second attempt at boot-repair (which made no apparent changes) is at [http://paste.ubuntu.com/5685009/](http://paste.ubuntu.com/5685009/). Secure boot and fast boot are both disabled. The drive I installed Ubuntu on is an external hard drive seperate from the one Windows is installed on, if that makes a difference.

Please advise a fix. Thanks in advance.

EDIT: In case it helps, I found the paste of my first attempt at boot-repair: [http://paste.ubuntu.com/5684961/](http://paste.ubuntu.com/5684961/).

---

### Post by BmanTheBoss on 2013-04-07
When the computer is booting up, hit esc (or whichever key brings you to the OS choice menu) a lot, and you should be able to choose Windows 8. One thing though, make sure you do this when the computer itself is booting up, not when Ubuntu is booting up.

---

### Post by oldfred on 2013-04-07
Boot-Repair has renamed the Windows boot file. It has to do that for UEFI that did not follow UEFI standard and only allow the Windows efi file to boot. Boot repair substitutes grub2's shim file that has the same Microsoft secure boot key to boot into grub and from grub menu you should be able to boot Window&#8217;s backup file.

Have you turned secure boot back on. While some system both both with secure boot on or off, many that need the file rename will only work with secure boot on.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by SomeColorMage on 2013-04-07
Esc spam doesn't work. Every option (even Windows Boot Manager) takes me to GRUB.

Enabling secure boot in the Aptio setup utility doesn't work. Says "Invalid signiature detected" and goes back to Aptio, can't even choose an OS.

Ran boot-repair with "backup and rename EFI files" ticked ([http://paste.ubuntu.com/5687662/](http://paste.ubuntu.com/5687662/)) did not make any changes at all.

The LiveCD won't run with secure boot enabled either. Should I try running boot-repair with secure boot ticked regardless?

---

### Post by oldfred on 2013-04-07
I think the rename has to have secure boot ticked. And I thought you have to have secure boot enabled. Live flash drive should boot with secure boot enabled, but some of these UEFI implementations are very particular.

---

### Post by texbrew on 2013-04-07
> **SomeColorMage said:**
> Esc spam doesn't work. Every option (even Windows Boot Manager) takes me to GRUB.

Enabling secure boot in the Aptio setup utility doesn't work. Says "Invalid signiature detected" and goes back to Aptio, can't even choose an OS.

Ran boot-repair with "backup and rename EFI files" ticked ([http://paste.ubuntu.com/5687662/](http://paste.ubuntu.com/5687662/)) did not make any changes at all.

The LiveCD won't run with secure boot enabled either. Should I try running boot-repair with secure boot ticked regardless?

First, let me say I'm an absolute noob to ubuntu, and I just joined the forum a few minutes ago. I wish I had searched this forum while I was trying to fix a *_very similar problem_*, so I could have tried the suggested fixes.

A brief run-down of what happened to me, and how I fixed it:

While running ubuntu 12.04 lts from a usb flash drive, I decided to do a full install, intending to install it inside Windows XP (on an old PC).

Instead, ubuntu installed itself on an external hard drive, which was plugged into another usb port. After that, when I tried to restart Window XP, I got white-text-on-black screen, displaying a message much like the one you mentioned, "device not found" followed by a long machine language address, followed by a grub> prompt. Any attempt to re-install ubuntu just used up more space on the external hard drive, and I couldn't even access the main hard drive. Although I don't have a lot of love for Windows XP, I wanted to be able to use that hard drive with ubuntu.

So I looked around the net and found a free Windows & Linux repair utility called, "Paragon Rescue Kit 11 Free". You can google it. They require you to "like" them on facebook, register, then they email you a product key, etc. which you paste into two fields when you launch the free download. Sounds kinda complicated, but it really isn't. Also, I was squeamish about launching this thing on my other machine, so I did a little investigating first. So you download the utility, launch it, burn it to a cd, then boot it from cd in the ailing machine. It allowed me to look around in the sick machine, verify the boot drive - "C", etc. To be honest, I tried several menu options and don't remember them all,_* but the one I think did the trick was called, Repair Master Boot Record*_, or something like that. Apparently this software checks to see what version of Windows is installed and acts accordingly. After getting a "Success" message from the software, I pulled the CD and rebooted. Windows XP came back up not once, but twice (I wanted to make sure). So I now had access to the main hard drive.

Next, I said goodbye and good riddance to WinXP and did a full ubuntu 12.04 install on the 40 gig main drive. You probably don't want to do that with your Windows 8, and that's understandable. And I don't recall if the rescue software mentions Windows 8 compatibility, but I think it's worth looking into.

Apologies for a very wordy reply, but I hope this helps you.

texbrew

---

### Post by oldfred on 2013-04-07
A lot of the old tools are good for older versions with BIOS and MBR(msdos) partitioning. 

But UEFI with gpt partitioning is totally different. For anything you find make sure it is not just Windows 8 as early versions you installed yourself are probably BIOS versions, but tools that support UEFI and gpt partitioning.

---

### Post by SomeColorMage on 2013-04-08
Well, I tried creating a live flash drive but it won't work with secure boot on either; after selecting to try without installing it just stays on a black screen, same as the CD. Is there anything else I can try?

---

### Post by oldfred on 2013-04-08
Many have to have secure boot off to install, even though Ubuntu's installer should work with secure boot on. But some vendors have modified UEFI to only boot Windows when secure boot is on. And some of those systems then cannot even boot Windows repair tools, so computer becomes a brick if Windows does not boot. Vendors are working on fixes to those issues, so make sure you have the newest UEFI/BIOS version.

---

### Post by SomeColorMage on 2013-04-12
Well this is interesting.

I figured out a way to get into Windows, but I still have a problem. If I select "Windows 8 (loader) (on /dev/sda4)" then "Windows Boot UEFI loader", the ASUS logo flashes for a second (this is part of the Windows boot loader on my computer) and then goes back to GRUB. If I select both of those a second time, I get into Windows. However, all it does is display the ASUS logo, say "Preparing Automatic Repair", read both drives for about a second, and then it just hangs.

Now, remembering my attempts to get Windows working before my first attempt at boot-repair, I know what the problem is. Windows thinks the external hard drive is broken, and for whatever reason is compelled to try and repair it if I start Windows up with it plugged in. I don't know why the repair fails to even start, but that doesn't really matter. If I can get into GRUB without having my external hard drive plugged in, I should be able to boot Windows no problem, but if I try that now, it just goes into grub rescue, spouting a very long error about how it can't find sdb5. I assume that's because the config files for GRUB are on that partition.

Is there a way I could get GRUB to run with the external hard drive removed? Like, say, moving the files needed to run GRUB onto one of the partitions of the internal hard drive and getting it to run from there?

---

### Post by oldfred on 2013-04-12
Post the latest link to a new BootInfo report from Boot-Repair.

Post #3 says why the BIOS Windows boot entry should never work with UEFI. Bug in grub's os-prober.

---

### Post by SomeColorMage on 2013-04-13
OK. [http://paste.ubuntu.com/5706069/](http://paste.ubuntu.com/5706069/)

I know the BIOS loader shouldn't work and I don't know how using it first suddenly makes the UEFI loader works - it just does.

---

### Post by oldfred on 2013-04-13
As long as sdb is MBR based you will not be able to easily dual boot. With Ubuntu on a MBR partitioned drive you should only be able boot it in BIOS mode. But maybe you can?
BIOS and UEFI write data differently to boot. Not sure if CSM makes it work better or not?
        UEFI Compatibility Support Module (CSM)

But UEFI needs gpt partitioning to work. Your install does show the efi partition in fstab and grub/Ubuntu's efi files in the efi partition. Not sure if that will then work as once grub has loaded I am not sure the MBR partitioning makes a difference.

---

### Post by SomeColorMage on 2013-04-14
Just tried activating CSM. No changes, Windows still won't start up properly with the external hard drive plugged in and GRUB still won't run if the external hard drive's removed.

---

### Post by oldfred on 2013-04-14
If the efi version of grub will not boot the install in MBR, you need to install grub to the MBR of sdb and boot in CSM/BIOS mode from sdb.

You may be able to convert MBR drive to gpt, certain limits exist & I have never done it.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Windows only works in UEFI with secure boot systems.

---

