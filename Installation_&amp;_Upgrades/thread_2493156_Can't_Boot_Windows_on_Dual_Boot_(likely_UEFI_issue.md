---
title: "Can't Boot Windows on Dual Boot (likely UEFI issue)"
date: 2023-12-05
forum: Installation &amp; Upgrades
---

### Post by zekereyna on 2023-12-05
Hello! I'm looking for help getting access to my Windows OS.

I have a PC that I've been dual-booting Windows and Ubuntu on for a while now. I think at some point earlier this year, either Windows or Ubuntu upgraded, and since then my boot sequence hasn't been working as expected.

I currently can't boot into Windows whatsoever.

I downloaded and ran the Boot Repair tool here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . It gave me a pastebin link here: [https://pastebin.ubuntu.com/p/qZh9zng3Nx/](https://pastebin.ubuntu.com/p/qZh9zng3Nx/)

After some inspection using Stack Overflow + Reddit (r/Ubuntu) + Ubuntu forums I've surmised that it might be an EFI issue? It's possible that my Windows + Ubuntu installations were both running in Legacy (BIOS) mode, and maybe I upgraded to Ubuntu 22 with EFI set.

The actions I'm considering are:
- figure out what the startup tool is erroring on. It mentions a blocker on "GPT detected. Please create a BIOS-BOOT partition..." and then run the startup tool again
- reinstall ubuntu 22, but on Legacy (BIOS) mode. Maybe windows will magically be accessible then
- reinstall Windows (don't have an installation disk, nor a disk drive... so will be interesting)

What I've done:
- go to BIOS on startup and try to load every single boot option
  - there is a windows option, but when I click it, the screen flashes black for a second and brings me back to where I was in my BIOS
- load ubuntu from a usb in non-UEFI (legacy) mode
  - this worked, but didn't know what to do next? maybe i should update grub?

I don't recall my exact configuration, but it seems like 3 of my drives are GPT and 1 is MBR. I'm not sure if that's a blocker for upgrading Windows to UEFI, but it's making debugging confusing. Especially since the pastebin link claims that 3 of these drives also _have_ an MBR in them.

I would greatly appreciate any pointers or tips! Once I figure out how to get access back to Windows, I want to then (separately) put energy into getting everything onto UEFI and GPT to make this simpler.

---

### Post by oldfred on 2023-12-05
You have UEFI system, and UEFI installs of both Ubuntu & Windows.
Not sure what previous error was but installing grub in BIOS mode makes it worse.
And you have old Windows BIOS boot files in gpt's protective MBR. That by its selft is not an issue as long as you do not attempt to boot in BIOS mode as then Windows will not boot.
Since drives are gpt, Windows has to be UEFI boot. Conversion of Windows to BIOS also converts drive to very old MBR(msdos) and totally erases drive.

Not sure why Boot-Repair says Legacy Windows installed, unless you have an old install, you copied to the gpt drive.
Windows can only boot in UEFI mode from gpt drives. And only in BIOS mode from MBR(msdos) drives. Both drives are gpt.

You should make sure system is set for UEFI boot.
Can you boot Ubuntu or Windows directly from UEFI boot menu.
See lines 130 Windows  & 132 Ubuntu, both are UEFI boot entries. And should work.
Grub only boots working Windows. But if Windows update turned fast start up back on, then grub will not boot it.

How you boot install media, UEFI or BIOS for both Windows & Ubuntu is both how it installs and how it repairs. 
Only boot in UEFI mode.

---

### Post by tea for one on 2023-12-06
> **zekereyna said:**
> reinstall Windows (don't have an installation disk, nor a disk drive... so will be interesting)
You can download (free of charge) a Windows 11 iso and make an installation/rescue usb disk.

Have you backed up all your personal data from both Windows and Ubuntu?

---

### Post by zekereyna on 2023-12-06
> [COLOR=#000000]And you have old Windows BIOS boot files in gpt's protective MBR. That by its selft is not an issue as long as you do not attempt to boot in BIOS mode as then Windows will not boot.[/COLOR]


It very much could be an older install -- I setup this computer in 2018.

> [COLOR=#000000]Can you boot Ubuntu or Windows directly from UEFI boot menu.[/COLOR]
[COLOR=#000000]See lines 130 Windows & 132 Ubuntu, both are UEFI boot entries. And should work.[/COLOR]

From the boot menu (my bios, not grub) I've tried all the options and the only one I can access is Ubuntu. 
I'm a little unclear on the differences between BIOS and UEFI boot menus, so the steps I take are:
- shut off computer
- hold power button to trigger GO2BIOS 
- verify if mode is "Legacy/UEFI" or"UEFI"
- select boot options

When I've booted up Ubuntu, grub also gives me an option to go to "UEFI firmware settings" and that brings me back to the same boot menu (BIOS). 
My motherboard's manual (which includes bios info) can be found here: [https://www.msi.com/Motherboard/H370M-BAZOOKA/support#manual](https://www.msi.com/Motherboard/H370M-BAZOOKA/support#manual)

I've also tried changing from "Legacy/UEFI" to just "UEFI" and when in the former there are more boot options. 
It lets me select each drive as an "option", when in UEFI it just lets me select *UEFI Hard Disk Drive* which has additional priorities *Windows Boot Manager *and *ubuntu (P2 ...*
I'm giving WBM the priority, but the screen blinks and then it boots into ubuntu via grub. When I disable ubuntu in the priorities it just brings me back to the BIOS.
When I switch to *Legacy/UEF* and choose one of the drives (SATA2, SATA3, etc) as my boot priorities, it'll just say

*Reboot and Select proper Boot Device or Insert Boot Media in selected Boot device and press a key*

Going forward, I'll assume that everything should be UEFI and focus on figuring out why Windows isn't working from the boot menu. I was reading about how EFI works, and noticed a couple things about all my partitions:
- they have 17MB in the front of each GPT drive (says "Windows Reserved")
- on the windows drive there is also a FAT partition that gets mounted to /boot/efi
- I looked through the /boot/efi directory while booted into ubuntu and noticed that it has "Windows" and "ubuntu" in it... but don't know how to make sense of it. I want to check if any needed files are missing

---

### Post by zekereyna on 2023-12-06
> **tea for one said:**
> You can download (free of charge) a Windows 11 iso and make an installation/rescue usb disk.

Have you backed up all your personal data from both Windows and Ubuntu?

Huh! For some reason I thought I would be asked for a product key prior to downloading the ISO. 
I just looked at [https://www.microsoft.com/software-download/windows11](https://www.microsoft.com/software-download/windows11) and it seems fairly easy to download the ISO? 

I don't think my PC was windows 11. My pastebin link seemed to indicate it could be Windows 7 or 8. I'll look around and see if I can find the correct ISO.
If I can boot via windows on a usb then I can poke around and see what's wrong. I think that would be a great help.

It's been a while so I'm not super confident on my backups. I think I have everything backed up to my last drive but I'm not 100% sure. 
It's hard to verify what the contents of the NTFS drives are. I'll poke around.

I do have a partition that says:

*Microsoft Windows Recovery Environment (524 MB)*

maybe that is a backup or something?

---

### Post by oldfred on 2023-12-06
Essentially there is no more BIOS systems.
Microsoft required vendors to install Windows 8 in UEFI boot mode to only gpt partitioned drives starting in 2012. Because large users wanted newer software but had older BIOS only systems they allowed BIOS/MBR installs, so both old & new systems could use same software.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
Many vendors still call it BIOS, but it really is UEFI.

starting in 2020, vendors are starting to make UEFI only systems.
My Dell with Intel 11th Gen chip, required a new motherboard. I think Dell did not reset Product key in UEFI. So my Windows would not work. The download of a new Windows would not install nor repair.
I used a Dell recovery download and it totally erased all of Windows and my Linux dual boot.  It was just like the day I purchased it.
My Linux on laptop is mostly a copy of my desktop, so backed up. I had saved Windows product keys for Windows purchased software, so I should be able to reinstall everything. Debating if I want to make it dual boot again or just use external SSD with full install of Kubuntu which works very well.

Your Window UEFI product key is in your UEFI, if you purchased system with Windows. 
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

If older system, Windows 11 may not work. It does some checks on hardware to make sure it qualifies.
I have an old Windows used for TV only and it was 8 upgraded to 10. And every update to 10 says hardware does not qualify for 11.

---

### Post by tea for one on 2023-12-06
> **zekereyna said:**
> 
I do have a partition that says:

*Microsoft Windows Recovery Environment (524 MB)*

maybe that is a backup or something?
If you are not sure, then it is probably not wise to proceed with this type of recovery.
Anyway, how would you use it if you cannot boot your version of Windows?

Have you considered a complete backup of Windows data and a fresh install of Windows 11?

---

### Post by ubfan1 on 2023-12-06
If you're going to create a Windows boot USB, if you have access to a Windows machine, it'll be easier to download Microsoft's Media Creation Tool, and then run it.  It will download an ISO (of its own choice unfortunately, but these days hopefully the latest 23h2) and write a USB.  If you really want (or already have) a Windows ISO to write it to a USB simply make a big enough partition FAT, mount the ISO and copy everything to the USB except the too-big ...soruces/install.wim:
rsync -avP --exclude sources/install.wim /media/user/CCCOMA_X64FRE_EN-US_DV9/* /media/user/yourUSB
Then install the wimtools package, and use wimsplit to break up the 5.3 GB file:
wimsplit /media/user/CCCOMA_X64FRE_EN-US_DV9/sources/install.wim /media/user/Win23h2/sources/install.swm 3000

That should successfully boot.

With a 2018 machine, a new Win 11 install should pick up the machine's license and activation.
I've done two W11 installs on older machines (shift F10 for a cmd window, regedit and enter the bypassTPMCheck=1 (and BypassRAMCheck and BypassSecureBootCheck))which had dual boot set up, and the dual boot still worked.  Virt-manager will install the W11 but needs the TPM emulator (if the tpm software is present, it will just get used.  I tried everything manually, and never quite got the right tpm invocation, but virt-manager took my (manual) vm and it just worked.

---

### Post by tea for one on 2023-12-06
Ventoy can also be used to create a Windows 11 boot usb.
Instructions are available for a Linux GUI.
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)

---

### Post by zekereyna on 2023-12-07
> [COLOR=#000000]Essentially there is no more BIOS systems.[/COLOR]
[COLOR=#000000]Microsoft required vendors to install Windows 8 in UEFI boot mode to only gpt partitioned drives starting in 2012. Because large users wanted newer software but had older BIOS only systems they allowed BIOS/MBR installs, so both old & new systems could use same software.[/COLOR]
[COLOR=#000000]CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode[/COLOR]
[COLOR=#000000]Many vendors still call it BIOS, but it really is UEFI.[/COLOR]

Thank you for the clarification here. I did some digging around for my product key and haven't found it yet.
 I don't happen to have a sticker on my tower with the product key, and I can't find my windows disc.

I did mount my windows OS drive however, and discovered I was running Windows 10!
I followed the instructions from this link: [https://superuser.com/questions/363018/how-do-i-tell-what-version-and-edition-of-windows-is-on-the-filesystem](https://superuser.com/questions/363018/how-do-i-tell-what-version-and-edition-of-windows-is-on-the-filesystem)

```
&#10140;  Diagnosis pwd
/media/zeke/Windows/ProgramData/Microsoft/Diagnosis
&#10140;  Diagnosis cat osver.txt 
10.0.19045%

```

I poked around, and if this drive gets wiped I'm not terribly worried. So I might strongly consider a fresh install after I've backed up pictures + documents.

I'm not super familiar with the EFI folders, but I did notice the "Windows" efi folder in the efi partition did not match the "boot" efi folder in the windows partition.

The former (from the windows OS partition) looks like:
```
&#10140;  EFI pwd
/media/zeke/Windows/Windows/Boot/EFI
&#10140;  EFI ls
bg-BG         da-DK  es-ES  fr-FR  kd_02_10df.dll  kd_02_1969.dll  kd_0C_8086.dll       lv-LV        pt-BR     sk-SK       uk-UA
bootmgfw.efi  de-DE  es-MX  hr-HR  kd_02_10ec.dll  kd_02_19a2.dll  kdnet_uart16550.dll  memtest.efi  pt-PT     sl-SI       winsipolicy.p7b
bootmgr.efi   el-GR  et-EE  hu-HU  kd_02_1137.dll  kd_02_1af4.dll  kdstub.dll           nb-NO        qps-ploc  sr-Latn-RS  zh-CN
boot.stl      en-GB  fi-FI  it-IT  kd_02_14e4.dll  kd_02_8086.dll  ko-KR                nl-NL        ro-RO     sv-SE       zh-TW
cs-CZ         en-US  fr-CA  ja-JP  kd_02_15b3.dll  kd_07_1415.dll  lt-LT                pl-PL        ru-RU     tr-TR

```

whereas the latter (the /boot/efi partition used by UEFI on startup) looks like:
```
root@zeke-MS-7B24:/boot/efi/EFI/Microsoft/Boot# pwd
/boot/efi/EFI/Microsoft/Boot
root@zeke-MS-7B24:/boot/efi/EFI/Microsoft/Boot# ls
BCD      bg-BG         boot.stl  Fonts  hr-HR  kd_02_1af4.dll  kd_07_1415.dll  Resources  sl-SI  winsipolicy.p7b
BCD.LOG  BOOTSTAT.DAT  cs-CZ     fr-FR  hu-HU  kd_02_8086.dll  kd_0C_8086.dll  sk-SK      uk-UA  zh-CN

```

the dates on the files are slightly different as well, so I'm curious if maybe I just need to update the EFI partition that UEFI uses with the correct files from the Windows EFI boot folder?
I will for sure do more research before I touch any of that though.

---

### Post by zekereyna on 2023-12-07
> **tea for one said:**
> If you are not sure, then it is probably not wise to proceed with this type of recovery.
Anyway, how would you use it if you cannot boot your version of Windows?

Have you considered a complete backup of Windows data and a fresh install of Windows 11?

Strongly leaning on a fresh install haha. 
I was hoping that Windows Recovery Environment might be an alternative boot I could use to get into a "recovery mode" to fix things.
I'm reading lightly about it, and it seems like that should be the intent: [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/add-a-hardware-recovery-button-to-start-windows-re?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/add-a-hardware-recovery-button-to-start-windows-re?view=windows-11)

However, I never saw a "Recovery" option in my boot priorities. So I suspect that my UEFI boot configuration for the windows side of things is just supremely messed up.
I also poked around my windows partition to investigate further but haven't modified or moved any files yet.

---

### Post by zekereyna on 2023-12-07
> [COLOR=#000000][FONT=Ubuntubeta]If you're going to create a Windows boot USB, if you have access to a Windows machine, it'll be easier to download Microsoft's Media Creation Tool, and then run it. [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR]
I'll dig up my Acer laptop or my partner's Lenovo and see if I can boot up windows there and use Microsoft's Media Creation Tool. Thank you for the pointer!

I'll also look into Ventoy.

---

### Post by zekereyna on 2023-12-07
Hello all!

Using Microsoft's Media Creation Tool allowed me to successfully boot into Windows again!

I'm running into wifi adapter issues, but super happy to finally have access to my device again :D 
I can mark this as SOLVED, but let me know if I should post a summary or anything for future reference. 

My next steps are:
- figure out Wifi Adapter issues. Looks like once I booted into windows successfully I was unable to maintain a sustained connection (ping google.com gave latency of 300 ms in best case)
- separate boot sequences into separate drives. looks like I can probably avoid grub boot menu stuff if I just have the OS's booting from separate drives via BIOS (UEFI) menu
- move Ubuntu to the SSD, just bc I don't like performance on my HDD
- ensure all my drives are GPT and don't have any old bootloaders sitting around on them since this confused things quite a bit
- upgrade the BIOS (looks like I have never upgraded it... and maybe that can improve performance?)

:D

---

### Post by tea for one on 2023-12-07
> **zekereyna said:**
> Using Microsoft's Media Creation Tool allowed me to successfully boot into Windows again!
Did you repair Windows or install from scratch?
> **zekereyna said:**
>  separate boot sequences into separate drives. looks like I can probably avoid grub boot menu stuff if I just have the OS's booting from separate drives via BIOS (UEFI) menu
Windows on one disk and Ubuntu on a separate disk is ideal.
Both systems installed in UEFI mode with GPT.
Each system should have its own ESP to allow independent operation.
When installing (or re-installing), only have the target disk available.

---

### Post by oldfred on 2023-12-07
I always liked separate drives for each system. But if only one SSD, dual boot on that drive is ok.
If SSD is larger you can use HDD for backs. Or use HDD for data, and/or Ubuntu's /home.
With SSD installs of Ubuntu on smaller drive I still kept /home in / so on SSD, but moved all data out of /home to data partition on HDD, so /home really only was my user settings which are loaded more often so SSD better.
Now like SSD, so have larger SSD and use old SSDs in USB adapter as external drives for both boot  with full install & data.

First on list should be backup. 
I like rsync to multiple places but TheFu's use of rdiff is actually better. Many posts by him on backup if you want more info.
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)

I do not recommend move of Ubuntu from HDD to SSD, but do a new install & restore from backup. Or rsync /home, data and maybe other folders. If you export list of installed apts you can easily reinstall them. New install & restore should only take about an hour. We have had users do a image backup & restore & we end up spending days straitening out issues of duplicate UUIDs & total reinstall of grub. Image copy may work if to totally new drive & not using old drive, or to totally different system. But I still recommend new installs.

---

### Post by zekereyna on 2023-12-12
> [COLOR=#000000]I always liked separate drives for each system. But if only one SSD, dual boot on that drive is ok.[/COLOR]

I just updated my configuration so drives are largely separate for each OS!
- 1 TB NVME <- windows, for games and videos
- 1 TB HDD <- half windows, half ubuntu (no OS, just storage)
- 120 GB SSD <- windows OS
- 240 GB SSD <- ubuntu OS

> [COLOR=#000000]First on list should be backup.[/COLOR]
backed up windows and ubuntu prior to reinstalling anything!

> [COLOR=#000000] do not recommend move of Ubuntu from HDD to SSD, but do a new install & restore from backup.[/COLOR]


> [COLOR=#000000]Windows on one disk and Ubuntu on a separate disk is ideal.[/COLOR]
[COLOR=#000000]Both systems installed in UEFI mode with GPT.[/COLOR]
[COLOR=#000000]Each system should have its own ESP to allow independent operation.[/COLOR]
[COLOR=#000000]When installing (or re-installing), only have the target disk available.[/COLOR]

thank you both for the advice. 
When installing ubuntu to the 240 GB SSD I unplugged all my other drives and installed ubuntu fresh, then once I verified startup worked I restored from backup.
Worked!

> [COLOR=#000000]Did you repair Windows or install from scratch?[/COLOR]
repaired windows with startup repair!

---

### Post by tea for one on 2023-12-12
Thank you for the update.
Two large disks for storage and two smaller disks for each OS - good choices.
Don't forget to backup your data regularly - backups are your personal lifebelt.

---

