---
title: "After installing Ubuntu 13.04, Windows 8 doesn't work"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by radeusgd on 2013-07-12
Hello!
So, after I installed 13.04, my Win8 doesn't work.
While booting I get:
> b&#322;&#261;d: nie mo&#380;na odnale&#378;&#263; polecenia "drivemap"
b&#322;&#261;d: invalid EFI file
Translation:
> error: cannot find command "drivemap"
error: invalid EFI file
That's when I enabled Legacy support, when it was disabled I got same thing but there were also warning that some modules "ntfs" something something could not be loaded.
It was an EFI installation and disabling SecureBoot was impossible in my BIOS(locked?).
Here's log from boot-repair: [http://paste.ubuntu.com/5868366/](http://paste.ubuntu.com/5868366/)
It could be problematic that I forgot to do the clean shutdown on Win8.
Please help me because I need Windows on this laptop too (laptop is Lenovo z580 if it helps).
Thank you in advance.

---

### Post by oldfred on 2013-07-12
You have installed the full signed kernels and should be able to boot with secure boot on. Many systems are modified from UEFI standard to only boot Windows, so Boot-Repair renames Windows file and you boot Windows from grub menu. But in UEFI menu you have to boot with UEFI and boot the Windows entry (which really is grub2's shim file with the Microsoft signing key).

This is the entry in grub menu you should use to boot Windows. It looks like you system (or Boot-Repair cannot tell) does not identify recovery or main install correctly. But /dev/sda2        E8E6-2E23 is your efi partition that UEFI must boot from.
 menuentry "[COLOR=#b22222]Windows UEFI recovery bkpbootmgfw.efi[/COLOR]" {
search --fs-uuid --no-floppy --set=root E8E6-2E23
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

      
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

It looks like your system has another recovery partition with efi boot files that is just for recovery but Boot-Repair finds those as boot entries and grub2's os-prober has a bug and only adds BIOS entries that will never work. If you want to clean up menus, there are more instructions in link in my signature below.

Another Lenovo

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

Microsoft requires vendors to let users turn off secure boot, but do not specify if Windows then must still work. Your system has to have a way to turn secure boot off, but then Windows may not boot. Some boot with secure boot off, others do not.

---

### Post by radeusgd on 2013-07-12
Oh man, thank you very much. VERY MUCH.
You're great :)
I used the added the menu entry you listed, removed others not needed and after 2 restarts and some Windwos autorepair it worked!
Now I have 1 additional(not working) entry by os-probe(but it's not a problem) and the correct entries and both Windows and Ubuntu boot properly.
Thank you.
Edit: Ubuntu sometimes goes black screen and hangs on boot but it happens less than 50% of the times I run it and after restart it boots up correctly so maybe it's a bit inconvenient it still works and I think that it may repair itself by updgrading packages etc.

---

### Post by oldfred on 2013-07-12
Is this an UltraBook or one with dual video. Or is it booting with Intel video sometimes and nVidia sometimes? The drivers are different.
But the very newest nVidia driver has just started to support dual video, but you may need the kernel that is in the next version of Ubuntu to have video work with that nVidia driver.
Most with dual video seem to use Bumblebee, some links again in thread in my signature, but that is all I really know about bumblebee.

---

