---
title: "Failed Ubuntu install (Unable to install GRUB in /dev/sda when installing GRUB)"
date: 2023-01-26
forum: Installation &amp; Upgrades
---

### Post by enoutnubu23 on 2023-01-26
I'm on about my 10th installation attempt of Ubuntu (my latest attempt was 22.10). It's constantly fails at the very end as it's dealing with Grub and the boot files(?) . I'm running on a seemingly, fully-compatible mini-PC with Windows 11. It's a modern UEFI system though at some point I probably tried legacy mode in UEFI as well. I've tried with Secure Boot on and off. CentOS did install without problems. Here's one of the fail pastebins:

[https://paste.ubuntu.com/p/3pnftrhFgK/](https://paste.ubuntu.com/p/3pnftrhFgK/)

I'm a Mac user by nature and only vaguely familiar with some basic Unix stuff.

---

### Post by TheFu on 2023-01-26
You need to use the same boot method that Windows uses, if you are attempting to dual boot.  Win8+ was UEFI, so you should use UEFI for Linux too.

If you are new, don't use 22.10, unless you KNOW your hardware is so new than 22.04 won't work.  Otherwise, use 22.04.  Never use a non-LTS release, if you can help it.  Do you really want to reinstall every 6 months?  22.10 support ends in June, but 22.04 support ends for all official flavors in April of 2025 or 2027 for Gnome and Server releases.

There are lots of ways that installs can go bad, especially dual-boot installs.  What's worse is that a Windows update in a few months might break the Linux boot process, so you'll need to fix it.  Be certain to thank MSFT for this hassle.  They don't like to play nice with other OSes.

Since you should be using UEFI, there's a FAT32 partition where the ubuntu boot shim gets places.  You wouldn't be installing grub into the area before partitions.   So, go back and change your BIOS settings to use EFI/UEFI booting, not "legacy" and do the install again.

Some SSDs need firmware updates to work.
Some motherboards need firmware/BIOS updates.
Some nvidia GPUs break booting, so some kernel options are needed until the proprietary nvidia drivers can be loaded.
There are some other odd, unusual things that can go wrong too.  But for well-supported hardware (about 90% of us) don't have any issues with installations.  That doesn't help you today.

If this doesn't get you to a booted Ubuntu, take the Ubuntu installer flash drive you made, tell it you want to "Try Ubuntu", install Boot-Repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) following the "2nd option : install Boot-Repair in Ubuntu" but don't actually let it try to fix the issues.  It can make things much worse.  Run the "BootInfo" report and post the URL it provides back here.  Then some gurus can look through that and likely know exactly the issue.

---

### Post by oldfred on 2023-01-26
What brand/model system? What video card/chip?

Since you installed BIOS version of grub (legacy) to PBR of sda4, you must not boot in BIOS mode. You can leave those grub installs, but they will never work and will just give error messages. Removing BIOS grub is more dangerous for a new user than just leaving them. But correctly installing UEFI version is required, so you can boot.

Is Windows fast start up or bitlocker on? Those must be off.

Some more general UEFI install info in link below in my signature.

---

### Post by enoutnubu23 on 2023-01-26
I only tried 22.10 as a last resort. Many previous attempts were 22.04, since I've seen this issue in various similar forms I thought perhaps there was hope in a new release.
It's definitely been set to 'UEFI' and not 'Legacy' or 'Dual' for the last several attempts.
Kamrui Mini-PC, (16GB+256SS/Intel Celeron J4125).  I don't think flashing the BIOS is an option currently.
I'll get the BootInfo shortly.

---

### Post by enoutnubu23 on 2023-01-26
> **oldfred said:**
> What brand/model system? What video card/chip?

Since you installed BIOS version of grub (legacy) to PBR of sda4, you must not boot in BIOS mode. You can leave those grub installs, but they will never work and will just give error messages. Removing BIOS grub is more dangerous for a new user than just leaving them. But correctly installing UEFI version is required, so you can boot.

Is Windows fast start up or bitlocker on? Those must be off.

Some more general UEFI install info in link below in my signature.

[COLOR=#000000]Kamrui Mini-PC, (16GB+256SS/Intel Celeron J4125)
I think that install location was midway through my many attempts. I re-partitioned a few times since.
Fast start is off, BitLocker is off (possibly unavailable in UEFI don't recall)[/COLOR]

---

### Post by grahammechanical on 2023-01-26
> Here's one of the fail pastebins:

Is that Boot Repair report still accurate?

On a UEFI system there should be an EFI System Partition (ESP). You have an EFI System Partition. It is sda1. When we install Ubuntu using the Something Else option we direct the installer to install Grub in the EFI System Partition. There is enough room in sda1 for both Windows and Ubuntu boot files and they do co-exist.

You installed Grub to sda4. If the motherboard's boot priority is set to sda1 then of course Ubuntu will not load because the motherboard UEFI utility is not looking in sda4 for boot files.

Regards

---

### Post by enoutnubu23 on 2023-01-26
Here’s the newest boot repair info:

[https://paste.ubuntu.com/p/Dxd68wJ6nG/](https://paste.ubuntu.com/p/Dxd68wJ6nG/)

You can see the successful CentOS installs.

---

### Post by yancek on 2023-01-27
Look at lines 15-27 and you will see that you have EFI boot files for windows and CentOS but none for UbUntu.  You should have a separate ubuntu directory on the EFI partition with the EFI boot files for Ubuntu there.  Linex 88-91 show the EFI entries for your computer and yo can see there are entries for windows and CentOS and none for Ubuntu.  If you have been booting and installing EF, then you need to leave the default of bootloader install or select the EFI poartition (sda1).  I have selected the device such as sda for install with an EFI system and it also installs the EFI files on the EFI partition.  Do not install to the partition with Ubuntu (sda5) as you have no other bootloader to boot it from that location.i

---

### Post by tea for one on 2023-01-27
Possibly a security option in your UEFI settings is preventing Ubuntu installing the boot files successfully.
e.g. Trusted Platform Management or similar?
The security choices can be disabled to avoid any obstacles during Ubuntu installations.

According to the boot-repair report, you have installed Ubuntu
[COLOR="#0000FF"]Line 56[/COLOR] - Ubuntu 22.10 on sda5
But, as mentioned by yancek, the boot files are still CentOS.

Did you try the default repair offered by boot-repair?

---

### Post by enoutnubu23 on 2023-01-27
> **tea for one said:**
> Possibly a security option in your UEFI settings is preventing Ubuntu installing the boot files successfully.
e.g. Trusted Platform Management or similar?
The security choices can be disabled to avoid any obstacles during Ubuntu installations.

According to the boot-repair report, you have installed Ubuntu
[COLOR=#0000FF]Line 56[/COLOR] - Ubuntu 22.10 on sda5
But, as mentioned by yancek, the boot files are still CentOS.

Did you try the default repair offered by boot-repair?

'Secure Boot' is the only security-related thing I can see in UEFI. I have disabled that. I can screen-shot the UEFI options. They're pretty simplistic.

On the 2 or 3 occasions when I tried an install and then pursued the boot-repair process the boot-repair always fails.  The one error I did jot down was 'Error detected in grub_mkconfig. Please report this message to [email]boot-repair@gmail.com[/email].'

---

### Post by enoutnubu23 on 2023-01-27
> **yancek said:**
> Look at lines 15-27 and you will see that you have EFI boot files for windows and CentOS but none for UbUntu.  You should have a separate ubuntu directory on the EFI partition with the EFI boot files for Ubuntu there.  Linex 88-91 show the EFI entries for your computer and yo can see there are entries for windows and CentOS and none for Ubuntu.  If you have been booting and installing EF, then you need to leave the default of bootloader install or select the EFI poartition (sda1).  I have selected the device such as sda for install with an EFI system and it also installs the EFI files on the EFI partition.  Do not install to the partition with Ubuntu (sda5) as you have no other bootloader to boot it from that location.i

Yes, it would seem I should have those EFI boot files there. CentOS was able to do, why is Ubuntu unable to? When installing Ubuntu I have tried both selecting the 'device' 'sda' as the boot location (thinking choosing the device v. the partition meant it might be looking for it on it's own) AND tried selecting the correct BOOT/EFI partition as well. Same failures.

---

### Post by tea for one on 2023-01-27
> **enoutnubu23 said:**
> Yes, it would seem I should have those EFI boot files there. CentOS was able to do, why is Ubuntu unable to?
Yes, it's a bit of a mystery why Ubuntu fails to install the EFI boot files.
This site has instructions for installing Grub via a live session.
[https://techbit.ca/2018/09/repair-grub2-efi-boot/](https://techbit.ca/2018/09/repair-grub2-efi-boot/)

---

### Post by enoutnubu23 on 2023-01-27
I've noticed some install guides mentioned that the option 'install along side another OS' is available &#8230; do we know how that option is willed into existence? Replace or 'something else' are the only options available to me.

---

### Post by oldfred on 2023-01-27
That might indicate Windows fast startup or hibernation is on.
If installer cannot see NTFS because of hibernation flag, it probably cannot see the ESP.

Note that Windows updates may turn fast startup back on as it is a default.
And Windows may update UEFI firmware, which can reset UEFI to default settings. 
So check settings again.

---

### Post by enoutnubu23 on 2023-01-27
> **tea for one said:**
> Yes, it's a bit of a mystery why Ubuntu fails to install the EFI boot files.
This site has instructions for installing Grub via a live session.
[https://techbit.ca/2018/09/repair-grub2-efi-boot/](https://techbit.ca/2018/09/repair-grub2-efi-boot/)

I gave this a try, booting from a live USB' (not sure if that's the correct terminology).

After getting through the first few steps, step '5. Fix Grub' is where things go awry. I get the error "Installing for x86_64-efi platform. grub-install: error: unknown filesystem.' What does it mean by 'unknown filesystem'&#8212;a fundamental filesystem issue or a directory naming problem?  I mean I can 'ls' the partition etc. (otherwise I couldn't have been able to do the previous steps in the instructions for manual grub setup. Does this partition need to be a certain format for Ubunutu that's different for Windows? Or can it be an format type for Windows that doesn't work for Ubuntu (even though it did for CentOS)?

Also, can I ask a dumb question? The directories in the EFI/Boot partition don't really match much of what I see in guides when it come to case-sensitivity. Like 'BOOT' v. 'Boot' (mine's 'Boot'). Does this cause problems?

---

### Post by oldfred on 2023-01-27
Windows formats do not care about case. So Boot & BOOT are the same.
But Linux formats do care about case.

---

### Post by enoutnubu23 on 2023-01-27
I assumed that was the case. This has nothing to do with my issues, right?

---

### Post by tea for one on 2023-01-27
> **enoutnubu23 said:**
> After getting through the first few steps, step '5. Fix Grub' is where things go awry. I get the error "Installing for x86_64-efi platform. grub-install: error: unknown filesystem.'
It would be helpful to see the exact command and error message.
You can copy terminal output and paste it within code tags via advanced reply.

Although, I think that you should first double check the Windows settings mentioned by oldfred in post 14.

---

### Post by enoutnubu23 on 2023-01-27
> **tea for one said:**
> It would be helpful to see the exact command and error message.
You can copy terminal output and paste it within code tags via advanced reply.

Although, I think that you should first double check the Windows settings mentioned by oldfred in post 14.

```
root@ubuntu:/# grub-install /dev/sda
Installing for ×86 64-efi platform. grub-install: error: unknown filesystem.
```

I'll do a reboot to UEFI shortly (I was just trying to stay in the USB Ubuntu for as long as I could.

---

### Post by enoutnubu23 on 2023-01-27
Secure Boot is off. I don't see fast boot unless they mean 'Quiet boot' and that has always been disabled. The only possibility is FTPM? (Sorry the images aren't in a reasonable order)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291641&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291642&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291643&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291644&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291645&stc=1[/IMG]

---

### Post by oldfred on 2023-01-27
Fast start up & bit locker are Windows settings.

Fast Boot and Secure Boot are UEFI settings.

Updates by Windows or even fwupdate in Linux may revert changed settings to defaults.
So whenever an issue, best to check all settings you change. I have to keep a list.

---

### Post by tea for one on 2023-01-27
You have ftpm - Firmware Trusted Platform Module.
I asked about similar options in post 9?

I suggest that you disable ftpm.
Then, boot into Windows and disable hibernation (fast startup).
Also check that bitlocker is disabled.
Power off.
Reboot into the installer and try to install again.

---

### Post by enoutnubu23 on 2023-01-27
> **tea for one said:**
> You have ftpm - Firmware Trusted Platform Module.
I asked about similar options in post 9?

I suggest that you disable ftpm.
Then, boot into Windows and disable hibernation (fast startup).
Also check that bitlocker is disabled.
Power off.
Reboot into the installer and try to install again.

I had tried an install before your response with just FTPM disabled. Install failed.

Just attempted again with Fast Startup disabled (Bit Locker wasn't on). Install failed.

It just can't seem to install grub on the first partition of the drive.

---

### Post by enoutnubu23 on 2023-01-27
I know it's probably much more complicated than this but can I somehow just find or create the necessary boot files and copy them to the EFI partition along with Windows and the now defunct CentOS?

---

### Post by enoutnubu23 on 2023-01-27
Figuring I had little to lose, I decided maybe the partition itself was the problem. Not knowing if any of this would work I shrunk the existing, broken Ubuntu install partition a little to create a new temporary partition, copied the files from the original boot partition the new partition, re-formatted the original boot partition and moved the files back. Ubuntu then installed correctly. I think I might need to update grub or understand how it works as I'm having to use UEFI to select boot OSes manually but it's a start. 

So in the end, it was a corrupt boot drive. Keep in mind the machine was a couple days old.

---

### Post by oldfred on 2023-01-27
I am surprised that worked without reinstalling boot loaders.
UEFI uses the GUID/partUUID of the ESP to find the boot files.
Then in the ESP for Ubuntu is a 3 line configfile grub.cfg that just loaded the full grub.cfg in your install.

You can see UEFI boot entries and the GUID it looks for.
sudo efibootmgr -v

And then the the partUUID(GUID) of the ESP and UUIDs of your install.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

The UUID also must match the UUID mounted as the ESP in your fstab or a grub reinstall will not work.
cat /etc/fstab

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

The Boot-Repair Summary report shows all the details, so you can trace the boot process from partUUID, to ESP to / install.

---

### Post by tea for one on 2023-01-28
Congrats on solving the problem - admirable perseverance.
> **enoutnubu23 said:**
> re-formatted the original boot partition and moved the files back. Ubuntu then installed correctly.
An EFI (fat32) partition can be corrupted if you have to shutdown the PC via the power button.
Maybe that happened after one of the failed attempts?
It is difficult to identify a damaged ESP if you are concentrating on booting a USB (which has its own ESP)
Chkdsk in Windows may have helped or fsck in Ubuntu (e.g. Dirty bit is set. Fs was not properly unmounted and some data may be corrupt)
> I think I might need to update grub or understand how it works as I'm having to use UEFI to select boot OSes manually but it's a start.
Probably better to start a new thread for this.

If you see fit, it is a nice gesture to mark the thread as solved to help other users/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by enoutnubu23 on 2023-01-28
Thanks to everyone for their help along the way!

---

