---
title: "Cannot boot into Windows from Grub menu with Ubuntu 18.04.1 LTS"
date: 2018-10-06
forum: Installation &amp; Upgrades
---

### Post by A4Skyhawk on 2018-10-06
Boot Repair Report here: [http://paste.ubuntu.com/p/Mbkw2V9qhK/](http://paste.ubuntu.com/p/Mbkw2V9qhK/)
Acer Aspire Model AXC-603-UB17 with Win 8 installed.
Installed (dual boot) Ubuntu 16.04 LTS, then upgraded to 18.04.1 LTS, with no problems booting Ubuntu or Win from grub, until recently.
Apparently, recent dist-upgrades caused something to change so that I can no longer boot into Windows from grub menu.  I can, however, get to Win by using F12 key.
I have tried Boot-Repair but have had no success in fixing the problem.
TIA, Bill

---

### Post by oldfred on 2018-10-06
Grub only boots working Windows.
And that means fast start up/hibernation must be off or NTFS cannot need chkdsk. In those cases you usually can directly boot Windows with f12 as you have been.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

### Post by A4Skyhawk on 2018-10-06
Fast s/u, sleep, and hibernate have been off since I first installed Ubuntu.  Secure boot is also off.

---

### Post by yancek on 2018-10-06
The primary reason to use boot repair for people unfamiliar with Linux/Ubuntu is to post the information it outputs.  Use the Create BootInfo Summary option with boot repair and post the link so members here who know more than you can review it and possibly make a suggestion.

---

### Post by A4Skyhawk on 2018-10-06
Isn't that what I have as a link in my op?  I used ~$ sudo apt-get install -y boot-info && boot-info

---

### Post by oldfred on 2018-10-06
Yes, you ran Boot-Repair's report.

Is fast start up off?

---

### Post by A4Skyhawk on 2018-10-07
Yes.

---

### Post by oldfred on 2018-10-07
If Windows has down updates, it may have turned fast start up back on. And many Windows updates are now in back ground so you may not have noticed.

Boot-Repair sees all the .efi boot files in the ESP. So it creates an additional grub file 25_custom with all those entries. Many are alternative Windows boots. 
Have you tried those also?

---

### Post by A4Skyhawk on 2018-10-07
> **oldfred said:**
> If Windows has down updates, it may have turned fast start up back on. And many Windows updates are now in back ground so you may not have noticed.
  
Boot-Repair sees all the .efi boot files in the ESP. So it creates an additional grub file 25_custom with all those entries. Many are alternative Windows boots. 
Have you tried those also?

I checked Windows and fast s/u, sleep, and hibernate are still in the "unchecked" state.

The following are the options shown in the grub menu and their responses when they are selected:
Ubuntu - boots to ubuntu
Advanced Ops
Win UEFI bootmgfw.efi - screen turns purple and freezes
Win Boot UEFI loader - Displays message: Failed to open: EFI/Boot/grubx64.efi and Failed to find image: EFI/Boot/grubx64.efi.  Message lasts for ~2sec and grub reappears.
Win Boot UEFI fbx64.efi - Displays message: System BootOrder not found.  Initializing defaults.  Message lasts for ~2sec and grub reappears.
EFI/ubuntu/fwupx64.efi - Instant return of grub menu.
EFI/ubuntu/mmx64.efi - Displays blue dialog box labeled "Shim UEFI key management".  It times out in ~10sec.  I have not tried the selections offered.
EFI/OEM/Boot/bootmgfw.efi - purple screen
Windows Boot Manager (on /dev/sda2) - purple screen
System Setup
Windows UEFI - purple screen

---

### Post by A4Skyhawk on 2018-10-07
I have a folder from 2016 in which I saved some .efi files.  In comparing the size of these files to the same ones currently in use in Ubuntu 18.04.1, there are some differences:
bootx64 from 2016 is 1.6 MB vs 1.3 MB for 2018.
fwupx64 is 64.4 kB vs 69.5, 71.4, and 65.6.
mokmanager is 1.3 MB vs (non-existent)
fbx64 is (non-existent) vs 1.2 MB.
mmx64 is (non-existent) vs 1.3 MB.

---

### Post by A4Skyhawk on 2018-10-07
I copied grubx64.efi to /EFI/Boot.  After grub update and reboot, selecting "Win Boot UEFI loader" reverts to the grub menu.
I copied bootmgfw.efi to /EFI/Boot.  After grub update and reboot, there are no changes to the responses of any of the options on the grub menu.

---

### Post by A4Skyhawk on 2018-10-09
[FONT=Arial, sans-serif][SIZE=3]Strange behavior after running Boot-Repair/Advanced.  Rebooted and got the grub menu (similar to post #9), selected &#8220;Win UEFI bootmgfw.efi&#8221; and it booted to Windows.  Good news.  But exited Win with restart, got the grub menu, selected &#8220;Win UEFI bootmgfw.efi&#8221; again, and this time got a purple screen.  Tried numerous restarts, selecting &#8220;Win UEFI bootmgfw.efi&#8221;, and got the same purple screen.  So I did an Advanced B-R again, and, as above, was able to boot into Win.  But again, after exiting Win and getting the grub and selecting &#8220;Win UEFI bootmgfw.efi&#8221;, I got a purple screen.  Then did the Advanced B-R a third time.  Now, I am able to cycle to Win and back to grub and into Win successfully - 4 times, so far.  [/SIZE][/FONT] 
 &#8220;[FONT=Arial, sans-serif][SIZE=3]Win UEFI bootmgfw.efi&#8221; is the only option in the grub that boots into Win.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=3]Is there anything else that I should do, or is my problem now &#8220;solved&#8221;? [/SIZE][/FONT] 
 
 
 [FONT=Arial, sans-serif][SIZE=3]Paste bin: [http://paste.ubuntu.com/p/kCH8SVksQJ/](http://paste.ubuntu.com/p/kCH8SVksQJ/) [/SIZE][/FONT]

---

### Post by ubfan1 on 2018-10-09
Nothing looks wrong in the boot-repair link, but the error message:
Win Boot UEFI loader - Displays message: Failed to open: EFI/Boot/grubx64.efi and Failed to find image: EFI/Boot/grubx64.efi. 
looks like an earlier install with secure boot on left /EFI/Boot/bootx64.efi as a copy of shim, the the next install, renamed this to
/EFI/Boot/bkpbootx64.efi, and when run from grub, complains that the grubx64.efi file is not
in the same directory.  Copy grubx64.efi there and see if that fixes the error (which should start grub),
or copy the Windows bootloader /EFI/Microsoft/Boot/bootmgfw.efi there as the bkpbootx64.efi file to hopefully boot Windows.

---

### Post by A4Skyhawk on 2018-10-09
> **ubfan1 said:**
> Nothing looks wrong in the boot-repair link, but the error message:
Win Boot UEFI loader - Displays message: Failed to open: EFI/Boot/grubx64.efi and Failed to find image: EFI/Boot/grubx64.efi. 
looks like an earlier install with secure boot on left /EFI/Boot/bootx64.efi as a copy of shim, the the next install, renamed this to
/EFI/Boot/bkpbootx64.efi, and when run from grub, complains that the grubx64.efi file is not
in the same directory.  Copy grubx64.efi there and see if that fixes the error (which should start grub),
or copy the Windows bootloader /EFI/Microsoft/Boot/bootmgfw.efi there as the bkpbootx64.efi file to hopefully boot Windows.

                        [FONT=Arial][SIZE=3]OK.  Did ~$ cp /mnt*/*EFI/ubuntu/grubx64.efi /mnt/EFI/Boot.  No change in responses to any selections in grub menu.  Good so far.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]Then did ~$ cp /EFI/Microsoft/Boot/bootmfgw.efi /mnt/EFI/Boot/bkpbootx64.efi.  Then “Win UEFI bootmgfw.efi” resulted in purple screen; numerous re-trys, same results.[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]Then did Advanced B-R (with “Secure Boot” unchecked.  Note: I *may* have done some previous B-Rs with “Secure Boot” left “checked” by mistake.  My BIOS is set up with this “disabled”.)  Now “Win UEFI bootmgfw.efi” boots to Win and other grub menu options perform as before (either reverts to grub or purple screen).[/SIZE][/FONT]
 
 
 [FONT=Arial][SIZE=3]A couple questions:[/SIZE][/FONT]
 [FONT=Arial][SIZE=3]1) Where in the Boot Report did you find the error message you referred to?  [/SIZE][/FONT]

 [FONT=Arial][SIZE=3]2) Would it be possible to see a “logic diagram” of the boot-up steps that involve the 10 files that are shown in boot/efi/EFI?  A “logic diagram” or “flowchart” would help, I think.  TIA.[/SIZE][/FONT]
 
 
 [FONT=Arial][SIZE=3]New paste bin url:  [http://paste.ubuntu.com/p/QNmwn7jVZ3/](http://paste.ubuntu.com/p/QNmwn7jVZ3/)  [/SIZE][/FONT]

---

### Post by oldfred on 2018-10-10
UEFI is supposed to allow any entry boot, some vendors modify UEFI and use description to limit boot.

Windows boots from /EFI/Microsoft/Boot/bootmfgw.efi.
Ubuntu boots from /EFI/ubuntu/shimx64.efi or grubx64.efi. 
Shimx64.efi is for UEFI secure boot and grubx64.efi is for UEFI standard boot, but shimx64.efi works with secure boot off. 
Systems may offer a "fallback" or hard drive boot entry at /EFI/Boot/bootx64.efi for internal drives. This path/file is the standard UEFI entry for all external drives. Both Ubuntu installer & Windows installer use this, but bootx64.efi is obviously different.

Grub used to not install anything into /EFI/Boot.
Boot-Repair would copy any existing /EFI/Boot/bootx64.efi to /EFI/Boot/bkpbootx64.efi. If it exists before Ubuntu install, it was just a copy of Windows bootfgw.efi. And Boot-Repair would copy shimx64.efi to /EFI/Boot/bootx64.efi  and add boot stanza to boot both bootx64.efi & bkpbootx64.efi if not existing.

Now grub does copy some files into /EFI/Boot as /EFI/Boot/bootx64.efi. Not sure if it backs up the Windows file if it exists, nor am I sure if it is grubx64.efi or shimx64.efi that a grub install uses, it may depend on whether you are installing in UEFI Secure boot or not.

When we manually copied shimx64.efi to /EFI/Boot/bootx64.efi we also had to make sure we had the /EFI/ubuntu folder with all its files as the standard shim or grub was/is hard coded to look for additional files in /EFI/ubuntu. The version of grub in the installer has all files in /EFI/Boot folder but is a very minimal version of grub just to boot flash drive.

Have not seen any real documentation on details of grub's install process. Just based on observation of how it works, but recent grub updates did change some things. And while UEFI is a standard, diffferent vendors implement it differently and even violate some parts of standard.

---

### Post by A4Skyhawk on 2018-10-10
[FONT=Arial, sans-serif][SIZE=3]Update:  This morning, when booting up the pc and getting the grub menu, selecting "Win UEFI bootmgfw.efi" resulted in a purple screen.  Looks like the changes didn't stick.  I re-checked Win power options - fast s/u, sleep, and hibernate are unchecked.  Also, BIOS secure boot is still off.  [/SIZE][/FONT]

---

### Post by ubfan1 on 2018-10-10
The error message came from your #9 message, not the boot-repair report.   
The setup of /EFI/Boot with shimx64.efi/bootx64.efi/grubx64.efi is probably still wrong, given that the problem is in grub itself (bug #1453980) -- the --uefi-secure-boot option does nothing.  Do join the bug to at least get it confirmed.
Most of the .efi files are tests or key manipulation, not needed in most cases.  shim runs grub if in the same directory.  grub (where ever it runs) looks in /EFI/ubuntu for the grub.cfg configuration file, which typically just pulls in the grub.cfg file from the main install's /boot/grub directory.   grub then runs the selected efi file, (a kernel if a normal boot).
 --- fixed typo in bug number ---

---

### Post by A4Skyhawk on 2018-10-10
Can't find bug #14539780.

---

### Post by A4Skyhawk on 2018-10-11
[SIZE=4][FONT=Arial, sans-serif]Following my post #9 yesterday, I did another Boot-Repair, and was able to reboot into Win w/   [/FONT]&#8220;[FONT=Arial, sans-serif]Win UEFI bootmgfw.efi&#8221;.  I immediately followed this with 12 &#8220;restarts&#8221; and &#8220;shutdowns&#8221; from Win and Ubuntu and was likewise successful w/ booting into Win from grub, ending w/ a s/d from Ubuntu.  I booted from grub into Win, shutting down from Ubuntu, 3 more times about 4 hours apart.  And this morning, I am having the same success booting into Win from grub.[/FONT]
[/SIZE]
[SIZE=4] [/SIZE][SIZE=4][FONT=Arial, sans-serif]I am marking this problem as solved. [/FONT][/SIZE]

---

