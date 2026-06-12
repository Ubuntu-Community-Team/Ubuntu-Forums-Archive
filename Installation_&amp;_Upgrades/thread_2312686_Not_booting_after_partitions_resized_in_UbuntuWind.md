---
title: "Not booting after partitions resized in Ubuntu/Windows 10 dual boot setup"
date: 2016-02-06
forum: Installation &amp; Upgrades
---

### Post by random20201129 on 2016-02-06
I had a working dual boot of Windows 7 and Ubuntu 15.10 using EasyBCD as the primary boot loader when I unfortunately decided to resize the Windows 7 C:\ partition (and reduce the size of the NTFS D:\ shared between Windows & Linux). I also decided to upgrade from Windows 7 to 10 at the same time.

I used the live CD Boot-Repair several times trying to get things to work and on the 2nd last run I restored the MBR to make EasyBCD the boot loader.
[http://paste.ubuntu.com/14902140/](http://paste.ubuntu.com/14902140/)
This gave me a working EasyBCD boot menu from where I could start Windows 10 fine, but after re-adding Ubuntu using EasyBCD 2.3 Ubuntu in Windows 10 Ubuntu wouldn't boot and gave this text dump immediately after selecting it from the boot menu.
Try (hd0,0): NTFS5: No ang2
Try (hd0,1): NTFS: No ang2
Try (hd0,2): NTFS: No ang2
Try (hd0,3): Extended
Try (hd0,4): non-MS: skip
Try (hd0,5): Extended
Try (hd0,5): EXT2:

So then I thought grub must need fixing so on my last run of the live CD Boot-Repair I reinstalled grub2 to my linux partition (/dev/sda6) and set the option to uninstall any existing grub.
[http://paste.ubuntu.com/14903832/](http://paste.ubuntu.com/14903832/)
This resulted in no working boot menu of any kind and the machine just keeps rebooting continuously until I turn it off manually.

Any ideas on how to get my Windows 10/Ubuntu 15.10 dual boot working?

I'm don't mind dumping EasyBCD but haven't been able to do this either

---

### Post by oldfred on 2016-02-06
EasyBCDl uses the very old grub4dos to chainload to another copy to grub to boot.
But newer grub2 is larger and does not fit well inside a PBR or partition boot sector. It has to convert to blocklists or hard coded addresses. Grub normally complains that system is not reliable using blocklists.

Did you turn off fast startup in Windows? That is always on hibernation, which prevents grub from booting it.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

With BIOS you have to have either grub2 or Windows boot loader in MBR.
Grub should work, if fast start/hibernation is off.

Otherwise you may want to see why EasyBCD is not working. But only a few that are primarily Windows users use EasyBCD.

 [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by random20201129 on 2016-02-06
Thanks oldfred. I'm happy to dump EasyBCD and not using Windows much so am happy to turn off it's fast start and hibernation if grub2 doesn't support it. But so far all my attempts to install grub2 as the master boot loader have failed, for reasons unknown. What do I need to do to achieve this? And should I install it into /dev/sda1 where EasyBCD is currently or /dev/sdb6 where Ubuntu is? Also, I'm not sure if it's normal, but sometimes when I boot into the Boot Repair live CD my HDD is /dev/sda and sometimes /dev/sdb (and the USB stick is the other /dev/sd{a,b} partition). Could this be a problem?

---

### Post by oldfred on 2016-02-07
You never every install grub to a NTFS partition. That breaks Windows. 

And normally you do not install grub to a partition like sda1 or sda6, just to MBR like sda. 
It is only EasyBCD that forces you to install to a partition PBR.

The MBR is sda which is first sector of hard drive. BIOS only jumps to that first sector to start boot process.

You need to keep track of which drive is your hard drive and which is flash drive. Some systems promote flash drive to sda, and then you must install grub to sdb, otherwise you break the flash drive as it then has grub, but needs syslinux boot loader.

My old BIOS system always saw first drive as sda or hd0 in grub. But I had several drives and flash drive would be sdf if plugged in when system was running, but sdb when rebooted. And then every other drive changed. It turned out I had used SATA0, but skipped SATA1, so flash drive would get into boot order somehow as second drive.

---

### Post by random20201129 on 2016-02-07
Thanks again Oldfred... I've made several more Boot-Repair attempts and getting more experienced as well as taking notes, and even made a backup of the whole drive just in case (I had my data backed up but not the 2 OSes before).

 When the Boot-Repair live system loads it seems to randomly assign the live USB and HDD as /dev/sd{a,b}. Perhaps it depends on when I insert the USB stick, before or after a cold start. As you state have learnt that I can't install grub into an NTFS partition (I thought Boot-Repair would reformat it but it doesn't even offer the option to install it to /dev/sda1), but only offers /dev/sda or /dev/sda6 as options.

Here's a summary of my last 2 runs (where the HDD was /dev/sda):
# 1. Restore MBR via Boot-Repair
Ran Boot-Repair with options to restore the MBR to /dev/sda (generic MBR) with the MBR to boot /dev/sda6 (Ubuntu 15.10).
Post repair Boot-Info is at [http://paste.ubuntu.com/14955402/](http://paste.ubuntu.com/14955402/)
After rebooting the screen flashes up some error message that I can't read as it disappears too quickly (but something like "Can't load ... FILENAME" where FILENAME might have had the word forced in it) and then the GRUB boot menu loads but only shows the Boot-Repair Live USB as an option to boot. Obviously can't boot my Ubuntu so it seemed that grub needed to be reinstalled in my Ubuntu to get it onto the boot menu.
# 2. Reinstall GRUB via Boot-Repair
Ran Boot-Repapair with options to install GRUB into /dev/sda and boot /dev/sda6 (Ubuntu 15.1) by default with a prior GRUB purge and the boot flag set to /dev/sda2 (Windows 10) as I read that GRUB doesn't use the boot flag, just Windows - that correct?
Post repair Boot-Info is at [http://paste.ubuntu.com/14955492/](http://paste.ubuntu.com/14955492/)
After rebooting I just get a blank screen after the BIOS finisheds loading and then the machine restarts, and this repeats until I power the machine down.


I'm feeling that I should rerun step 1. and then try booting from the GRUB rescue menu and then assuming I can boot into my Ubuntu then re-install GRUB from there - something along the lines of what's in [https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)

Would you recommend trying this or something else?

---

### Post by oldfred on 2016-02-07
Installing to the partition sda6 may be confusing things. Best just to install to MBR or sda.

This may be confusing Windows in sda2. Linux is case sensitive, so sees two BCDs, but Windows is not case sensitive and does not allow two identical named files or folders (even though case is different).
/boot/bcd /boot/BCD 

[FONT=arial]You are showing BIOS installs, but Booted Boot-Repair in UEFI mode.
> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
Do not mix UEFI & BIOS as that causes major issues. They are not compatible.
[/FONT]
It does look like you reinstalled grub-pc correctly to MBR.

Grub does not use Boot flag, but Windows must have it on primary NTFS partition with boot files.

Have you changed UEFI/BIOS to boot in UEFI mode?
That would give error messages as it cannot find /EFI/Boot or ESP - efi system partition.

You need to make sure hard drive is AHCI, not RAID nor IDE.
And you need to have CSM/Legacy/BIOS boot on.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

