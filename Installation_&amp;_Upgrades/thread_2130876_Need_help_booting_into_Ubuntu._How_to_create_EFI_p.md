---
title: "Need help booting into Ubuntu. How to create EFI partition; boot repair did not solve"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by Number703 on 2013-03-30
So I have been trying to create a dual-boot for Windows 8/Linux for a while now. Due to the laziness of HP, I am unable to disable UEFI or move the Legacy boot order above UEFI, so I need to install Linux in UEFI. I'm currently trying to install Ubuntu 13.04. I can boot from USB fine, go through the installation process fine, but it just goes straight to Windows every time. I install as "something else" (creating alongside Windows doesn't work either). I create a "swap" partition, and then I create an "ext4" partition with mount point '/'. Is there something else that I need to do, a /boot partition or anything?

[FONT=arial]I ran boot repair, which did not solve this issue. When I ran boot repair, I got the message "EFI detected. Please check the options." I don't really understand which options I am supposed to check, or what I am supposed to do with those options. After running boot repair, it said to "Make BIOS boot on sda2/EFI/ubuntu/grubx64.efi file." How do I do this? My BIOS didn't appear to have any new settings or anything added under boot order. The boot repair link I got was [http://paste.ubuntu.com/5656914/](http://paste.ubuntu.com/5656914/)

[/FONT]
[FONT=arial]In looking for solutions I came across this link: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
Do I need to manually create an EFI partition to install? Under "Creating an EFI partition" it gives these steps:
[COLOR=#333333][FONT=Ubuntu]An EFI partition can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:[/FONT][/COLOR]

[LIST=1]
[*=left][FONT=inherit]*Mount point:* /boot/efi (remark: no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically)[/FONT]
[*=left][FONT=inherit]*Size:* minimum 100Mib. 200MiB recommended.[/FONT]
[*=left][FONT=inherit]*Type:* FAT32[/FONT]
[/LIST]
[FONT=inherit]*   4. Other:* must be located at the start of a GPT disk, and must have a "boot" flag

The first step, Mount Point, I have no idea what it is talking about, but I am using manual partitioning (I think?) so I guess I don't need to do that.
The 4th point, Other, I don't understand. How do I locate at the start of GPT disk? How do I add a "boot" flag?

Thanks for any help.[/FONT]
[/FONT]

---

### Post by darkod on 2013-03-30
The EFI partition should already be there, so you don't need to create it. In the Drive Info section you can clearly see two EFI System Partitions. I think there should be only one, sda2.

When you installed ubuntu, did you boot the usb in uefi mode, or legacy mode? You need to boot it into uefi mode so that it installs into uefi mode.

The message to make BIOS boot on sda2/EFI/ubuntu/... means you need to go into bios and try to create a new entry in the EFI boot manager with that path. That will make it boot grub2 which then can give you menu to boot ubuntu or windows.

I don't use uefi so I can't say for sure where to find that, and also different brands make the bios options in a different way. Refer to your machine manual for more info, or google how to add new efi boot option and make it default.

It might be better to remove the boot flag from sda5, so that it doesn't show as second efi system partition. You should be able to do that with Gparted in live mode.

---

### Post by oldfred on 2013-03-30
You can use gparted to add boot flag. But in gpt partitioning all that does is flag that partition as the efi partition. The efi partition is where all system install boot loaders. You can only have one efi partition per drive.

 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

        HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

If you installed in BIOS/CSM/Legacy mode, not UEFI, Boot-Repair can convert your install to UEFI boot. It really is just uninstalling grub-pc (BIOS) and installing grub-efi(UEFI).

Many systems seem to only boot the Windows efi file. Boot-Repair also can rename files for those systems. It renames the Windows file and uses grub's shim which has the Microsoft secure boot key.

Do not run the secure boot rename if you can get it to boot without it.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by Number703 on 2013-04-02
So the "Backup and rename EFI files" thing didn't fix it.
I did find this: [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) which seems like it might fix the problem. I'm not really sure how to use it though and I'm cautious about tinkering around with BIOS stuff. Also, under "creating a new boot option" it says "[COLOR=#000000][FONT=arial]This assumes that [/FONT][/COLOR]*/boot/efi is your EFI System Partition, and is mounted at [I]/dev/sda1." *[/I]But my EFI partition is at /dev/sda2, not 1... sda1 is a Windows recovery. Will this make a difference?

Currently I'm actually having trouble getting Ubuntu up from the USB, it just goes to text only mode now for some reason... but assuming I'm able to solve that issue does anybody know anything about this efibootmgr?

---

### Post by oldfred on 2013-04-03
I think the efiBootmgr is usually built into many UEFI installs. You access some or many of the functions from your UEFI/BIOS menu. Only a few have very limited versions of UEFI that may not include it.

Did you remove boot flag from sda5?

If you have having video issues that is separate from boot issues. What video card/chip does your system have.
       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Number703 on 2013-04-04
Well, not sure what the problem was, but just downloaded the .iso again and re-made the USB, after a few tries of that I can get into Ubuntu from a LiveUSB again.

"Did you remove boot flag from sda5?"
I don't know how to do that...

I tried running the EFIbootmgr from terminal, efibootmgr -c (for creating a new boot option) yields "Could not open disk /dev/sda: Permission denied"  Any ideas what that's about? Secure Boot is disabled. Does it make a difference that this is just running from the USB (I formatted the disk and am in the process of reinstalling Ubuntu but need to go to bed now)? Also, again my efi partition is on /dev/sda2, not sda1 like the page says should be the case.


Alternatively, is this just an issue with trying to dual boot? I'm pretty much over Windows 8, would this be easier if I just uninstalled Windows and created a solo boot with Ubuntu or another distro? I can't tell if my problem is with the install itself, or if everything is installing fine but Windows 8 is just over-riding it.

---

### Post by darkod on 2013-04-04
For removing (or adding) flags, open Gparted from ubuntu live mode, right-click the wanted partition and select Manage Flags. That will allow you to remove the boot flag. Don't forget to hit the green button in Gparted to execute the change.

Yes, single boot will be much more easier than uefi dual boot. For single boot (or even dual boot if you have your win8 dvd), I would actually recommend installing in legacy mode and using legacy boot, not uefi. Simply go into bios, disable secure boot and disable uefi boot. Depending how the option is called it might be Legacy Only or similar.

After that boot ubuntu live mode and write new blank msdos table on the hdd. You can use Gparted for that.

After that install win8 (if you still want to).
Then install ubuntu.

That should be it.

---

### Post by Number703 on 2013-04-06
SUCCESS!!! I have the dual boot working. I'm not sure exactly what it was that did it, here's what I did:
Installed Ubuntu on it's own partition
Removed boot flag from sda5
Ran boot repair
Ran efibootmgr -c... I'm not sure if this did anything but I did it anyways.

So, yeah, thanks for all your help, this is awesome.

---

