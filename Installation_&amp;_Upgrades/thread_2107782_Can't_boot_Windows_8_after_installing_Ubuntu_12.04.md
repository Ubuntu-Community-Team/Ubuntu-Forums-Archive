---
title: "Can't boot Windows 8 after installing Ubuntu 12.04 alongside"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by MattPalmer on 2013-01-22
Hi,
 
I tried to install Ubuntu 12.10 alongside an existing installation of Windows 8, UEFI using secure boot.  

I shrank the main windows partition from Windows 8 to make room for Ubuntu, and in the BIOS changed the boot order to allow booting from a USB drive containing Ubuntu 12.10.

All seemed fine during install, but then the machine wouldn't boot Ubuntu, getting a access denied error on startup.  Windows 8 would then boot.

I booted into the Try Ubuntu from the usb stick again, and ran boot-repair, using the recommended fix.  

[http://paste.ubuntu.com/1560899/](http://paste.ubuntu.com/1560899/)

After this, nothing at all would boot from the hard drive, getting access denied errors twice, rather than once as before.  So I ran boot repair again, and selected the "Secure Boot" option.  It asked me to run various commands from a terminal, which I did.

Now the computer boots to Grub screen fine (no access denied errors), and will run Ubuntu.  However, Windows 8 no longer boots at all. 

[http://paste.ubuntu.com/1560942/](http://paste.ubuntu.com/1560942/)

How can I restore Windows 8 to booting, preferably with Ubuntu as well - but I can live without Ubuntu for a while - I need Windows 8 for work purposes.


Thanks for any advice,

Matt.

---

### Post by MattPalmer on 2013-01-22
OK - disabling Secure Boot in the BIOS allows Windows 8 to boot up. 

Is there any way of getting this to work while preserving Secure Boot too?

---

### Post by oldfred on 2013-01-22
Some UEFI have hard coded the UEFI boot to the Windows boot file. That really is a bug in the UEFI implementation as users are supposed to be able to turn secure boot off and use other secure boot signatures to boot. 
Ubuntu uses the same signature as Windows and that is in the shim file. The work around Boot-Repair does is to rename the shim to bootmgrw.efi and then the UEFI will boot to grub and grub chain loads back to the renamed bootmgrw.efi backup file.
Some have reported no issues with secure boot on or off and booting. Others have issues.

What computer and UEFI/BIOS do you have and is UEFI/BIOS up to date?

---

### Post by MattPalmer on 2013-01-24
Hi,

my PC is a Samsung laptop, model number NP3530EC-A0DDX.  The BIOS is a Phoenix Secure Core Tiano.  The BIOS version is P04RAP, and the MIOM versions (whatever that is) is also P04RAP.

The GRUB menu contains various windows 8 and windows 8 recovery start options, none of which work if SecureBoot is enabled in the BIOS.  If I select the "Windows UEFI bkpbootmgfw.efi" option, I get an error like:

/EndEntire file path: ACPI (a0341d0,0)/PCI(2, 1f) UnknownMessaging...

(Sorry, took too long to write the whole thing down - I will if it's useful).  The Grub menu item contained:

Set params "Windows UEFI bkpbootmgfw.efi"
search --fs-uuid --no-floppy --set=root 1E5C-64A3
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi

Does this help anyone...?  I can write down the lot if it will help, but I'd rather not if it won't!

Thanks,

Matt.

---

### Post by MattPalmer on 2013-01-24
A little more info.  The actual error message on not being able to boot Windows 8 in SecureBoot ends with "Can't load image".

I've looked in the EFI partition, and there is a path /EFI/Microsoft/Boot

there are also files:

bootmgfw.efi
bootx64.efi
bootmgfw.efi.grb
bootx64.efi.grb
memtest.efi

However, there is no bkpbootmgfw.efi file.

---

### Post by oldfred on 2013-01-24
Your pastebin link showed this, did it get deleted?

/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by MattPalmer on 2013-01-26
Hmmm....very strange.  The pastebin link does indeed show the file being there.  But it isn't there when I look at the EFI boot partition, mounted from Ubuntu.

So I guess it was either deleted (not by me!), or it was never there and the pastbin output is wrong in some way (don't know how it's generated -  I assume it's a file listing, so was originally there).

Is there any way of regenerating the bkpbootmgfw.efi from the bootmgfw.efi files?

---

### Post by oldfred on 2013-01-26
Backup entire efi partition. Boot script only shows some of it but it still is not large.

Then rerun Boot-Repair and post new BootInfo report. You may need to go into advanced options and use the rename files option.
       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

---

