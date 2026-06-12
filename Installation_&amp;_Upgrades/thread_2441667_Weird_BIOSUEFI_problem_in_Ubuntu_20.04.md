---
title: "Weird BIOS/UEFI problem in Ubuntu 20.04"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by rei-nert on 2020-04-25
I created a live-USB of Ubuntu 20.04 official release, then using the boot option, there was a BIOS USB and a UEFI USB. I chose UEFI USB and installed the new Ubuntu, with and EFI partition.
Reboot time, and a wild black screen appeared. GRUB problem, it couldn't find i386 folder (of coursed, I installed it in UEFI mod), I tried to change the prefix to the EFI partition. It didn't work.
"Maybe if I reinstalled it, it will work". Nope, again, same screen.
"Alright, let try to reinstall just grub". Nothing.
Almost giving up, then I saw that there was a "ubuntu" entry in my boot seletion. Clicked on it and it worked flawless. Reboot to test again. Same screen.
I did the same thing, choosing in the boot menu, and thought "let me see if it was booting in BIOS or UEFI", so I ran in terminal '/sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" '
Weirdly, it returned "Legacy boot". Tried this tutorial to install GRUB in EFI ([https://wiki.debian.org/GrubEFIReinstall](https://wiki.debian.org/GrubEFIReinstall)). Reboot and same screen.
Tried to installed again in UEFI. Same thing and same output in the terminal.
Then, I thought "Let me see if I install it in Legacy mode, if it'll do the same thin". Installed it in Legacy Mode.
Oddly, after I reboot, it just got in Ubutu, with no problem at all.

I don't know what happened, but I decided to share this problem that I had

---

### Post by CelticWarrior on 2020-04-25
Welcome and thank you for sharing the weird experience.
Please post your hardware specifications so we can take a look at the problem. And did you made the EFI partition yourself or used the option to "erase and install..."?

---

### Post by cwmoser on 2020-04-25
I was confused with the BIOS versus UEFI alternative.
Watching some Youtube instructional videos about this I found either you have the
old school BIOS (text based and no mouse support) or you have the modern UEFI (graphical and with mouse support).
Its either or, but not both.
Upon power up if you press a key to enter Setup and its text based, your computer is older and predates UEFI.
On the other hand, if you enter Setup and its graphical and you can use the mouse to move around, its UEFI and
your motherboard is more modern than the old BIOS type motherboards.

With UEFI you allocate a small partition on your boot drive for software to boot your PC.
This allocation is done in the installation process when you install Ubuntu Linux.
This is an alternative to the BIOS schema where you have simply a small boot record at the start of your boot drive
which will allow any operating system boot without Microsofts "police action".

That said, all my PCs and laptops use the older BIOS, and I don't select anything to do with UEFI and in fact 
my computers just might not even boot if I did an installation of Ubuntu with UEFI.   
In addition, if I had a PC with UEFI, I would have to make a setting change to 
Safe Boot (or some other name) - which is a Microsoft mandated feature that
only allows Windows 8 or 10 to boot the PC - not allowing Linux or even Windows 7 to boot the PC.

---

### Post by rei-nert on 2020-04-25
> **CelticWarrior said:**
> Welcome and thank you for sharing the weird experience.
Please post your hardware specifications so we can take a look at the  problem. And did you made the EFI partition yourself or used the option  to "erase and install..."?

I made my own ESP (EFI partition) with 250 MB (as recommended in this guide: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace))

My hardware specifications are:
[IMG]https://i.imgur.com/HHdDS65.png[/IMG][SIZE=2][IMG]https://i.imgur.com/EZuQHMx.png[/IMG][/SIZE][IMG]https://i.imgur.com/R3yQBaN.png[/IMG]

---

### Post by rei-nert on 2020-04-25
> **cwmoser said:**
> I was confused with the BIOS versus UEFI alternative.
Watching some Youtube instructional videos about this I found either you have the
old school BIOS (text based and no mouse support) or you have the modern UEFI (graphical and with mouse support).
Its either or, but not both.
Upon power up if you press a key to enter Setup and its text based, your computer is older and predates UEFI.
On the other hand, if you enter Setup and its graphical and you can use the mouse to move around, its UEFI and
your motherboard is more modern than the old BIOS type motherboards.

With UEFI you allocate a small partition on your boot drive for software to boot your PC.
This allocation is done in the installation process when you install Ubuntu Linux.
This is an alternative to the BIOS schema where you have simply a small boot record at the start of your boot drive
which will allow any operating system boot without Microsofts "police action".

That said, all my PCs and laptops use the older BIOS, and I don't select anything to do with UEFI and in fact 
my computers just might not even boot if I did an installation of Ubuntu with UEFI.   
In addition, if I had a PC with UEFI, I would have to make a setting change to 
Safe Boot (or some other name) - which is a Microsoft mandated feature that
only allows Windows 8 or 10 to boot the PC - not allowing Linux or even Windows 7 to boot the PC.

So, about that, my motherboard have both options. When I plug the live-USB and get in the boot menu, I have this screen:
[IMG]https://i.imgur.com/syta3Ou.jpg[/IMG]

---

### Post by CelticWarrior on 2020-04-25
> I was confused with the BIOS versus UEFI alternative.
You still are, I'm afraid, because...
> Watching some Youtube instructional videos about this I found either you have the
old school BIOS (text based and no mouse support) or you have the modern UEFI (graphical and with mouse support).
Its either or, but not both.
That's the problem with watching too much clickbait videos often made by people with inflated egos instead of reading what the real experts say.
Yes, it's either/or indeed but that's not the whole story and the devil is in the details.
No, UEFI doesn't need to be graphical and/or have mouse support and there were BIOS with mouse support. Yes, any firmware settings with *fancy* graphics means UEFI but not all UEFIs have them, most actually don't. It's like thumbs and fingers: All thumbs are fingers but not all fingers are thumbs.

UEFI and BIOS are firmwares that do the some thing (in quite different ways). UEFI replaced the 35 years old BIOS a long time ago so if you have one you don't have the other but... In order to accommodate UEFI-incompatible OSes almost all UEFI have a Legacy mode (AKA CSM AKA "BIOS mode").

> With UEFI you allocate a small partition on your boot drive for software to boot your PC.
This allocation is done in the installation process when you install Ubuntu Linux.
This is an alternative to the BIOS schema where you have simply a small boot record at the start of your boot drive
which will allow any operating system boot without Microsofts "police action".
 
Mostly correct.
The "small partition on your boot drive" is the ESP (EFI System Partition), a small FAT32 formatted partitions where the bootloaders are installed.
The "small boot record at the start of your boot drive" is the MBR (Master Boot Record). But that part about Microsoft is conspirational misinformation. The Linux Foundation supports and recommends Secure Boot. I and the vast majority of "power users" recommend disabling it for convenience only. So, it's an optional feature in the agreed UEFI standard since the beginning (and Microsoft's role in all this is NOT policing).

Additional information regarding partitioning: Windows has strict requirements, Linux has not (but should have the same). For UEFI installations it requires GPT drives and for BIOS/Legacy it requires MBR ("msdos") drives. 

Additional information regarding multi-booting:
In the old days, with BIOS/MBR, we could have only one bootloader.
Now, with UEFI/GPT, we can have many bootloaders coexisting in the ESP. This alone justifies sending BIOS/MBR to the history's rubbish bin where it belongs since almost a decade, once and for all.


> all my PCs and laptops use the older BIOS, and I don't select anything to do with UEFI 
You couldn't even if you wanted. 

> in fact my computers just might not even boot if I did an installation of Ubuntu with UEFI
Surely they wouldn't boot. And it's "installing Ubuntu in UEFI mode", not "an installation of Ubuntu with UEFI".

> if I had a PC with UEFI, I would have to make a setting change to Safe Boot (or some other name) - which is a Microsoft mandated feature that only allows Windows 8 or 10 to boot the PC - not allowing Linux or even Windows 7 to boot the PC. 				 			  			   		 			 			 			

It's "Secure Boot" as commented above. And it's not a "Microsoft mandated feature", it's a feature agreed upon by the consortium that created the UEFI specifications - based on Intel's original EFI design - of which Microsoft is one member of the current [Board of Directors]("https://uefi.org/board"). And most notably for our chitchat here, ALL current major Linux distros and those of the last decade boot perfectly with Secure Boot enabled. Windows 7 probably not but who cares? It's obsolete and unsupported, using it in 2020 with an internet connection is stupid and irresponsible.

---

### Post by cwmoser on 2020-04-26
UEFI has for a long time been a mystery - even to the point of failing when I tried 
to install Ubuntu on a friends laptop having UEFI and Secure Boot a couple years ago.
Now I might get back with him and retry.
I learned a lot from those Youtube videos which did give me a basis in understanding UEFI,
and then you guys clarified a lot of details with either the misinformation or my misunderstanding.
Thanks for the clarification, it was very informative.

---

### Post by CelticWarrior on 2020-04-26
> **rei-nert said:**
> I made my own ESP (EFI partition) with 250 MB (as recommended in this guide: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace))

It should work if you actually followed all the instructions. But if you're installing only Ubuntu, no dual-boot, why not let the installer take care of all of it? It's the option "Erase and install..."
Otherwise, if manually partitioning in advance, one has to select "something else" and tell the installer to use (and format when applicable) all the partition we want to use, one by one, and including the ESP (EFI System Partition) with the correct types for each one.

Other things to be aware of:
[LIST]
[*]Your hardware is old(ish) and from the time when many manufacturers implemented bad/broken firmwares (UEFI) -> If there's UEFI update from the manufacturer (they may still call it "BIOS") then do it before anything else.
[*]Check UEFI settings. If Legacy/CSM can be disabled, just do it. Then you should see only ONE entry for the USB installer. If not, then ALWAYS choose the one with "UEFI: ...". This will boot and install in UEFI mode. Unless...
[*]It doesn't recognize an ESP or it's a MBR("msdos") partitioned drive (it should be GPT) or users select the wrong option when a warning message about the possibility of other systems installed in other mode (this message shouldn't appear in the current release and it was very misleading)
[/LIST]

In summary here are my recommendations:
[LIST]
[*]Update UEFI and disable Legacy/CSM if possible, disable both Secure Boot and Fast Boot options
[*]Boot a live session in UEFI mode
[*]Prepare the drive with the recommend options: Open GParted; with the drive selected go to Device menu > New partition table and select the "GPT" type.
[*]Start the installer and use the automatic installation > "Erase and install..."
[/LIST]

---

