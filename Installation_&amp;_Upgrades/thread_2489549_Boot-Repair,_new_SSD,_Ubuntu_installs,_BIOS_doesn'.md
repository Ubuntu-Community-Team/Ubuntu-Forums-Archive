---
title: "Boot-Repair, new SSD, Ubuntu installs, BIOS doesn't find disc, so no boot"
date: 2023-08-02
forum: Installation &amp; Upgrades
---

### Post by Sun.Dial on 2023-08-02
Laptop HP Pavilion DM4 (approx. Feb 2012) I have installed a new SSD in this laptop having first made a backup of the original.

The new SSD is an EXRAM SSD MSATA MINI SATA3 SATA III 6GB/S SSD Internal Solid State Drive  512GB in a mSATA SSD to 2.5'' SATA Adapter Converter Card Module.

In the BIOS setup, InsydeH20 Setup Utility, the BIOS version is F.OC. I have checked the HP website for an updated version but there doesn't seem to be one.
In the 'Boot Options' section is mentioned only the CD drive, Floppy, and Network, my USB with Ventoy being removed. Also there is no mention of MBR, GPT, EFI or UEFI, Legacy Boot, Fast Boot which I've come across in my search for clues.

From a live Ubuntu CD I can install the OS on to the new drive, but when restarting the BIOS stops and reports:
Boot Device Not Found, Please install an OS on your hard disk, Hard Disk (3F0)

I have run Boot-repair from a USB drive using Ventoy (which is shown as SDA) and the report is located here:
[URL="https://pastebin.ubuntu.com/p/rFpfT4PYHJ/"]https://pastebin.ubuntu.com/p/rFpfT4PYHJ/
[/URL]
I have tried also the Windows 8 installation disk and although it won't install, from the command line I can manipulate the drive, eg create new partitions which GParted recognises.

Any help would be greatly appreciated. Thanks.

---

### Post by oldfred on 2023-08-02
Looks like early UEFI system.
Often had UEFI issues, some by vendor & some with early versions of Ubuntu. 
But almost all versions of HP, require users to go into UEFI(BIOS) settings & change boot order there so it can be in UEFI boot menu.
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

But if UEFI does not correctly see drive, the issue may be your adapter, some are better than others.
Better to use a standard SATA drive for an older system like that.

Trying to look up drive, price seems very low?
Fake scam SSD
[https://ubuntuforums.org/showthread.php?t=2489334](https://ubuntuforums.org/showthread.php?t=2489334)
[https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/](https://arstechnica.com/gadgets/2022/08/walmart-lists-a-30tb-portable-ssd-for-39-it-is-naturally-a-scam/)

---

### Post by MAFoElffen on 2023-08-03
> **Sun.Dial said:**
> Laptop HP Pavilion DM4 (approx. Feb 2012) I have installed a new SSD in this laptop having first made a backup of the original.

The new SSD is an EXRAM SSD MSATA MINI SATA3 SATA III 6GB/S SSD Internal Solid State Drive  512GB in a mSATA SSD to 2.5'' SATA Adapter Converter Card Module.

Why use an mSATA to SATA "adapter card"? Why do you not have the mSATA drive connected directly to the WWAN port of that Laptop? I use a universal drive bay to replace my optical drive as a SATA bay, then use the WWAN port for my mSATA, to give me 3 internal drives in my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,fsuse%,mountpoint,model
NAME     LABEL       SIZE FSTYPE     FSUSE% MOUNTPOINT MODEL
sda                  1.8T                              Samsung SSD 870 QVO 2TB ## SATA
&#9500;&#9472;sda1   {SYSTEM}    550M vfat           7% /boot/efi  
&#9500;&#9472;sda2               128M                              
&#9500;&#9472;sda3   {Windows}   900G ntfs                         
&#9500;&#9472;sda4               983M                              
&#9500;&#9472;sda5                30G                              
&#9500;&#9472;sda6                32G                              
&#9474; &#9492;&#9472;swap swap         32G swap              [SWAP]     
&#9500;&#9472;sda7   bpool         2G zfs_member                   
&#9500;&#9472;sda8   rpool       500G zfs_member                   
&#9492;&#9472;sda9   hpool     397.4G zfs_member                   
sdb                  1.8T                              Samsung SSD 870 QVO 2TB ## SATA 
&#9500;&#9472;sdb1   kpool      1000G zfs_member                   
&#9492;&#9472;sdb2   dpool       863G zfs_member                   
sdc                  1.8T                              Dogfish SSD 2TB  ## mSATA
&#9492;&#9472;sdc1   backups     1.5T zfs_member                   

```
Yes. That is 6TB storage in my laptop. Capacity limit with today's tech as 18TB... (8TB x2 + 2TB)

Whatever you do, your model laptop is still only going to see it as SATA II and do SATA II speeds. That is not a problem. SATA III is backwards compatible.

Next, your laptop is UEFI Capable, as oldfred noted. Why are you installing as Legacy?

My recommends, try the mSATA drive plugged directly into the WWAN port, to test if the problem is with the mSATA to SATA adapter card. It may not be the problem, but then that opens up you having that bay open to install another (regular) SSD Drive later.

Even though mSATA is SATA III, the read/write speeds of the interface and media are slower than SSD SATA III. That is why they are cheaper. That is also why I bought a higher end mSATA drive, to try to make up for that.

---

### Post by Sun.Dial on 2023-08-03
Thank you Oldfred for this information which I have sifted through; it makes interesting reading.
When F9 is pressed I am presented only with two boot options in the list: Internal CD, UFD 3.0 Silicon-Power32G (my Ventoy USB). There is no mention of UEFI unless that is it, excuse my lack of knowledge here.
When F10 is pressed I recognise BIOS settings Main, Security, Diag', System, Config; no mention of UEFI.

Having run Boot-repair again I receive this report.
[http://paste.ubuntu.com/p/QyckQdNR9j/](http://paste.ubuntu.com/p/QyckQdNR9j/)

---

### Post by Sun.Dial on 2023-08-03
Thank you for your suggestion [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000]which I have implemented. I didn't know that there was a WWAN port underneath but it fitted the mSATA card perfectly. 
I then ran Boot-Repair again, report:
[http://paste.ubuntu.com/p/QyckQdNR9j/](http://paste.ubuntu.com/p/QyckQdNR9j/)
The message at the end eludes me I'm afraid.
I then tried the ISO for Super Grub2 Disk 2.04s1 option 1: 'Detect and show boot methods'. This found an OS for the first time after inserting the mSATA card in its new home. 
'Linux /boot/vmlinuz-5.15.0-43-generic (single) (hd1,gpt2)' and it booted the Ubuntu image OK. Success so far. However it will only boot this way up to now.

[/COLOR]

---

### Post by MAFoElffen on 2023-08-03
The output of the following command will answer a lot of missing information that the report is assuming. Please post the ouput of this within CODE tags:
```

sudo dmidecode -t 0

```

---

### Post by Sun.Dial on 2023-08-04
OK, thanks, here's the o/p of dmidecode:

```
[FONT=-moz-fixed]# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: F.0C
	Release Date: 01/21/2013
	ROM Size: 2560 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 15.12
	Firmware Revision: 41.30
[/FONT]
  
```

---

### Post by tea for one on 2023-08-04
> **Sun.Dial said:**
> 
I then ran Boot-Repair again, report:
[http://paste.ubuntu.com/p/QyckQdNR9j/](http://paste.ubuntu.com/p/QyckQdNR9j/)
The message at the end eludes me I'm afraid.
Is it this message:-> The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.

You should be able to disable Legacy boot mode in your UEFI (BIOS) settings.
Power on PC
Immediately tap F10 (one second intervals)
UEFI settings should appear
System Configuration > Boot Options > Legacy Support > Disabled
F10 key to save and exit

---

### Post by Sun.Dial on 2023-08-04
Thanks, 'Sys Config' only shows Boot Options: Post Hotkey delay (sec) 5 and three options for the boot order: CD, Floppy, Network 
There is no mention of '> Legacy Support > Disabled' unless I'm missing something.

---

### Post by tea for one on 2023-08-04
> **Sun.Dial said:**
> Thanks, 'Sys Config' only shows Boot Options: Post Hotkey delay (sec) 5 and three options for the boot order: CD, Floppy, Network 
There is no mention of '> Legacy Support > Disabled' unless I'm missing something.
Unlikely to be missing anything, I suspect that your BIOS version F.0C is old with limited options, but also
> BIOS is upgradeable
Upgrading the firmware on a PC made in 2012 may produce unexpected consequences (i.e. brick the machine)
If the device is unimportant to you, then its worth considering.

In the meantime, can you see if you have any mention of UEFI or EFI in the PC boot menu?
Power on
Immediately tap F9 (one second intervals)
Boot menu should appear
What do you see?

Any sign of (either):-
OS Boot Manager (UEFI)
Boot from EFI File

---

### Post by Sun.Dial on 2023-08-04
Boot Manager menu:
Network Adapter
Internal CD
up/down arrows to change option...
press F10 to BIOS Setup Options

It is quite an old PC but works fine for me with a regular HDD.
I've looked at BIOS updates and there doesn't seem to be anything better, newer.
Thanks for the advice.

---

### Post by MAFoElffen on 2023-08-04
> **Sun.Dial said:**
> OK, thanks, here's the o/p of dmidecode:

```
[FONT=-moz-fixed]# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.0C
    Release Date: 01/21/2013
    ROM Size: 2560 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        [COLOR=#ff0000]Selectable boot is supported[/COLOR]
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        [COLOR=#ff0000]UEFI is supported[/COLOR]
    BIOS Revision: 15.12
    Firmware Revision: 41.30
[/FONT]
  
```
Look harder. You are missing where to change the BIOS Boot mode from Legacy to UEFI mode...

---

### Post by Sun.Dial on 2023-08-04
Hello, yes, I'd seen that but there is no mention of it in the BIOS. Having done some more searching I think that the Advanced tab is actually missing having been locked by the manufacturer. I have tried numerous suggestions to unlock it and recover the Advanced tab but have had no luck so far.
Or, am I looking in the wrong place for this?

---

### Post by oldfred on 2023-08-04
Some systems require you to set the UEFI password to open more settings. Or its turn on UEFI Secure Boot which requires password.
Never lose that password, or reset back to bland when done.

---

### Post by Sun.Dial on 2023-08-04
In your earlier link suggestions I'd read about the possibility of needing to set a password. I recently tried it but still no luck seeing the Advanced tab. Good to try though, thanks.

---

### Post by MAFoElffen on 2023-08-04
Dang.

I looked in the HP Partner Support Portal. I see his Notebook as being on the latest BIOS image for that model. (Though I don't have his serial number.) I downloaded his notepad's manual, and on BIOS, it matches what he has described, to the letter. I didn't see any BIOS "Boot Mode Option" setting in the instructions for his BIOS setup menu.

I'm at a loss for that.

EDIT: I searched the HP support forums and also came up with a dead end on that model for that. Sorry.

---

### Post by MAFoElffen on 2023-08-04
Since there seems to be no option found (so far) to change that notepad to UEFI... Then add an MBR / MSDOS partition table to the mSATA drive and install as Legacy boot(?) That would be my best guess on this notepad.

It came out with Windows 7...

---

### Post by Sun.Dial on 2023-08-05
Thanks for looking those items up.
The serial is 2CE 2070 738
Product no. A6X7 1UA #ABA
System board ID 1793
Dated 3/2/12
and yes, it came with Win7

---

### Post by yancek on 2023-08-05
The information you posted in post 7 indicates that both Legacy and UEFI are supported so it is odd there is no UEFI option in the BIOS.  Beginning at line 6, the report indicates Grub is installed in the MBR of that drive and looks for Grub on partition gpt2.  Line 96 shows the drive is GPT so in that case, to do a Legacy install you need to first create a 1-2MB unformatted bios_boot partition on which to install core.img.  THis is necessary on GPT drives for a Legacy install.  Since you can't seem to install UEFI, this would be necessary.  

Lines 37-43 show an EFI partition with the correct EFI boot files so you must have attempted 2 or more installs, one EFI which created these files and another with Grub in the MBR.  Creating a bios-boot partition (you can use gparted for this which is on the ubuntu install iso) and try rebooting.

---

### Post by Sun.Dial on 2023-08-05
Post #17: blanking mSSD and reinstalling Ubuntu with legacy boot. Will report back.
Post #19, thank you, I will try this next.

---

### Post by Sun.Dial on 2023-08-05
Post #17: blanking mSSD and reinstalling Ubuntu (from Ventoy USB) with legacy boot. No luck, screen shows:
Intel UNDI, PXE-2.1 (build 083)
Realtek PCIe GBE Family Controller Series v2.41 (06/08/11)
PXE-E61 : Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
No bootable device -- insert boot disk and press any key

New Boot-Repair report (before running repair): [http://paste.ubuntu.com/p/xXJ8cpMsbz](http://paste.ubuntu.com/p/xXJ8cpMsbz)

Post #19, thank you, I will try this next.

---

### Post by Sun.Dial on 2023-08-05
Weird!
As the SSD did not seem to be recognised I thought I'd try installing Windows 8, although not quite the original OS. The installation stalled because I'd forgotten to format an SSD partition as NTFS. Leaving the Win8 CD in the tray I inserted the Ventoy USB intending to load GParted. Unexpectedly, I received the same screen error messages as in post 21, followed by an invitation to press any key to boot from the CD, which I missed. A blank screen appeared for a few seconds and then the Ubuntu 22 I'd installed previously on the SSD miraculously booted!

I tried a reboot without the Ventoy USB with the same result, Ubuntu booted, Win8 CD still in the tray.

Puzzled, and not a little intrigued, I used Gparted to make an NTFS partition at the start of the SSD and moved the Ubuntu partition to make space.
I installed Win8 in the NTFS without problems, the SSD partitions were immediately recognised.
Rebooting Win8 worked OK, but strangely, only if the Win8 CD was in the tray.

I'm trying various ways to achieve a boot without the CD or Ventoy USB, maybe even dual boot.
More to follow...

---

### Post by Sun.Dial on 2023-08-06
yancek, post#17: I'm afraid I couldn't get this to work. I looked again in the BIOS options and there is no way to set up a UEFI boot unfortunately. I've changed the SSD to mbr and am trying some alternatives. Thanks for your detailed reply which was very helpful in understanding some of the output of Boot-Repair.

---

### Post by Sun.Dial on 2023-08-06
.....On Hiren's BootCD PE Windows 10 there is a utility program called Bootice by I Pauly. I tried the option 'Physical Disc/Process MBR' on the SSD choosing the option 'Grub 2.00 (boot.img core.img)', then 'Install/Config' which claimed to succesfully change the MBR of the SSD. 

Leaving Hiren's CD in the tray and rebooting, and ignoring the offer to boot from the CD, the grub rescue prompt appeared. Repeating a boot with a Windows 8 pre-release disc in the tray gives the same result.

Running Boot-Repair on this reported a fix (report: [http://paste.ubuntu.com/p/FRb8KknYpC](http://paste.ubuntu.com/p/FRb8KknYpC))

Next boot was with the Windows 8 pre-release disc in the tray, ignoring the offer to boot from that CD. The result was that I could now see the Grub menu with Ubuntu and Win8.
Ubuntu booted OK.
Windows 8 did a scan and repair, rebooted and looked fine.

I haven't used Windows since 2009 and don't intend to, though it has its uses sometimes. I can leave the Win8 CD in the drive for booting purposes if need be but the question remains....

Why is it necessary for a bootable Windows CD to be in play even though the prompt to boot from it is ignored?

Thanks to everyone for their help and advice.

---

### Post by oldfred on 2023-08-06
HP for whatever reason is one of the brands that is least dual boot friendly. Most seem to get it to work, but often have issues.

I have seen others with early HP UEFI give up on UEFI boot and revert to the old BIOS boot mode.
But you still should then have a setting in UEFI/BIOS that says default boot mode is BIOS, not UEFI.

Newer systems seem to try UEFI boot, if that fails, try BIOS boot. Older systems seemed to only boot in mode set in UEFI/BIOS settings.

My old desktop was UEFI, but all UEFI settings were underneath the Legacy/CSM/BIOS settings in System settings. Which is backwards as BIOS/CSM is a part of UEFI, UEFI is not part of BIOS.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

