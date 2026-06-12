---
title: "Fresh install of Ubuntu on separate HDD disk, got error /boot/grub/i386-pc/normal.mod"
date: 2020-10-11
forum: Installation &amp; Upgrades
---

### Post by hotka on 2020-10-11
So I used a live USB to install Ubuntu 20.04 on my HDD and all was well, so it seemed, until I tried to boot from the HDD. got the error /boot/grub/i386-pc/normal.mod not found message. I am dual booting with Win 10 but on a separate external HDD. As far as I am aware I have a legacy BIOS. I tried to use grub rescue, to no avail. I then used Boot Rescue, which failed also. Here is the URL [https://paste.ubuntu.com/p/N8h8wPYGj4/](https://paste.ubuntu.com/p/N8h8wPYGj4/)

Edit: turned off hibernation in windows 10, still doesn't work [https://paste.ubuntu.com/p/V7Q3fwFNMf/](https://paste.ubuntu.com/p/V7Q3fwFNMf/)

---

### Post by oldfred on 2020-10-11
It looks like you originally installed in UEFI boot mode to sdc.
Your sdc has an ESP sdc1 and a comment in fstab on that being the original efi partition.

Best not to mix UEFI & BIOS on same system.
But also best if newer UEFI hardware to have all systems as UEFI with gpt partitioning.
Microsoft has required vendors to install Windows in UEFI/gpt mode since Windows 8 released in 2012.

Since you can install Ubuntu in either UEFI mode (with ESP) or in BIOS boot mode (with bios_grub partition) to gpt partitioned drives, better to use gpt partitioning, if only for future compatibility. I started converting drives in 2010.

It looks like you booted Boot Repair in BIOS mode and it installed a BIOS grub boot loader to MBR of sdc and a Windows type boot loader to MBR of sda to boot Windows.
You have to in UEFI boot menu choose to boot external drive in BIOS mode, not UEFI mode.

Normal not found is typical of tying to boot in wrong mode. So you may be booting in UEFI mode. UEFI typically has ubuntu entry. BIOS will be a drive entry.

---

### Post by hotka on 2020-10-12
Apologies, I am not particularly tech-savvy, so I have a few questions just to clarify things.

1. I checked windows system information which said BIOS mode Legacy and I checked my BIOS and could not find 'Secure Boot'. This, to my understanding, means I have BIOS and not UEFI. Am I correct? Is there a way of knowing for sure?

2. Assuming I have a BIOS only system (It's a HP pre-built from 2010 that only updated to win 10 recently), why did Ubuntu install to my HDD in UEFI mode? 

The live USB i had used to install was in BIOS mode (as it had the purple screen with the keyboard at the bottom upon booting) and based on the fact you said that I booted Boot Repair in BIOS mode further supports this, as I booted Boot Repair from said live USB

3. Assuming I have a BIOS only system, then I don't have a UEFI boot menu. When I first installed from the live USB there was no two options for booting the usb, only one. Same with trying to boot now from the HDD. 

4. You said that BIOS has a 'drive entry' whereas UEFI has a ubuntu entry. All I see in the boot menu is a drive entry.

What am I supposed to do? I am stumped, I do not have much technical knowledge and so I do not even know where to start :/

---

### Post by oldfred on 2020-10-12
Some vendors started adding UEFI as the replacement to BIOS (but still called it BIOS) before Windows 8 in 2012. Even some Windows 7 systems (Which do not support UEFI Secure Boot) were installed in UEFI mode.

Not sure then how you got ESP & UEFI install on sdc? Ubuntu could not have installed in UEFI mode unless system has UEFI.
How you boot install media, UEFI or BIOS is then how it installs.

Boot-Repair looked like it has correct Windows boot loader in Windows drive. Does that drive selection in BIOS boot menu work?
And it looks like grub reinstalled in BIOS mode to sdc. Does that now boot?
Or what errors are you getting?

Windows only installs in BIOS mode to MBR(msdos) and only in UEFI to gpt partitioned drives. So partitioning of Windows drive will also show whether UEFI or BIOS.
Ubuntu can install in either boot mode to either partitioning, but probably should not.

I still suggest gpt partitioning. The only place now to use MBR, is for any drive that is Windows in BIOS mode. BIOS Windows will read data partitions on gpt drives.

---

### Post by hotka on 2020-10-12
Windows boots just fine, still getting that same /boot/grub/i386-pc/normal.mod not found message when booting from sdc
[h=2][/h]

---

### Post by oldfred on 2020-10-12
While grub is supposed to use UUID, sometimes the drive enumerated by BIOS confuses things. The boot drive will also be hd0, but when reinstalling it may be hd2 or hd3.

If you type exit, does it then boot?
Are you getting 
grub>
or
grub rescue?

Or try manual boot. Assumes boot drive is hd0.
configfile (hd0,5)/boot/grub/grub.cfg

or:

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod normal
(If that fails try:  insmod (hd0,5)/boot/grub/normal.mod)
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
#after boot
sudo update-grub

---

### Post by slickymaster on 2020-10-12
*Thread moved to **Installation & Upgrades**.*

---

### Post by hotka on 2020-10-12
I am getting grub rescue

i think the boot drive is hd0. i did ls (hd0,5) and got back filesystem is ext2.

insmod normal after set prefix and set root just gives back the same /boot/grub/i386-pc/normal.mod not found message
 
everything after that that you told me to do gave back either a 'not found' message or a 'unknown command' message

---

### Post by oldfred on 2020-10-12
Normal should be in your sdc5 partition.
But may be different between a UEFI & BIOS install.

I might use Boot-Repair again and use advanced mode to totally reinstall grub & include new kernel when in BIOS mode.

---

### Post by hotka on 2020-10-12
[https://paste.ubuntu.com/p/qZm9rnGtmf/](https://paste.ubuntu.com/p/qZm9rnGtmf/)

I'm not sure it worked properly, one of the pop ups in the terminal that the boot repair said would pop up didn't actually pop up

---

### Post by oldfred on 2020-10-12
It mentions nVidia.
If the uninstall of the kernel also removed nVidia, you probably have to manually reinstall it.
And may need nomodeset boot parameter to get into system.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

