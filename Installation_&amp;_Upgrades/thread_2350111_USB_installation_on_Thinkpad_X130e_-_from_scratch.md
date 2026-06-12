---
title: "USB installation on Thinkpad X130e - from scratch"
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by hespt on 2017-01-21
hi,

I've tried to install various distros of Ubuntu and Linux Mint using a USB stick and each time, after installation is supposedly completed, I restart and am given the options of running live or installing again. if I try to reboot without the USB, I am told there is no operating system.

perhaps against my better judgment I searched and executed various solutions, using boot-repair and following instructions in various responses on these pages:
[http://askubuntu.com/questions/125494/cant-boot-without-flash-drive-plugged-in](http://askubuntu.com/questions/125494/cant-boot-without-flash-drive-plugged-in)
[http://askubuntu.com/questions/142004/cannot-boot-without-usb-stick-after-successful-install](http://askubuntu.com/questions/142004/cannot-boot-without-usb-stick-after-successful-install)
[http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow](http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow)

So I have two questions:
1) is there a way to revert/reformat to factory settings to undo all these "fixes" I've executed? (i have all data backed up so nothing to lose here)
2) how can I successfully install ubuntu on my machine from a USB stick without having to boot from the USB each time?

many thanks for your help.

---

### Post by oldfred on 2017-01-21
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Is that considered a Yoga model?
Lenovo left off AHCI settings on some of those.

Many systems now only boot "Windows Boot Manager". That is not supposed to be allowed per UEFI standard.

But many work arounds.
If only booting Ubuntu, you can change description (delete & add) so description of Windows entry actually boots shimx64.efi. It only check description not actual boot file.
If dual booting there is the fallback or hard drive entry that still works and can boot shimx64.efi. Many system already have that entry, but it is just a copy of Windows own .efi boot file.

Boot-Repair in advanced mode and checking "use the standard efi file" will copy shimx64.efi to bootx64.efi.
But if you do not have an UEFI entry for that as fallback or hard drive boot, then you have to create that.

       
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019) 
    

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by hespt on 2017-01-22
okay, thanks a lot for your response.

Just ran boot-repair, here are details:
[http://paste2.org/2MDWzP1K](http://paste2.org/2MDWzP1K)

x130e does not seem to be a Yoga machine.

I do only need to boot to Ubuntu.

About to reboot now... hopefully something works.

Thanks again.

---

### Post by hespt on 2017-01-22
nope, still says operating system not found when booting without USB...

---

### Post by oldfred on 2017-01-22
You converted your ESP - efi system partition to a bios_grub partition.
The ESP is FAT32 for UEFI boot.
The bios_grub is so grub can install to a gpt partitioned drive in the 35 year old BIOS boot method, CSM with UEFI systems.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I suggest converting sda1 back to FAT32, you may just need to remove bios_grub flag & add boot flag with gparted. It shows as FAT32 already.
And you have the ESP mounted in the fstab.

If you really want BIOS boot, you need a bios_grub but it only is 1 or 2MB and must be unformatted.

Then rerun Boot-Repair.
Also check in advanced options the 'use the standard efi file'.
I would also run the full uninstall/reinstall of grub2.
While it looks like Boot-Repair did correctly reinstall grub, but you are not showing an entry in UEFI.
sudo efibootmgr -v

But many systems including many Lenovo's only want to boot the UEFI entry with "Windows Boot Manager".
But since only Ubuntu we can make the Ubuntu entry use Windows description.

      
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by hespt on 2017-01-23
> **oldfred said:**
> 

Then rerun Boot-Repair.
Also check in advanced options the 'use the standard efi file'.
I would also run the full uninstall/reinstall of grub2.
While it looks like Boot-Repair did correctly reinstall grub, but you are not showing an entry in UEFI.
sudo efibootmgr -v 

ok, followed instructions above. An error message reads "GPT Detected. Pleade create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag)... Then try again."
so in gparted I created an unformatted partition, 1 MiB, with bios_grub flag, then ran boot-repair.
I couldn't find the option that says "use the standard efi file."
results pasted here: [http://paste2.org/ljz9K9Xs](http://paste2.org/ljz9K9Xs)
rebooted, same problem.

> **oldfred said:**
> 
But many systems including many Lenovo's only want to boot the UEFI entry with "Windows Boot Manager".
But since only Ubuntu we can make the Ubuntu entry use Windows description.

      
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Then, after rebooting I tried the above command in terminal and got the message:
** Warning ** : BootA has same label Windows Boot Manager
efibootmgr: could not set variable Boot00B: No such file or directory
efibootmgr: could not prepare boot variable: no such file or directory

Thanks again for your help.

---

### Post by oldfred on 2017-01-23
If it is asking for the bios_grub partition that is a BIOS repair, not UEFI.
And in a BIOS boot of Ubuntu, Boot-Repair may not have all the UEFI repair tools.
So "use standard efi file" may not be there.

My system shows that option in Boot-Repair, but it is not checked by default.

You may have to delete old "Windows Boot Manager" entries in UEFI if updating to a new one.
Some allow duplicate descriptions, others seem not to allow that.

But you need to decide if you want BIOS or UEFI and fix that mode. If UEFI you do not need bios_grub.
IF BIOS you do not need to update UEFI entries.

Be sure to always boot live installer in mode you really want, UEFI or BIOS.

       UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by ubfan1 on 2017-01-23
What are you trying to do?  You cannot dual boot Windows anymore since it looks like you installed Ubuntu to the whole disk.  Neither do you have any UEFI Windows (or Ubuntu) bootloaders in the old EFI partition -- looks like that for reformatted as well.  It's good you have backups, you might need to reinstall Windows and then install Ubuntu.

---

### Post by hespt on 2017-01-24
just trying to run ubuntu, no need for windows.
sounds like I want UEFI, not BIOS.
and yes, this machine has nothing on it that I need to save. Starting from scratch.

there's no way to install/boot to Ubuntu without reinstalling Windows?

thanks.

---

### Post by oldfred on 2017-01-24
You do not need Windows, but may be easier to have the "Windows Boot Manager" entry that really boots Ubuntu using shimx64.efi as posted above.
You need to boot Lubuntu installer in UEFI mode to be able to update entries.

Did you run Boot-Repair (after booting in UEFI mode)?

---

### Post by hespt on 2017-01-24
yes, I made sure I am booting in UEFI mode and turned quick mode off, then ran boot-repair.
[http://paste2.org/CDc5sp3e](http://paste2.org/CDc5sp3e)

if there are other steps here I should be taking and I'm not taking them it's probably because I don't understand how to do certain things. Changing the boot file name, for example. how do I do that?

thanks again.

---

### Post by hespt on 2017-01-24
ok, I made sure I was booting in UEFI, disabled quick mode, and ran boot-repair again.
paste2.org/CDc5sp3e

still detects no operating system on restart without the USB.

If there are directions above that I should be trying but didn't it's because I don't know how to execute them.

what next?

thanks.

---

### Post by oldfred on 2017-01-24
It looks like you ran BIOS based fixes.
Your fstab shows the mount of the efi partition commented out. 

And you show grub installed to the MBR and the sector referred to is the new bios_grub partition. So it looks like it is correctly configured for CSM/BIOS/Legacy boot.
But then you have to set your UEFI to CSM boot only or similar settings somewhere in UEFI.
It should then boot in BIOS/CSM/Legacy mode.

You also show grub installed to the PBR partition boot sector of sda2. That almost never is correct, but the sector(s) of the PBR are not otherwise used, so not a problem. Always install grub to a drive like sda, never to a partition like sda2.  With UEFI, a reinstall of grub to sda will always put correct UEFI boot files into whatever partition is the ESP - efi system partition on sda. UEFI only can boot from an ESP.

If you want UEFI boot, you need to boot Ubuntu installer in UEFI mode, and add Boot-Repair and in advanced mode run the full uninstall/reinstall of grub2. That uninstalls grub-pc(BIOS) and installs grub-efi-amda64(UEFI).

See post #5 on the efibootmgr command to add an entry for "Windows" that really boots shimx64.efi.
But that will only work if you now reconfigure grub version for UEFI boot as you currently have it for BIOS boot.

This user highlights some of the UEFI settings you must change.
 Lenovo 110s  My Experience Installing and Using Linux on my Lenovo 110s UEFI settings
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394) 

        T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by hespt on 2017-01-29
still haven't solved the problem but I'm lost as to what to do :/

---

### Post by oldfred on 2017-01-29
Do you want BIOS boot? It looks like if you set system to boot in CSM/BIOS/Legacy mode it should work.

But if you want UEFI boot, you have to uninstall grub-pc and install grub-efi-amd64.

You may also want to turn off UEFI Secure Boot.

---

### Post by sudodus on 2017-01-29
I have a similar computer, a Thinkpad X131e, and it works well for me both in BIOS and UEFI mode. I can run live drives and installed systems in the internal drive as well as in USB drives.

I suggest that you start from the **lubuntu-16.04.1-desktop-amd64.iso** file.

- If you want to install to the internal drive, just go ahead with the standard method.

- If you want to install the the Lubuntu install USB drive to 'another' USB drive, things are easier, if you remove the internal drive before. Then just go ahead with the standard method.

---

### Post by hespt on 2017-01-29
> **sudodus said:**
> I have a similar computer, a Thinkpad X131e, and it works well for me both in BIOS and UEFI mode. I can run live drives and installed systems in the internal drive as well as in USB drives.

I suggest that you start from the **lubuntu-16.04.1-desktop-amd64.iso** file.

- If you want to install to the internal drive, just go ahead with the standard method.

- If you want to install the the Lubuntu install USB drive to 'another' USB drive, things are easier, if you remove the internal drive before. Then just go ahead with the standard method.

I believe I'm using the Ubuntu MATE 15.04 64-bit amd64 iso file. But I've tried this with other flavors and versions of Ubuntu plus Linux Mint. Should the one you suggest work any differetly?

and I did try changing boot mode to BIOS but I am still given the "operating system not found" message.

thanks.

---

### Post by oldfred on 2017-01-29
The 15.04 version expired a year ago.
The 14.04 & 16.04 versions are LTS or long term support. Others have only a short term support.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Please use a current release.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by hespt on 2017-01-29
my mistake, I'm using 16.04.

---

### Post by sudodus on 2017-01-30
The original 16.04 LTS release is buggy. The first point release, ***16.04.1 LTS*** is debugged and polished. It works much better.

---

### Post by hespt on 2017-01-30
thanks. It took me a minute to figure out, but I am using 16.04.1 LTS (it leaves off the .1 LTS part in the welcome screen)

---

### Post by sudodus on 2017-01-30
Is this an Ubuntu only installation or do you intend to dual boot or multiboot with also other operating systems (for example Windows or some other linux distro)?

***Please try again to install Ubuntu and describe with as many details as possible what happens!*** The more you tell us the better we can help.

[hr][/hr]
You can also try a flavour of Ubuntu with a lighter desktop environment,

- Lubuntu - ultra light
- Ubuntu MATE - medium light
- Xubuntu - medium light

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

If trying live works, it is possible in install the version and flavour that you are trying. Installing is not always straight-forward, there might be problems with the graphics or wifi. In my Thinkpad X131e, the graphics work well, but the wifi chip needs a proprietary driver for wifi. Wired internet (ethernet) works without problems.

---

### Post by hespt on 2017-02-10
just trying to boot Ubuntu. I've reinstalled a bunch of times. No indication that anything is wrong until I restart and see "no operating system found"

I've tried a lot of the fixes that I've seen on other forum threads. All the details are in this thread. ready to quit soon :/

---

### Post by oldfred on 2017-02-10
Did you decide if you want BIOS or UEFI boot?
And if UEFI boot have you run Boot-Repair's advanced mode and 'use stanard efi file'

Using efibootmgr as posted before.
And added either (or both) boot of fallback or UEFI:hard drive entry that uses the standard efi file which is /EFI/Boot/bootx64.efi.
And added an UEFI entry with efibootmgr that says "Windows Boot Manager" but boots /EFI/ubuntu/shimx64.efi. 

My entries, but I do not have a Windows entry as my system is ok with the "ubuntu" description. But I did add the fallback entry just as UEFI OS.
 ```
sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0002,0008,0009,0001,0003,0004
Boot0000* ubuntu    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xfa000)/File([COLOR=#ff0000]\EFI\ubuntu\shimx64.efi[/COLOR])
Boot0001* UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0002* UEFI OS    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xfa000)/File([COLOR=#ff0000]\EFI\BOOT\BOOTX64.EFI[/COLOR])..BO
```

---

### Post by hespt on 2017-02-11
okay, when running boot-repair I didn't see the option of "use standard efi file"

but maybe this helps. here is what I get from efibootmgr:
```

ubuntu-mate@ubuntu-mate:~$ sudo efibootmgr -v
BootCurrent: 0008
Timeout: 0 seconds
BootOrder: 000A,0005,0006,0007,0008,0009
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0006* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0007* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0008* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0009* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000A* Windows Boot Manager    HD(2,GPT,dd0112a4-91e4-43bb-8105-bcea8bb7e673,0xe1800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...8................

```

Again, I really don't know what I'm doing-- barely enough to get through the other threads on similar problems. Most things will have to be spelled out for me.

But maybe something above will help us fix this problem?

Thanks.

---

### Post by oldfred on 2017-02-11
Your default UEFI boot is 000A or the Windows entry which you do not have.
But you have configured system for BIOS boot not UEFI. If you have UEFI Secure boot off and BIOS/CSM/Legacy boot on I thought it would work.

Looks like I missed that you had sda1 FAT32 formatted, but bios_grub partition. The bios_grub must be unformatted and only needs to be 1 or 2MB.

If you want UEFI boot you need the ESP - efi system partition, FAT32 with boot flag.
You have sda1 as bios_grub but huge and formatted FAT32. Change flag from bios_grub to boot to convert to ESP & do grub total uninstall and reinstall from Boot-Repair booted in UEFI mode. That uninstalls the BIOS grub version & installs the UEFI version of grub. 

I normally add both ESP & bios_grub as first two partitions on every drive including larger flash drive.
But make sure ESP is sda1 as that is default for efibootmgr commands,otherwise commands have to be modified to specify drive & partition.

And since only booting Ubuntu easiest to change Windows entry to boot shim instead of bootmfgw.efi.

But to change we have to delete & add again. So delete 000A.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 
    
       
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
     
My first two partitions, almost never use bios_grub anymore but it is only 2MB:

```
Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot, esp
 2      525MB   527MB   2097kB                           bios_grub

```

---

### Post by hespt on 2017-02-11
So it seems we're getting somewhere here but I don't exactly know how to make the changes you suggest.

First, I'm fine with booting either BIOS or UEFI-- whichever will be easiest.

Where do you suggest I go from there? I know how to make basic changes with Gparted but anything more involved I might need some specific step-by-step help.

Thanks.

---

### Post by oldfred on 2017-02-11
First in gparted on sda1 change boot flag from bios_grub to boot.
Shrink sda1 by 2MB.
Make new unformatted partition in the 2MB and leave unformatted, but add bios_grub flag.

The lets check if sda1 still has your efi boot files or if installing BIOS grub saw bios_grub partition and overwrote it. If overwritten then you need to reformat it.

Then you can install either grub-pc(BIOS boot) or grub-efi-amd64(UEFI boot). 
How you boot Ubuntu & then which mode Boot-Repair is in, should let you install correct grub version.
You probably have to do in advanced mode the full uninstall/reinstall of grub to have everything in correct place.

If then UEFI boot, you will need to run the efibootmgr commands posted above.

---

### Post by hespt on 2017-02-13
Ok, here's what I have at the moment. Again, I don't care whether I boot in BIOS or UEFI, I just want to do whatever's easiest.
```

ubuntu-mate@ubuntu-mate:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.5 GiB, 1593864192 bytes, 3113016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5DC7AFAA-9804-4622-93B0-C6195CFBB12B

Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M EFI System
/dev/sda2    1050624 609191935 608141312  290G Linux filesystem
/dev/sda3  609202176 625141759  15939584  7.6G Linux swap
/dev/sda4  609191936 609202175     10240    5M BIOS boot

Partition table entries are not in disk order.


Disk /dev/sdb: 7.3 GiB, 7807696896 bytes, 15249408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6b44f287

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        2048 15249407 15247360  7.3G  b W95 FAT32


Disk /dev/sdc: 7.5 GiB, 8004829184 bytes, 15634432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x183f65c4

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1        2048 15634431 15632384  7.5G  c W95 FAT32 (LBA)
ubuntu-mate@ubuntu-mate:~$ 

```

from Gparted:
sda1 - "EFI System Partition" - fat32 - 512M - boot, esp flags
sda2 - ext4 - 290G - no flags
sda3 - "BIOS-boot" - unknown - 5M - bios_grub
sda4 - linux_suspend - 7.6G - no flags


What to do?

---

### Post by sudodus on 2017-02-13
0. If you find the setting in the BIOS menus, set the computer to boot in BIOS mode.

1. I suggest that you download the Lubuntu iso file [lubuntu-16.04.1-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/lubuntu-16.04.1-desktop-amd64.iso). You find it via [http://releases.ubuntu.com/](http://releases.ubuntu.com/), where you can also find other flavours and versions of Ubuntu.

2. Check with md5sum, that the download was successful. See this link: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

3. Create a USB boot drive with a cloning tool, for example with [mkusb](https://help.ubuntu.com/community/mkusb). This method is very reliable.

4. Boot from the USB boot drive. Check that it works correctly. If not, please ask for help here (but I think it will work because this works well in my similar computer Thinkpad X131e).

5. Use ***gparted*** to create an MSDOS partition table, which makes things easier. You find gparted via the Lubuntu 'System Tools' menu.

6. Start the installer (use the icon on the desktop).

- Select language
- Do *not* download updates; do *not* install third-party software. (Not now, it is better to do it later.)
- 'Unmount partitions that are in use'

7. When you arrive at the the partitioning page 'Installation type', please use the basic method to install: 

- Select '**Erase disk and install Lubuntu**'. This will probably cause less problems than any other alternative.

8. Continue ...

- Check that it is the correct drive and 'Write the changes to disks' (it will probably be on the drive **sda**).
- Accept or modify 'Where you are'
- Select keyboard
- Enter names and password. Do *not* encrypt unless absolutely necessary. Encryption makes things more complicated.

9. 'Installation complete' - Select 'Restart Now'

10. 'Please remove the installation media (in your case the USB pendrive), then press ENTER:'

The computer should reboot into the installed Lubuntu system. Check that it works correctly. If not, please ask for help here (but I think it will work because this works well in my similar computer Thinkpad X131e).

[hr][/hr]
It might be a good idea to start a ***new thread***, if you need help to make the installed system up to date and to add some application programs, that can help you do what you want to do with the computer.

---

### Post by hespt on 2017-02-19
Thank you! These steps worked! I can finally now boot without the USB.

Could it be that this lubuntu iso somehow does not have the same problem as the ubuntu mate that I was trying to install?
Or is it step 5 above-- creating a new MSDOS partition in Gparted before installing?
I would love to know...

One problem (and this is probably for a separate thread): lubuntu does not seem to recognize my audio hardware. No response when I try to adjust volume or change settings in ALSA mixer. On loading audio media in VLC I get this error message.
"[COLOR=#FF0000]Audio output failed:[/COLOR][COLOR=#000000]The audio device "default" could not be used:[/COLOR]
[COLOR=#000000]No such file or directory"

Thanks.[/COLOR]

---

### Post by sudodus on 2017-02-20
Congratulations :KS

I'm the installation worked for you. Maybe step 5 did it. But I am not sure.

-o-

Lubuntu uses the ALSA for audio. It is not as advanced as ***pulseaudio*** and ***pavucontrol***. I use Lubuntu and I install the latter tools,

```
sudo apt-get install pulseaudio pavucontrol
```

Then it will almost always be possible to use pavucontrol's menus to tweak the audio settings until it works.

---

