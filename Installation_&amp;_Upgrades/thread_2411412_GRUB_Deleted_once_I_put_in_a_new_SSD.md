---
title: "GRUB Deleted once I put in a new SSD"
date: 2019-01-30
forum: Installation &amp; Upgrades
---

### Post by pikiaboy on 2019-01-30
SSD_1 was dual booted with Windows 10 and Ubuntu 18.04. 

Had a new SSD_2 and wanted to see what was on that installation of windows. Unplugged SSD_1 from my laptop, threw in SSD_2, and logged into windows. 

Took out SSD_2 and put back SSD_1 back in and now GRUB isn't popping up. 


Booted into a live usb and ran boot-repair. Crashed and hanged multiple times, so I got this paste from boot-info.

[http://paste.ubuntu.com/p/wtb6tXkmzn/](http://paste.ubuntu.com/p/wtb6tXkmzn/)

Any advice?

---

### Post by yancek on 2019-01-30
Not sure I understand what you're doing.  You indicate you have windows 10 and Ubuntu installed on one SSD, you dis-connected that SSD, put it a different SSD and booted windows?  What windows?  Is this another install of windows 10 or some other version of windows?  Your boot repair indicates the windows drive is in an unsafe state which means you left fastboot or hibernation on.  Needs to be off when you run boot repair or if you want to access a windows data partition from Linux.  

When you took out 'SSD2' and replaced 'SSD1' you indicate Grub does not appear.  What does happen?  Did you change the boot priority from the usb with the live system back to the SSD1 in the BIOS?

---

### Post by oldfred on 2019-01-30
When you physically remove or turn off a drive in UEFI, so not seen, UEFI forgets any boot entries for that drive.
Generally UEFI finds Windows entry, but not any others. You either have to use efibootmgr from Ubuntu live installer or reinstall grub to add Ubuntu entry back into UEFI boot menu.

You may just need to change boot order in UEFI.

Windows updates make Windows first in boot order, Ubuntu/grub updates may make Ubuntu first in UEFI boot order. So you have to manage which system you want first in boot order and if updates change order, manually change back. You can use efibootmgr or in UEFI change boot order.
See also:
man efibootmgr

---

### Post by pikiaboy on 2019-01-30
Hi, 

Thanks for responding. I've installed efiBootmgr and changed the boot order to boot ubuntu first. Now, when I restart my machine, I am shown the GNU GRUB screen, instead of the GUI GRUB that I am used too.

---

### Post by oldfred on 2019-01-30
Post this:
sudo efibootmgr -v

---

### Post by pikiaboy on 2019-01-31
Here is the output of sudo efibootmgr -v. 

BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0003,0001,0004
Boot0000* Windows Boot Manager    HD(2,GPT,33266b18-2107-4ad7-957f-1605dc618d0a,0xe1800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* UEFI: PC300 NVMe SK hynix 256GB, Partition 2    HD(2,GPT,33266b18-2107-4ad7-957f-1605dc618d0a,0xe1800,0x32000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0003* ubuntu    HD(2,GPT,33266b18-2107-4ad7-957f-1605dc618d0a,0xe1800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* UEFI:  USB Flash MemoryPMAP, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,MBR,0x1ad1e7,0x800,0x1d13340)..BO

---

### Post by oldfred on 2019-01-31
Both your Windows & UEFI: PC300 drive boot entries boot the Windows boot file, but the Ubuntu entry looks correct.
What brand/model system?

Did you run the Boot-Repair suggested fix, it looks like that would reinstall grub and may resolve any grub issues.

---

### Post by pikiaboy on 2019-01-31
I have the Dell XPS 15 9560. 

I ran Boot-repair for about 30 minutes. It just kept running and didn't change anything. Should I try rerunning it for longer?

---

### Post by oldfred on 2019-01-31
All Dell need UEFI updates & SSD firmware updates. Have you done that?
And drives must be set for AHCI.

And if you update UEFI, many settings will change back to defaults, so know what you have changed and check or redo them.

---

### Post by pikiaboy on 2019-01-31
All of my drives are set to AHCI. 
The laptop should already have UEFI updates and SSD firmware updates

---

### Post by pikiaboy on 2019-01-31
..

---

### Post by pikiaboy on 2019-01-31
Found my issue.

When I dropped down to the GNU Grub Shell, I tried to boot manually. 

I was following the steps from here: [https://askubuntu.com/questions/616811/gnu-grub-terminal-instead-of-ubuntu-login-screen](https://askubuntu.com/questions/616811/gnu-grub-terminal-instead-of-ubuntu-login-screen)

My issue was that because my XPS had an NVME drive, I had to set the root to /dev/nvme0n1p6. 

> 
set root=(hd0,1)
linux /boot/vmlinuz-WHATEVER-YOURS-IS root=/dev/nvme0n1p6 *NOTE: because I have an NVME drive, this is not /dev/sda1 or whatever partition you install is on.*
initrd /boot/initrd.img-3.13.0-29-generic
boot


Once booted, i just ran update-grub and everything went back to normal

---

