---
title: "Installed Ubuntu 12.10... now Can't boot Ubunto OR Windows 8!"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by pattmayne on 2013-01-24
I got a new DELL XPS 8500 with Windows 8. I understand that it has UEFI (as opposed to traditional boot-loading BIOS system).

I installed Ubuntu 12.04 (not realizing that it doesn't work as well with the secure-load/uefi system). I partitioned my solid state drive so Windows was on one partition, and Ubuntu would be on a new one (sdb7). This always worked with my PREVIOUS computer... I had Windows XP on one partition and UbuntuStudio on a separate partition. Grub always gave me a boot menu.

Here comes the problem:

At first my computer wouldn't let me boot from the USB and with UEFI I can't get into the boot menu... with UEFI I have to access boot options via Windows. I had to un-select "secure" booting, which allowed the computer to boot from my Ubuntu USB.

I successfully installed Ubuntu, but when I restarted the computer it booted right into the USB again. I expected it to give me a boot menu (including Windows 8, Ubuntu, and the USB stick).

So I shut down the computer, removed the USB stick and restarted it... and I got the following error message on a black screen:

"Reboot and select proper boot drive or insert boot media in selected boot device and press a key."

NOW this SHOULDN'T be a huge problem... I should just "select the proper boot drive"... but I can't access BIOS or a boot menu unless I'm inside Windows!! And I can't get into Windows!

What I can do (ALL I can do) is run Ubuntu live from my USB. I've looked at lots of forums and I've tried several things, but nothing works! This is kind of a new issue so maybe nobody has had this problem yet. Others had the same error message, but from different problems. They can usually ONLY log into Windows. I can't get into Windows.

When I boot Ubuntu live from the USB I can look into the files for my Windows and Ubuntu installations, but I can't boot into either one.

Here's what I tried (which didn't work so far):

-re-installing ubuntu 12.10
-boot-repair program in Linux

Here's another piece of information. When I tried boot-repair, it told me that "The boot of your PC is in Legacy Mode... You may want to retry after changing it to EFI mode."

I don't know how to change it to EFI mode.

ALSO... boot-repair tells me to: "remember to tell the bios to boot on sdb1/EFI/ubuntu/grubfix64.efi"

I don't even know what that means.

If you're interested... I tried the boot-repair three times and got these URLs:

[http://paste.ubuntu.com/1565228](http://paste.ubuntu.com/1565228)

[http://paste.ubuntu.com/1565261](http://paste.ubuntu.com/1565261)

[http://paste.ubuntu.com/1565303](http://paste.ubuntu.com/1565303)

Anyone with any info PLEASE help me out. My brand-new computer is unbootable...

---

### Post by Sazhen86 on 2013-01-24
The only advice I can offer is to keep hitting F2 whilst it is powering on and you should get to the BIOS settings.  Also make sure the USB keyboard is plugged in directly and not using a USB hub.

Hope that helps.

---

### Post by grahammechanical on 2013-01-24
> I successfully installed Ubuntu, but when I restarted the computer it booted right into the USB again. 

Well, it would. Woudn't it? If the boot priority is to look for an OS on USB before looking for an OS on a hard disk or SSD in your case, then it would find an OS on the USB and boot it. The machine would not look any further.

This may have not been an error message at all.

> "Reboot and select proper boot drive or insert boot media in selected boot device and press a key."

It may have been another way of saying: "Cannot find an operating system."

If the BIOS/UEFI was set to only boot from USB then it would not look anywhere else for an operating system.

I see this from your last listed pastbin.

>  No boot loader is installed in the MBR of /dev/sdb.

and this

> Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sdb7 and looks at sector 369730960 of the same hard drive

But Grub is not in the MBR of sdb7. Which disk has boot priority?

Regards.

---

### Post by oldfred on 2013-01-24
Did you turn off fast boot? Some systems will only let you back in UEFI menu from Windows if fast boot is still on.

       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

To install grub to a partition, you must have installed in lebacy/BIOS mode.
You do not install grub to a partition like sdb7 even with MBR unless using another boot loader. And with UEFI all system boot from the UEFI partition as UEFI is like having multiple MBRs. If you install Ubuntu in UEFI mode it should automatically install grub-efi's boot loader to the efi partition.


Boot-Repair does convert BIOS type Ubuntu installs to UEFI installs by uninstalling grub-pc and installing grub-efi.

---

### Post by pattmayne on 2013-01-24
> **Sazhen86 said:**
> The only advice I can offer is to keep hitting F2 whilst it is powering on and you should get to the BIOS settings.  Also make sure the USB keyboard is plugged in directly and not using a USB hub.

Hope that helps.

With UEFI the time-window for hitting f2 is allegedly 0.02 seconds... not a feasible option! The nice thing about it is that Windows loads in like three seconds... except that now it won't load at all. Also, yes the USB keyboard is plugged directly into the machine.

---

### Post by pattmayne on 2013-01-24
Thanks everyone for giving me some feedback. Let's see what I can learn here...

grahammechanical:

How do I know which disc has boot priority? And how do I change that priority? The PC came already with a lot of partitions, and this whole process is very different from my previous experience with pre-UEFI bootloating and Bios. I'm totally a noob here...

So yeah... I don't know how to access the UEFI without getting into Windows. I feel like if I could get into the UEFI then I could change the settings and boot it up.

But I'm also having a problem finding where the bootloader is installed. You say it shouldn't be on sdb7?? I created that partition for Ubuntu and I assume that the bootloader was installed in the same place. Is that a mistake? If so, how can I fix it?

---

### Post by darkod on 2013-01-24
The boot device priority, and also the setting whether the machine is using uefi boot or legacy boot, is still inside bios. You have to try and get into it, even though the reaction time to press a button might be short.

As for the bootloader destination, even with legacy bios boot it never was a partition. It was always the MBR of the hdd since that's where the boot process starts. In some cases, I would say exceptions in a specific setup, people need to install grub to the ubuntu partition but in that case you need to have another bootloader on the MBR to kick off the boot process.

Since the machine came with secure boot, that complicates things further. You will have to refer to its manual and to google searches, whether you need to disable secure boot only to install ubuntu, and enable it gain, or leave it disabled. If you leave it disabled, does win8 boot since it came preloaded configured with secure boot?

In any case, to have uefi dual boot you need to install ubuntu in uefi mode too, in other words during the install boot the ubuntu cd/usb in uefi mode, not legacy.

The main thing here seems to be that you need to access the bios in any way you can. Take a look if the manual has some ideas. And judging by the message saying you have the machine in legacy boot, it seems you changed the boot type to legacy and maybe even installed 12.04 in legacy mode, not uefi.

---

### Post by pattmayne on 2013-01-24
NEW UPDATE... I did manage to get into the BIOS screen (Huge benefit here!) I just kept pressing f2 really fast LoL... and it worked!  I put it in UEFI mode instead of Legacy and kept "secure boot" turned OFF.

Now it still won't load an operating system but it gives me a new message: "No Bootable Device Available."

I'll play around with it more after work, but does anybody have further insight based on this new development?

---

### Post by oldfred on 2013-01-24
To see where you are at now.
Post a new link to a new BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by pattmayne on 2013-01-24
OK It's pretty much fixed now. This is how:

I ran boot-repair from a live usb of Ubuntu. Previously it didn't work because I was set to "legacy" mode. I kept speed-hitting f2 during the boot to get into the bios, changed the boot from Legacy to UEFI, kept secure boot OFF, then booted into liveUSB Ubuntu. Within live Ubuntu I installed and ran boot-repair. This included re-installing MBR on sdb2, but I don't know if that particular action was useful.

Then I rebooted and it went right into Windows 8! This is good! It's not a perfect fix yet because I want the GRUB2 menu to let me load any OS I have installed, but it has salvaged my computer from uselessness! Now I just have the remaining task of properly installing GRUB2. But that's a different problem which I'm sure I can find on the forums.

SO as I understand it, this was the problem: It was a double-problem: (1) I had GRUB2 installed on sdb7 but the other boot stuff was in sdb2. (2) I had the BIOS set to boot in Legacy mode instead of UEFI. Either was the computer was looking for boot-stuff in the wrong places. I still have work to do, but I'm no longer scared and nervous LoL.

Important Info for anyone with the same problem:

here is info about how to get boot-repair while running from a liveUSB:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Here is the file created by boot-repair when I fixed my bootup problems:
[http://paste.ubuntu.com/1568051/](http://paste.ubuntu.com/1568051/)

Thanks very much to everyone who contributed. Your knowledge will stay with me in my ongoing Linux dangerousness.

---

### Post by oldfred on 2013-01-25
You show ubuntu in the efi partition, so if you directly go into UEFI menu you now should have another boot option - ubuntu.

---

