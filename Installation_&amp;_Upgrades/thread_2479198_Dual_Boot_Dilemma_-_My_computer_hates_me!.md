---
title: "Dual Boot Dilemma - My computer hates me!"
date: 2022-09-17
forum: Installation &amp; Upgrades
---

### Post by drumone on 2022-09-17
[SIZE=3]I have a custom built dual-boot PC ( see specs below). I have been having major issues with Windows recently. Therefore, I reinstalled the Windows OS, hoping it would solve the problems. Not surprisingly, it didn't! Long story short, I have reinstalled both Ubuntu and Windows multiple times. This last time I swapped the drives, meaning the OS on drive 0 is now on drive 1 and vice versa. Ubuntu seems fine. I don't know about Windows for sure yet because when I changed the boot order in the UEFI BIOS I no longer have the GRUB menu options of choosing my OS. Before I do something I'll regret, could someone look at my paste bin and tell me what I should do to resolve this? You can find the info here: [https://paste.ubuntu.com/p/fMTPqRsmMx/](https://paste.ubuntu.com/p/fMTPqRsmMx/)[/SIZE][SIZE=3]. I greatly appreciate all the help I can get! Thank you![/SIZE]

  	 	 	 	  [LEFT] Asus ROG Crosshair VIII Dark Hero AMD X570 ATX motherboard[/LEFT] [LEFT] AMD Ryzen 9 5950x processor[/LEFT] [LEFT] Fractal Lumen S24 CPU liquid cooler[/LEFT] [LEFT] Asus Dual-RX6600 GPU[/LEFT] [LEFT] G.Skil RipJaws V 64GB RAM[/LEFT] [LEFT] Samsung 980 Pro SSD – 1TB NVMe - Ubuntu
[/LEFT] [LEFT] Samsung 980 Pro SSD – 1TB NVMe - Windows[/LEFT] [LEFT] Corsair RM850x power supply[/LEFT] [LEFT] Fractal Define R5 ATX Midtower case[/LEFT] [LEFT] Fractal Dynamic X2 GP-14 140mm case fan – 2 in the front, 1 in the rear[/LEFT]

---

### Post by TheFu on 2022-09-17
If you don't tell us what the specific issue is, we don't know where to look.

If it is just a boot thing, then change the boot device in the BIOS.  By swapping the NVMe, you hid the EFI boot that the BIOS expected.  Put them back.  While we can swap the non-boot drives around and thanks to UUIDs or LABELs in the fstab file, it usually doesn't matter to Linux, the hardware + BIOS has settings where it seeks out the UEFI/EFI fat32 partition, assuming legacy BIOS booting isn't being used.  

With UEFI, there's only 1 EFI fat32 partition for a computer and it needs to be where the BIOS expects it.

---

### Post by drumone on 2022-09-17
My apologies! Reading it again I see that I was as clear as mud. 

The problem is that I don't have the GRUB menu that allows me to choose the OS when I boot. I've always had the Ubuntu drive boot first in the UEFI boot order list. At this point, the BIOS sees both drives (Ubuntu - 1, Windows - 2), but it only boots into Ubuntu without giving me the option of my other OS. I need to have access to both.

I'm working on a degree in software development and I'm required to use Microsoft Visual Studio for my current class. Hence my need to use Windows. I prefer Ubuntu, but the university only supports Windows and Mac.

---

### Post by TheFu on 2022-09-17
Well, if you are doing CS, you should learn and use virtual machines.  Multi-boot systems is asking for problems.  Virtual machines keep each separate and means having a hardware-agnostic VM can be restored to almost any other system, so when it is time for new system in a few years, moving the VMs without any real changes noticed, except massively better performance, is like copying a file and setting about 20 VM config things. That's it.

If you mix MSFT with any other OS, you'll find that MSFT screws up the booting about once a year. Of course, it never happens when it is convenient.  It waits until the most critical period, then every OS except the main MSFT one won't boot.  VMs remove that issue.

I've had Windows inside a VM for decades now, but it wasn't until 2008 that I finally made Linux the VM host system for a number of reasons.  Properly tuned VMs provide 90% of the native performance that running on the actual hardware provides, except when it comes to GPU-intensive stuff.  For "productivity" things, like coding, or making documents, it doesn't matter.  FPS gaming and video editing is where running directly on the hardware matters, but for everything else, a VM works well with 100x more flexibility.

VMs can still have boot issues, but those are limited to that single VM, not everything on the computer. VMs isolate the OS from any others on the same system.  That's very convenient.  Also, VMs provide virtual hardware, so the actual hardware in the system isn't seen by the VM-guest.  That means never having to hunt down odd drivers for guest machines.  

Well, I've said my 20 cents.  Take the advice or leave it.  Consider yourself warned.

---

### Post by drumone on 2022-09-17
Thanks for your thoughts TheFu. I'll give virtual machines some thought and research in the future. How are VMs for music production? I'm a musician and I write and arrange music using Sibelius, Virtual Drumline, Guitar Rig 5, and other software. I also hope to get into recording with this system, in the future. Seeing as how these programs are very heavy RAM/ CPU users I'm wondering how a VM would perform?

For right now, however, I would just like to get the GRUB menu back so I can select my OS. I am safe to run the boot-repair and let it do whatever it suggests?

---

### Post by oldfred on 2022-09-17
You have UEFI boot, with both systems using ESP on nvme0's ESP - efi system partition.
See line 78, that show GUID or partUUID of ESP used to boot.

You show mount of ESP in fstab, so Ubuntu set to boot in UEFI mode.
But you have BIOS boot loader grub in MBR & Windows in other MBR.
Windows can only boot in UEFI mode from gpt drives, so a Windows BIOS boot loader should not be on a UEFI boot system.
Ubuntu can be reconfigured to boot in either UEFI or BIOS by reinstall of grub to either gpt or MBR(msdos) drives, but since Windows is UEFI, Ubuntu must be UEFI to dual boot from grub. And the only time to use MBR, is for a BIOS install of Windows on a system over 10 years old that does not have UEFI.

Make sure you have UEFI setting for UEFI boot only. 

Grub only boots working Windows. And Windows updates turn fast start up back on preventing grub from booting it.
Since UEFI, you should be able to directly boot Windows in UEFI mode from UEFI menu. Check manual for your motherboard often f12, f10 or similar for UEFI boot menu. Often f2 or del is for UEFI settings.

If you cannot directly boot Windows that is a Windows issue that cannot be resolved from Ubuntu. Sometimes you have to use f8 or directly try to boot Windows several times for it to go into a repair mode.
If that does not work, you then need your Windows repair flash drive.

---

### Post by drumone on 2022-09-17
I ran boot-repair from a live USB. I let it do the recommended repair and it reinstalled GRUB and whatever else needed. I now have my choice of OS back again. Problem solved! 

Thanks to everyone who took the time to post their thoughts, code, and suggestions! I greatly appreciate your help!

---

