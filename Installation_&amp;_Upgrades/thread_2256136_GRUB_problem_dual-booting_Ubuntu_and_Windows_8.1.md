---
title: "GRUB problem dual-booting Ubuntu and Windows 8.1"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2014-12-10
Lenovo U410 - 28GB SSD and 500GB HDD, Windows 8.1, UEFI, Secure bootand Intel Rapid Start enabled

When I install Ubuntu 14.04 as dual-boot, I can boot into Ubuntu from GRUB but the Windows option doesn't work. I've tried the Boot Repair tool from a live USB, but all that does is to add extra entries, none of which work.

I installed GRUB on the EFI partition so that shouldn't be  a problem.

I've gone into the BIOS, and set a Supervisor password, but it still won't let me edit the Secure Boot settings. (I had to do that on my Acer E3 in order to add Ubuntu to the secure boot database).

 

Has anyone managed to get the Windows option in GRUB to work on this particular machine and configuration?

If so, how did you manage it?

Thanks

---

### Post by oldfred on 2014-12-10
Grub often has issues with UltraBooks as the Intel SRT uses RAID. It used to not install at all, but now I think they have added the RAID drivers, but grub may not yet fully recognize that Intel SRT is a special case and not a RAID install.

Best to post link to summary report from Boot-Repair.

Did you install / to SSD or to hard drive? Some have done each with Intel SRT, but across many brands & models. The SRT implementation seems be be an Intel standard so the same.

---

### Post by Gordonbp531 on 2014-12-11
I installed onto the HDD and put the GRUB bootloader on dev/sdb2 which is the EFI partition.
Here's a link to what the GRUB menu looks like after using Boot repair:
[https://uk.owncube.com/public.php?service=files&t=5ac7d8ea662e9f2e0dd8263df64172dd]("https://uk.owncube.com/public.php?service=files&t=5ac7d8ea662e9f2e0dd8263df64172dd")
(the three entries below Advanced Options for Ubuntu have been created by Boot Repair)

here's a link to the error message when I click on the Windows option:
[https://uk.owncube.com/public.php?service=files&t=8fbabc79eea6491e4044a50eec1fc72d]("https://uk.owncube.com/public.php?service=files&t=8fbabc79eea6491e4044a50eec1fc72d")

And finally, here's a link to the Boot Repair report:
[http://paste.ubuntu.com/9466074/]("http://paste.ubuntu.com/9466074/")

---

### Post by oldfred on 2014-12-11
Did you turn off the always on hibernation in Windows or fast boot, and turn off the Intel Fast flash in UEFI?
Grub does not seem to boot Windows when hibernated.

Can you go into UEFI and direct boot the Windows entry, not from grub menu?

---

### Post by Gordonbp531 on 2014-12-11
> **oldfred said:**
> Did you turn off the always on hibernation in Windows or fast boot, and turn off the Intel Fast flash in UEFI?
Grub does not seem to boot Windows when hibernated.

No I didn't. Should i do  a re-install after turning those off? 
Would I be able to turn them back on after the install, or would I have to live without fast start?

> Can you go into UEFI and direct boot the Windows entry, not from grub menu?

yes, that works OK.....

---

### Post by oldfred on 2014-12-11
I think you can turn fast start back on, but then probably have to use one time boot key, often f10 or f12 or use UEFI boot menu to boot Windows. 
You should not have to reinstall, if both systems are working.
If hibernation or fast start in Windows is on, you have to be careful not to write into Windows NTFS partitions. Reading should be ok, but the hibernation resets everything to as when shutdown, so anything written into Windows disappears.

 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by Gordonbp531 on 2014-12-12
Having turned off Intel Rapid Start, and with Windows not hibernating, the Grub menu options for Windows still don't work - same error.

---

### Post by oldfred on 2014-12-12
Are you able to boot into Windows directly from UEFI boot menu or one time boot key?

Also if secure boot is on, grub does not boot Windows.

---

### Post by Gordonbp531 on 2014-12-12
Yes I can boot into Windows using the Boot menu.
The Windows Grub entry on my Acer works OK - and that machine has Secure Boot turned on.

---

### Post by oldfred on 2014-12-12
Good to know secure boot does work now to boot Windows from grub menu, there was a bug report, but I have not checked it lately. But perhaps not in all cases?

Not sure what else to suggest.

---

