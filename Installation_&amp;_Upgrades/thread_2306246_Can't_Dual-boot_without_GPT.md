---
title: "Can't Dual-boot without GPT?"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by vpiercy on 2015-12-13
I have a new system and can't get it to dual-boot. I have Win7 on an M.2 drive and Ubuntu on an HDD. Boot Repair says I need a GPT area on my drive (and Boot repair asks me if the Linux HDD is removable--it's 1000GB). I went to"[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")" page and I still don't know if the M.2 drive is causing the problem.  > [B]Windows 7 UEFI, or new self built system - no secure boot issues, new motherboards may now have Windows secure boot setting. Many call it "Windows" or "Other"
You should not have any of the secure boot issues, but still should use the newest versions of Ubuntu. They include many UEFI & grub install updates.
You still have gpt partitioning and should use Windows disk tools to shrink Windows if you have Windows.
If installing only Ubuntu (no Windows), see partitioning below. But you then can use either BIOS or UEFI, but probably should use gpt partitioning.[/B]I'm not dual-booting on the same drive so I shouldn't need to shrink Windows, right?

Is this section what I need to follow? The first link about the Samsung system doesn't seem to apply. 
> [B]Two Drive UEFI installs, Internal, external or flash drive
You must partition in advance including efi partition on second drive, then use Something Else to install.
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)[/B]


The second link mentions GPT on SSD drives and points to [this Arch page]("https://wiki.archlinux.org/index.php/Solid_State_Drives"), but that Arch page says nothing about GPT.

---

### Post by yancek on 2015-12-13
Windows 7 doesn't install UEFI by default so did you install it and select to use UEFI.  If you are using UEFI with windows, then you would need to install Ubuntu using UEFI also.  If you installed Ubuntu on a GPT system you need a small BIOS boot partition so the question is, are you using UEFI or not for both systems?

---

### Post by vpiercy on 2015-12-13
I must be using GPT b/c Boot Repair mentioned it. 

OTOH, how would I know? When I select which device to boot from in the BIOS (or whatever one calls the motherboard software now), some of the devices will have two entries, one plain and one prefaced with UEFI. 

Thanks for the response!

---

### Post by LostFarmer on 2015-12-13
If you are talking about program "boot-repair'', it gave you a web site to post for more help with useful information, where is it ?  if some other, download and run [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  , you can select  "Create bootinfo summory" option   Note: post the **Ubuntu pastebin link **

---

### Post by oldfred on 2015-12-13
With gpt partitioning, you need either the bios_grub flagged partition for BIOS or an ESP - efi system partition.
If Boot-Repair is asking for a bios_grub partition it is trying to install a BIOS boot loader to a gpt partitioned drive and you do not have a bios_grub.

Boot-Repair's auto-fix installs grub to all drives of in BIOS mode and if more than one drive best not to let Boot-Repair's auto fix run. Use only advanced mode and choose which operating system to install boot loader for and to which drive's MBR. Best to keep each system's boot loader on same drive as system, but in BIOS set Ubuntu/grub as default or first in boot order.

You can install Windows 7 in UEFI boot mode.
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.
And how you boot install media UEFI or BIOS is how it installs.

If you want Windows 7 in UEFI mode you have to copy DVD to flash drive and move the UEFI boot files into /EFI/Boot and rename to bootx64.efi. The bootx64.efi is a default boot for all UEFI devices. Originally just external, but now for any device.

---

### Post by sudodus on 2015-12-14
> **vpiercy said:**
> ...
OTOH, how would I know? ...

See this link: [Test if running in UEFI mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode)

---

### Post by oldfred on 2015-12-14
When you boot live installer you get two different screens, so you can tell which way you have selected to boot from UEFI/BIOS boot menu.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by vpiercy on 2015-12-14
LostFarmer--Boot Repair wasn't able to go online. All the Linux distros I try can use my Ethernet, hardwire, but not Boot Repair. :/  I think my motherboard might be too new and Boot Repair needs a network driver. I think I have the latest Boot Repair version (linked from the Ubuntu pages).

---

### Post by vpiercy on 2015-12-14
Nice link sudodus: 

> van@Ubuntu-15:~$ test -d /sys/firmware/efi && echo efi || echo bios
efi



---

### Post by vpiercy on 2015-12-14
oldfred, thank you for your very information rich posts. I'm afraid I'm a bit lost with them though. I'll keep studying those pages and that link in your second post. I am posting now from Ubuntu just because I hit F2 at boot and changed the boot device priority. A sloppy workaround to be sure. 

I've already installed Ubuntu 15.10 on its own 1T HDD and Windows 7 on an M.2 drive. I would hate to have to reinstall Windows 7 at this point. I could reinstall Ubuntu, though I'm already making myself at home with this installation. 

Using sudodus's link above, I determined that Ubuntu is loading in EFI. I'm guessing Windows isn't. Boot Repair certainly seems flummoxed by this set-up. I'll try to post my boot information from Boot Repair. I have to understand the GPT stuff better. I know it's designed to replace use of an MBR, and that it's more robust, more redundant, but I don't get how to write it to disk with the correct boot information. I always relied on Boot Repair to do that sort of thing. 

Thank you!

P.S. My BootInfo. (It's a photo b/c Boot Repair doesn't recognize my network device!) In the boot info I see my Ubuntu drive (the 1T HDD) and the Boot Repair USB drive (8GB), but I don't see the M.2 drive with Windows 7. I don't think Boot Repair can see it. 

[http://i.imgur.com/TTneSsq.jpg](http://i.imgur.com/TTneSsq.jpg)

[IMG]http://i.imgur.com/TTneSsq.jpg[/IMG]

---

### Post by oldfred on 2015-12-14
If Windows is the older BIOS/MBR, it is easier to dual boot if Ubuntu is in BIOS boot mode. Ubuntu can boot in either BIOS or UEFI from gpt. And Boot-Repair can convert from UEFI to BIOS if you first add a tiny 1 or 2 unformatted partition with the bios_grub flag.

I now only use gpt partitioning, and have since installing 10.10. About 2012, my new gpt drives got both an ESP - efi system partition (for future use then) and the bios_grub partition. My new UEFI system still has both gpt partitions, but now I do not use the bios_grub unless booting my old system.

Some users do keep Windows in BIOS and Ubuntu in UEFI and just use one time boot key to choose. UEFI/BIOS choice must be made at start of boot. Or from grub menu you can only boot other systems in same, UEFI or BIOS, boot mode.

---

### Post by vpiercy on 2015-12-15
Thank you for the reply!

I went to this page (linked form the "UEFI Installing-Tips" page) on [DiskSpace]("https://help.ubuntu.com/community/DiskSpace"). 

So at this point I go into Gparted and create a small GPT partition [COLOR=#000000]with the bios_grub fla[/COLOR][COLOR=#000000]g [/COLOR]on each drive at the beginning of the drive. Won't this destroy my Windows 7 installation? Sounds very risky. I have a backup, but I'm not exceedingly confident about Windows restoring properly.

Wait. I just need to change the Ubuntu drive, correct?

---

### Post by sudodus on 2015-12-15
You need the partition with the bios_grub flag only on the drive you are booting from.

---

