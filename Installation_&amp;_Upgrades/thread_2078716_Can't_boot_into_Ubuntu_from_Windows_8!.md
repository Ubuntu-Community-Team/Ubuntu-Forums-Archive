---
title: "Can't boot into Ubuntu from Windows 8!"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by pwert00 on 2012-10-31
Hi all,

I recently bought an *HP Pavilion g6* with Windows 8 and decided that I wanted to also have Ubuntu on my system.  I made the bootable usb with Ubuntu 12.10 using the directions on the Ubuntu website, and after installation it asked me to restart my computer.  After restarting my computer, my computer will automatically boot into Windows 8 and it does not recognize that there is another operating system to boot into.  The partition is there, but it won't give me an option to boot into Ubuntu as if Windows 8 is the only operating system on the computer.  

How can I boot into Ubuntu?  Is there some settings I need to enable in Windows 8?  Do I need to reinstall?  

Thanks!

Paul

---

### Post by YannBuntu on 2012-10-31
Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") --> Recommended Repair, and indicate the URL that will appear.

---

### Post by pwert00 on 2012-11-01
Okay, I ran boot repair.  I am restarting now to see if it worked.  I got this message:

"
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1325004/](http://paste.ubuntu.com/1325004/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

The boot files of [Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
"

---

### Post by oldfred on 2012-11-01
After Boot-Repair can you go into UEFI/BIOS and select ubuntu to boot? You should have choices for both Windows & ubuntu.

Adding boot menu entry for EFI firmware configuration

Above also says boot repair added the correct Windows chain load entry. Grub2's os-prober adds a BIOS type chain load entry when it should add an efi type entry. Boot-Repair adds the correct one, but you may have several now?

---

### Post by pwert00 on 2012-11-05
Is there a way to boot into ubuntu without the USB drive?  I don't have access to a usb drive yet which is why I haven't yet tried the boot-repair.

---

### Post by oldfred on 2012-11-05
How did you install, or is this really a wubi install from inside Windows?

I thought you ran boot repair above?

Most use USB flash drives, they have become a lot lower in cost recently.

---

