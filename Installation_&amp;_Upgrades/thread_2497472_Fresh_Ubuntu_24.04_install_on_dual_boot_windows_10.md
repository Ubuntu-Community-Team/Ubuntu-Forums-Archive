---
title: "Fresh Ubuntu 24.04 install on dual boot windows 10 / ubuntu 23.10 : lost windows boot"
date: 2024-05-06
forum: Installation &amp; Upgrades
---

### Post by onbr on 2024-05-06
Hello all,

I hope I am writing on the correct forum, if not please redirect me to the correct one.

I am at a total loss and would very much appreciate some wise help before I do anything stupid and make things worst.

The context :
My PC was on dual boot with Windows 10 (with a separate user data disk) and Ubuntu 23.10 (with a separate disk as /home) all working as a charm
After an aborted upgrade from Ubuntu 23.10 to 24.04 I did a clean Ubuntu 24.04 install using the same partitioning (with reformatting) as on my previous working Ubuntu 23.10.
I should have done an total clonezilla backup which I usually do but didn't this time (Arghhhh, yup I know )
Install went well and Ubuntu 24.04 is up and running BUT
But I cannot boot into my Windows 10, the entry doesn't show up in grub on startup.

Tried boot-repair but to no avail. 

Here is a link to my boot-info : [https://paste.ubuntu.com/p/vJsBJrj2Sc/](https://paste.ubuntu.com/p/vJsBJrj2Sc/)

I would be grateful if someone out there could take a look and help me out before I through my PC out the window ...
Ok no It wont get to that ...
I could of course reinstall everything, both OS but would have to reinstall all my programs and could potentially end up losing something in the process.
So any help would be really appreciated.

Thanks
Olivier

---

### Post by grahammechanical on 2024-05-06
I am not educated enough to understand all that the boot repair summary  says. But it seems to me that you have Windows in BIOS/Compatibility  mode (Legacy Windows) and Ubuntu in UEFI mode. 

Both Windows and Ubuntu must be loading in the same mode for Grub to detect the Windows operating system.

Regards

---

### Post by tea for one on 2024-05-06
[COLOR="#0000FF"]Line 8[/COLOR] - Windows is installed in the MBR of /dev/sdd
[COLOR="#0000FF"]Line 158[/COLOR] - OS#2:   Windows 8 or 10 on sdd2

You have Windows 10 on disk sdd but, according to the report, it is installed in old-fashioned Legacy mode.
Reinforced by the lack of ESP on sdd and no sign of Windows efi  boot files.

Ubuntu is installed in UEFI mode as shown by the ESP on sdc1 containing Ubuntu boot files.

Mixed mode installations should be avoided.
Before you do anything else, back up your personal files.

Best course of action is to install both systems in UEFI mode with GPT

---

### Post by oldfred on 2024-05-06
Since Windows is in old BIOS boot on MBR(msdos) partitioned drive, your old install of Ubuntu must have been in old BIOS boot mode.
You do not have to reinstall to convert your UEFI install to BIOS mode. Only real difference is version of grub.
For UEFI grub2 is grub-efi-amd64 and for BIOS grub-pc. Do not install grub now grub-legacy, but package is still grub) as that is the very old (pre-2010) version.

Boot-Repair is not suggesting that option as it sees your ESP and UEFI install, even though you booted it in BIOS/Legacy/CSM mode.
You should be able to use Boot-Repair's advanced mode and BIOS boot. Choose install & choose drive to install grub into. 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Keep Windows boot loader in MBR of Windows drive. Windows may need repair or turning off fast startup after an update, and then grub will not boot it. But if you have Windows boot loader in MBR, you should be able to boot it from UEFI/BIOS boot menu. Better to have Windows repair/recovery drive and Windows install flash drive for your current version to make Windows repairs.

You have newer UEFI hardware.
Microsoft has required vendors to install Windows in UEFI boot mode on gpt (only) partitioned drives since 2012 and release of Windows 8.
Conversion from MBR to gpt totally erases the entire drive, so best to start planning conversion to gpt when you make major changes, have good backups or new drive. 
Conversion of a data only drive is a bit easier, but UUIDs change & settings have to be updated.

You can boot Ubuntu in BIOS/Legacy/CSM mode from gpt, but must have a bios_grub partition.  
I started converting drives from MBR to gpt back in 2010 with BIOS only system. I knew eventually I would get a newer UEFI system and want gpt.

---

### Post by onbr on 2024-05-07
Hello All,

Thanks for your time and help.

Yes my dual boot install is a bit of a mess (to say the least) and after reading your kind replies I've decided to go the tedious but better way of doing a clean and good :P dual boot install the proper way : A Dual Boot - Windows 11 and Ubuntu 24.04 on separate drives with separate EFI partitions thus avoiding boot issues and will in the future use RescueZilla (Clonezilla gui) to backup everything before doing any major upgrades (which I should have done in the first place (yup lesson learned :mad: ).

Having all (well nearly all :rolleyes: ) my data on separate drives should get me there without losing much.

But before doing that and given the context is there a way I could repair and boot into my Windows 10 to retrieve whatever is there (list of programs, some personal data, ...) ?
My Ubuntu is not a problem as all my personal data is backed up, so that can be wiped (easy and quick to reinstall).

Thanks

---

### Post by oldfred on 2024-05-07
Grub may not boot Windows if hibernated/fast startup on. Fast startup also sets hibernation flag. Or if Windows needs chkdsk or other repairs. You probably need a Windows repair/recovery drive or the installer.

You may be able to directly boot by choosing Windows in BIOS mode by drive from UEFI/BIOS boot menu. Not sure what UEFI systems show as BIOS boot options.
But it looks like your Windows install is damages by the UEFI install of Ubuntu.
Windows normally boots in BIOS mode from a Windows MBR, to a partition with boot flag & more boot files. Since Windows 7 it normally has a smaller boot partition and then main (c: "drive") partition. 
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

I would expect Boot-Repair to then show Windows in MBR of sdd, sdd1 to be NTFS with bootmgr & BCD files and then main install.  But you have sdd1 as Microsoft reserved and sdd2 as ESP. I might try to change flag on sdd2 to boot flag and use Windows repairs to try to add bootmgr & BCD. If you have those somewhere copy those into sdd2. It may also need chkdsk from Windows. All those repairs can only be done from Windows.
your Windows boot partition may not have been the normal sdd1. Windows may default to put boot partition and whatever drive is seen as default boot even when you specify another drive.

While Windows normally has boot partition, it will work ok with all 3 boot files in main install as long as that partition has boot flag. Boot-Repair with BIOS often copies bootmgr & BCD into main install as most uses never see nor know about Windows boot partition and may delete it. And then grub sees two sets of boot files (grub does not use boot flag) and grub will have both Windows boot partition and main install as boot options after Boot-repair's copy of boot files.

If using a Windows ISO to create flash drive installer, best to use Windows Media creation tool to download & install to ISO.
Newer versions of Windows created a .wim file in ISO that is over 4GB which will not fit on FAT32 partition. But UEFI requires FAT32 to boot. Windows creation tools splits .wim file. Some older instructions with Linux do not know about larger .wim. And there are some newer alternatives with Linux.

---

### Post by freddofrog2 on 2024-05-07
I also had the upgrade pathway from 23.10 mulch the boot sectors and partition table a SSD connected in (with for backups) via USB within a 2012 Intel Mac Mini. Distressing.

---

### Post by onbr on 2024-05-10
Hi and Thank you all for your kind and concerned replies :P

I tried a lot of what was proposed + a few other suggestions read here and there, doing it all with tweezers (figure of speech) not wanting to break things further  and ... 
Decided I would do a fresh install of it all, Windows 11 (yup I still need it for a few things) and Ubuntu 24.04, so has to get rid of my crappy setup (thanks for pointing it out) and do it all in a more modern and up to date fashion.
I have most of personal data saved up so that's good. Will just have to go through the whole somewhat tedious install process though but that's ok.
It's a bit like a nice big house clean up where you find some old goodies, throw a lot of them, rearrange your **** and end up exhausted but with a clear mind.

So a big thumbs up for all of you who answered my (finally not so desperate) plea for help.
It always somewhat humbles me when I browse the Internet and its forums to see all these people (you all of which) who take the time to offer replies and solutions (some I must say either totally gibberish or totally out of scope, , no you all mind you; but hey it's a mixed bag).

Cheers ):P

---

