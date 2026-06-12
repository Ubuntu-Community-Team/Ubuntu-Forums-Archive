---
title: "Can't get into BIOS or boot into OS"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by dogbot2 on 2014-04-25
I recently installed Ubuntu 14.04. 
Windows 7 was installed on there first.
After changing the boot priority in the BIOS to my bootable ubuntu usb drive, ubuntu still wouldn't install, so I decided to enable UEFI mode and see if that would help.
That fixed the problem of Ubuntu not being able to install, but upon installing I am now not able to boot into either OS and I can't access the BIOS.
I installed Ubuntu with a "/" partition, a "/home" partition, and a swap partition.

When I try booting a message appears that says:
"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

I tried using the boot repair utility following the recommended repair instructions at:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And it didn't work. Here is the pastebin link for the result of that repair:
[http://paste.ubuntu.com/7325060/](http://paste.ubuntu.com/7325060/)

I understand that other people have posted things like this, so sorry if it's a repost.
Any help would be appreciated! And let me know if I didn't give enough info.
Thanks!

---

### Post by oldfred on 2014-04-25
I do not see anything wrong with install.
But if you turned on UEFI secure boot it will not boot as your install is BIOS for both Windows & Ubuntu.
You need to make sure UEFI is off, and BIOS/CSM is on in your UEFI/BIOS menu.

I do see grub both in sda2's PBR or partition boot sector and the MBR. You need the current verison of grub in the MBR. Grub in a PBR is not recommended and is not used as BIOS boots from MBR.

---

### Post by dogbot2 on 2014-04-28
Thanks for the reply! I ended up solving the problem.
Just pressed F2 during startup and got into my BIOS that way fortunately. Then I disabled UEFI

---

