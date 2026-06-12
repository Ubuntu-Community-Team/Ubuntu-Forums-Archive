---
title: "Unable to boot after 12.10 installation [Win8 machine - no bootable image found]"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by layr on 2013-04-09
**HP Probook 4545s**, came with Win8 installation.
First installed Ubuntu onto sparate '/' partition; after restart system rebooted into Win8 (no GRUB whatsoever). Then ran boot-repair for [the first time]("http://paste.ubuntu.com/5691845") - now system finds no bootable image; after powerup is displayed '*>>Start PXE over IPv4.*', followed by '*>>Start PXE over IPv6.*' after which system shuts down. Guess it tries to boot over the network, but obviously fails to do so.
Then returned to the [tutorial]("https://help.ubuntu.com/community/UEFI"), where discovered UEFI needs separate bootable partition. From the first boot-repair report it looks as if grub got installed into correct EFI partition nevertheless, but just in case [ran repair again]("http://paste.ubuntu.com/5691919"), defining the GRUB location onto the EFI partition.

Welp, still the same. It should be added I'm not 100% sure whether Fast boot is disabled, since the tickbox in BIOS is disabled, but comment says it would be disabled when DriveLock gets enabled, which it is. Secure boot is disabled.

---

### Post by oldfred on 2013-04-09
What is DriveLock?

You normally have to go into UEFI menu to change default boot from Windows to grub or the ubuntu setting.

But it looks like you have run the file rename which is used for those systems with hard coded UEFI that only boot the Windows efi file. That is not per UEFI standard and this is just a work around to non-standard "standards".

It looks like you have done this, just not sure if required for your system or not.
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

---

### Post by layr on 2013-04-09
> **oldfred said:**
> What is DriveLock?> DriveLock prevents unauthorized access to the contents of a hard drive. After DriveLock protection is applied to a drive, a password must be entered to access the drive and the drive can be accessed only when it is inserted into the notebook.Still no-go.
What I did:
1. run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
2. Reboot - still the same, doesn't boot anywhere (no boot-loader)
3. Enabled SecureBoot, then ran Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply

Btw, both the 'Backup and rename EFI files' and 'SecureBoot' options were already ticked by default, don't believe it changed anything.
Btw2: why is my text formatting here at ubuntuforums so bad? No indents nor newlines get passed; all text gets crumbled into one chunk instead.

---

### Post by oldfred on 2013-04-09
Are you trying with both secure boot on and off after updates. Some systems boot either way, some only boot with secure boot on. Ubuntu has the same Microsoft key so it should work but some UEFI are not standard.

Formatting depends on what you copy & paste from. I used to use gedit but now use Zim. Zim seems to give me some extra lines, but I like that I can just click on links to see if still valid.

---

### Post by layr on 2013-04-09
Yes, tried with secureBoot on and off.

Btw the forum formating issue seems to be Chromium-related: [http://ubuntuforums.org/showthread.php?t=2130762](http://ubuntuforums.org/showthread.php?t=2130762)

---

### Post by layr on 2013-04-11
Up, still no success. Would there be a way to at least boot into Windows again?

---

### Post by oldfred on 2013-04-11
Windows has a backup of its original file. You can manually copy it back into the efi partition. Path in efi partition will depend on how you mount it.

 Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Ubuntu normally shows it likd this as it is mounted at boot/efi.

 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

Then make sure UEFI is booting from the Windows entry.

---

### Post by layr on 2013-04-11
> **oldfred said:**
> Then make sure UEFI is booting from the Windows entry.
 Wait-wait, that might be my issue. Where could I set the entry UEFI boots from? I didn't set it manually for the Ubuntu either.

**  Edit:**
 Okay, got it. Sorry for my noobery, this particular computer does not belong to me and I wasn't that comfortable in its BIOS. Found out how to pick EFI files and got it working with /boot/efi/EFI/ubuntu/grubx64.efi
[U]
 In order to load GRUB automatically at startup, copy that file over /boot/efi/EFI/Boot/bootx64.efi[/U]
 

 For anyone using Probook/4545s: secure boot has to be turned off.

---

### Post by skrishna on 2013-06-18
Oops -- sorry, posted to wrong thread.

---

