---
title: "Problem with double boot Ubuntu +W10 after W10 update"
date: 2018-09-15
forum: Installation &amp; Upgrades
---

### Post by anmaru on 2018-09-15
I have in my laptop two operating systems: Windows 10 and xubuntu.
One day, after turning off my laptop from Windows 10 , it started to update. I let the updates finish, and the next time I wanted to turn it on using windows 10 I got the following error: 
"error: file <</EFI/Microsoft/Boot/bootmgtw.efi>> not found.Press any key to continue"

Then, I tried to repair the boot system from a usb with xubuntu  that I created using the program Rufus so it would boot in UEFI mode (I tried it before by burning it with Ubuntu disk utility) I installed boot-repair and run it and I got this error:

"GPT detected. Please create a Bios-Boot partition (>1MB,unformatted filesystem,bios_grub flag)This can be performed via tools such as Gparted. Then try again. Alternatively, you can retry after activating the [Separate/boot/efi partition:] option."

This is the analysis I got from boot repair [http://paste.ubuntu.com/p/d2wJsHR6QY/](http://paste.ubuntu.com/p/d2wJsHR6QY/)

Could you help me please:(?

---

### Post by yancek on 2018-09-15
Take a look at the link below to the microsoft site.  You should have this file at this location for windows:  \EFI\Microsoft\Boot\bootmgfw.efi
It almost always shows in the boot repair output but does not show in yours.  You might try booting Xubuntu and mounting sda1, the EFI partition and look at that location to see if the file is actually there.  I'm guessing you had a couple of typos in your original post regarding the error message??s

[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcd-system-store-settings-for-uefi](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcd-system-store-settings-for-uefi)


I'm not sure why you are getting the GPT detected and being told to create a BIOS boot partition.  You should not need that with an EFI/GPT install unless you booted the Xubuntu usb in Legacy mode rather than EFI.  Some computers will have an option in the Boot options section of the BIOS to boot from an EFI file.  You might look for that rather than trying to use Grub to boot.

---

