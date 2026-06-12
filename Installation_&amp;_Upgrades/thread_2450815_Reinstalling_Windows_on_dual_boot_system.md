---
title: "Reinstalling Windows on dual boot system"
date: 2020-09-21
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2020-09-21
I have a laptop on which were windows on the hard drive and ubuntu on an internal SSD.

Windows has been completely trashed and I am in the process of re-installing it.

I am told that the ubuntu instance is intact and not disturbed.

I have a live ubuntu of the same ilk.

How do I start the ubuntu again when windows has trashed grub?

---

### Post by CelticWarrior on 2020-09-21
Why would Windows do that? "Trashed Grub", I mean.

What is your problem exactly?

---

### Post by crip720 on 2020-09-21
If installation of windows does mess up grub, just boot to your Ubuntu USB install boot repair and install grub.  It is possible that windows will leave grub alone.

---

### Post by CelticWarrior on 2020-09-21
That shouldn't be a problem at all in any modern UEFI system, hence my question.
Most of the times is users not understanding how UEFI boot process works, not understanding that bootloaders co-exist in the ESP (EFI System Partition) and that they can be booted independently.
Unlike what happens with BIOS/MBR, removing one OS does NOT warrant re-installation of the other's bootloader in the vast majority of cases.

---

### Post by Impavidus on 2020-09-21
There are still plenty of legacy (i.e., uefi in legacy mode or simple bios) computers around. Basically every computer that originally came with preinstalled Windows 7 or before, which are most computers older than 8 years. Given that computers tend to last for 10–15 years, that could be around 30% of computers still in use.

---

### Post by CelticWarrior on 2020-09-21
Yes, but those UEFI machines that had the preinstalled Windows 7 in Legacy mode shouldn't count because that can and should be installed in UEFI mode. Why they were sold like this has to do with vendors' laziness in updating drive images. Windows 7 could have been installed in UEFI mode easily. One redeeming factor could have been the "downgrade to Windows XP" option some of those machines came with.

---

### Post by makem2 on 2020-09-21
Windows is installed and on boot the machine boots into windows.

I assume therefore that grub has been overwritten in the bootloader and grub needs to be reinstalled.

My question becomes, on which drive do I install grub and how? 

The machine will normally boot the hard drive so I expect grub should be installed there?

---

### Post by CelticWarrior on 2020-09-21
> [COLOR=#000000]I assume therefore that grub has been overwritten in the bootloader and grub needs to be reinstalled.[/COLOR]

Correct assumption for BIOS systems; totally incorrect for UEFI.
Please check UEFI settings > Boot and where "Windows bootloader manager" is set it back to "Ubuntu". Then boot Ubuntu and run 'sudo update-grub' in terminal.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
This ^^^ page has been up for many years now.

---

### Post by crip720 on 2020-09-21
If it is windows 8.1 or 10 then fast boot is on, disable it in windows.  Boot to you ubuntu USB install boot repair and use pastebin to paste output, no repair yet.  Let these people see what you are working with first.  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by CelticWarrior on 2020-09-21
> [COLOR=#000000]The machine will normally boot the hard drive so I expect grub should be installed there?[/COLOR]

Again, this is textbook example of the "not understanding UEFI" problem. 
In UEFI any OS is booted from the ESP (EFI System Partition) - the link above also explains this - no matter where any given OS is installed. Although "boot the hard drive" would have make more sense in BIOS times, even then it wasn't true either. This again reveals a misunderstanding of the boot process.

---

### Post by makem2 on 2020-09-21
The bios tells me the hard drive is booted in UEFI mode but I do not see how to find where there is an option to choose between windows and ubuntu.

---

### Post by CelticWarrior on 2020-09-21
It's in the Boot menu or equivalent. Every firmware is different. Again, where you find "Windows bootloader manager" navigate to it and press Enter (or follow your firmware's specific instructions), other boot options should be listed there. 

Yes, this requires some effort in reading about boot process requirements and your own manual (~5min). If you're installing any OS you don't have the luxury of ignoring basic aspects of the process.

---

### Post by makem2 on 2020-09-21
> **crip720 said:**
> If it is windows 8.1 or 10 then fast boot is on, disable it in windows.  Boot to you ubuntu USB install boot repair and use pastebin to paste output, no repair yet.  Let these people see what you are working with first.  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[https://paste.ubuntu.com/p/rGX8mdccsb/](https://paste.ubuntu.com/p/rGX8mdccsb/)

Edit: Booting into the live usb shows an error:

Check finished: errors found in1 files! You might encounter errors.

---

### Post by CelticWarrior on 2020-09-21
Your summary report clearly shows all the required bootloaders for Windows and Ubuntu present in the ESP, as it should be.
Furthermore, as expected. it shows the following boot order:

```
[COLOR=#000000]BootOrder: [/COLOR][COLOR=#666666]2001[/COLOR][COLOR=#000000],0004[/COLOR]
```
where 2001="[COLOR=#000000]EFI USB Device" (perfectly normal considering you're booting a live session from an external USB media) and 0004=**"**[/COLOR]**[COLOR=#000000]Windows Boot Manager"[/COLOR]**[COLOR=#000000] exactly as expected.

So, again as suggested, you should disable Windows Fast Startup feature as that creates issues for dual-booting and even Windows standalone. Then, for the third time in this thread, **all you need to do is change the boot stanza back to "Ubuntu" instead of "Windows bootloader manager".**  [/COLOR]

---

### Post by makem2 on 2020-09-21
> **CelticWarrior said:**
> Your summary report clearly shows all the required bootloaders for Windows and Ubuntu present in the ESP, as it should be.
Furthermore, as expected. it shows the following boot order:

```
[COLOR=#000000]BootOrder: [/COLOR][COLOR=#666666]2001[/COLOR][COLOR=#000000],0004[/COLOR]
```
where 2001="[COLOR=#000000]EFI USB Device" (perfectly normal considering you're booting a live session from an external USB media) and 0004=**"**[/COLOR]**[COLOR=#000000]Windows Boot Manager"[/COLOR]**[COLOR=#000000] exactly as expected.

So, again as suggested, you should disable Windows Fast Startup feature as that creates issues for dual-booting and even Windows standalone. Then, for the third time in this thread, **all you need to do is change the boot stanza back to "Ubuntu" instead of "Windows bootloader manager".**  [/COLOR]

I am still searching for Windows bootloader manager option which is not in bios.

I will check pastebin for your clue 004=windows boot manager which may help me find it

Fast boot was disabled and I see windows boot manager is on sdb2 but I don't see how to access it to change it.

---

### Post by makem2 on 2020-09-21
Please, advise me where/how to find and edit the boot stanza from either windows or the live ubuntu usb.

Once I find it I will change it.

---

### Post by CelticWarrior on 2020-09-21
First of all, it's in the UEFI ("BIOS") settings > BOOT menu, not in any OS. And surely there aren't that many places where it could be that you miss it.

But it can be managed by software tools thanks to the UEFI improvements over the obsolete BIOS. If you could boot Ubuntu then you would use 'efibootmgr'. From Windows which is the OS you can boot now, there's third-party tool that can be used, [EasyUEFI]("https://www.easyuefi.com/index-us.html").

---

### Post by makem2 on 2020-09-21
> **CelticWarrior said:**
> First of all, it's in the UEFI ("BIOS") settings > BOOT menu, not in any OS. And surely there aren't that many places where it could be that you miss it.

But it can be managed by software tools thanks to the UEFI improvements over the obsolete BIOS. If you could boot Ubuntu then you would use 'efibootmgr'. From Windows which is the OS you can boot now, there's third-party tool that can be used, [EasyUEFI]("https://www.easyuefi.com/index-us.html").

There are only two place to look in the bios, Boot priority option and system configuration

Boot priority:

usb
hdd/ssd
lan
odd

System configuration:

Boot Mode: UEFI boot or CSM boot

No place that windows boot manager could hide

I will try the efibootmgr from the usb

---

### Post by makem2 on 2020-09-21
```

xubuntu@xubuntu:~$ efibootmgr
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 2001,0004,0002,2003,2002
Boot0000* Realtek PXE
Boot0001* Realtek PXE
Boot0002* ubuntu
Boot0003* EFI USB Device (ASIX AX88772 USB Fast Ethernet Controller)
Boot0004* Windows Boot Manager
Boot0007* Realtek PXE
Boot0008* Realtek PXE
Boot0009* Realtek PXE
Boot000A* Realtek PXE
Boot000B* TOSHIBA MQ02ABD100H             
Boot0015* Realtek PXE
Boot0016* Realtek PXE
Boot0017* ubuntu
Boot0018* ubuntu
Boot0019* Realtek PXE
Boot001A* ubuntu
Boot001B* ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
xubuntu@xubuntu:~$ 

```

I see where I can change Windows Boot Manager to ubuntu but 'how' is not obvious. I have to find that boot file and edit it using nano in my case.

I prefer to make the change using ubuntu not third party windows if I can find how!

---

### Post by makem2 on 2020-09-21
Using the third party tool I booted xubuntu into emergency mode.

I am loath to ask for help in this thread so will go try to find where to go from here so as not to risk messing up.

Thank you for the assistance.

EDIT: Checking the journal show errors related UEFI so maybe am in the right thread?

Couldn't get size: 0x800000000000000e

and

MODSIGN: Couldn't get UEFI MokListRT

There are thousands of lines - is it suitable for pastebinit and ask for assistance ?

---

### Post by oldfred on 2020-09-21
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

[https://kb.wisc.edu/page.php?id=58779](https://kb.wisc.edu/page.php?id=58779)
UEFI boot menu:
    Acer - Esc, F9, F12
    ASUS - Esc, F8
    Compaq - Esc, F9
    Dell - F12
    EMachines - F12
    HP - Esc, F9
    Intel - F10
    Lenovo - F8, F10, F12
    NEC - F5
    Packard Bell - F8
    Samsung - Esc, F12
    Sony - F11, F12
    Toshiba - F12


You also have a lot of duplicate and obsolete entries.
You show two types of PXE entries repeated multiple times. Best to house clean duplicates and obsolete entries. UEFI RAM is not unlimited, years ago there was a big issue originally blamed on Linux where UEFI had too many entries. Turned out Windows could also do it, and it was vendors UEFI.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

You also can change boot order with efibootmgr on most systems. HP and a few others only allow change in UEFI ststen (often f2) boot tab.  (not the boot menu)

---

### Post by makem2 on 2020-09-21
Now I am really in a pickle, can't get into windows or ubuntu. However I know I can change the boot order to get windows back and in the extreme, reinstall a fresh ubuntu, losing my previous hard work setting it up.

I can do as you suggest oldfred, do a clean up and seek guidance in fixing ubuntu later.

But today, enough!

Edit: Just realised I can get into recovery mode but no go as it's overlaid by last entries from emergency mode. Oh well, another day.

---

### Post by oldfred on 2020-09-21
You also have grub proxy files which is from Grub Customizer.
Those then are not standard grub files. 
If you use Boot-Repair to do the total reinstall of grub that will reset everything back to defaults, but then you lose any changes you did make.

---

### Post by makem2 on 2020-09-21
> **oldfred said:**
> You also have grub proxy files which is from Grub Customizer.
Those then are not standard grub files. 
If you use Boot-Repair to do the total reinstall of grub that will reset everything back to defaults, but then you lose any changes you did make.

"but you lose any changes you did make", I assume you mean to grub not the ubuntu OS.

I looked at the entries you suggested:

```

xubuntu@xubuntu:~$ sudo efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 2001,0002,0004,2003,2002
Boot0000* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* ubuntu    HD(1,GPT,0ca21933-62a8-4dbd-aa0e-d484ee6d028c,0x800,0x76800)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0003* EFI USB Device (ASIX AX88772 USB Fast Ethernet Controller)    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(2,0)/HD(1,MBR,0x60596519,0x305a94,0x1f00)RC
Boot0004* Windows Boot Manager    HD(1,GPT,0ca21933-62a8-4dbd-aa0e-d484ee6d028c,0x800,0x76800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................
Boot0007* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0008* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0009* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot000A* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv6([::]:<->[::]:,0,0)RC
Boot000B* TOSHIBA MQ02ABD100H                 BBS(HD,TOSHIBA MQ02ABD100H             ,0x500)................-.;.......;.A.;.............................................A.........................
Boot0015* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0016* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0017* ubuntu    HD(1,GPT,0ca21933-62a8-4dbd-aa0e-d484ee6d028c,0x800,0x76800)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0018* ubuntu    HD(2,GPT,e5a1951b-f090-441d-92ce-dbe518417005,0x200800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0019* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c8a6e27,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot001A* ubuntu    HD(1,GPT,0ca21933-62a8-4dbd-aa0e-d484ee6d028c,0x800,0x76800)/File(\EFI\ubuntu\shimx64.efi)
Boot001B* ubuntu    HD(2,GPT,e5a1951b-f090-441d-92ce-dbe518417005,0x200800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
xubuntu@xubuntu:~$

```

I see the duplicates but not confident to remove. Maybe, after I get ubuntu running I could attempt but I keep coming back to the same question, where is the bliddy file to edit lol.

---

### Post by oldfred on 2020-09-21
Please use code tags for longer text. Also preserves formatting. Was missing / in last code [/code].

You do not edit UEFI entries, but install boot loaders whether grub or Windows.
And you show multiple Ubuntu entries & a Windows entry.
Grub only boots working Windows. And then you have to use the UEFI boot menu and Boot 0004 which in boot menu will just say "Windows".

---

### Post by makem2 on 2020-09-23
I have spent much time trying to edit the boot menu but have been unable to.

So, I decided I could try the Boot-Repair tool.

This tool gave me a working grub with unbuntu and windows. Windows boots up correctly but ubunu takes me to emergency mode making me suspect the problem is in a ubuntu file and I may be able to correct it using fsck. However, I have no knowledge how to do it so have asked assistance in the general thread. I will continue to see if I can learn more about that in the meantime.

I feel it would be easier for me to work on the machine which has the error to correct the duplicates pointed out. I have yet to find the boot menu and I am certain the the choice of OS is not in Toshiba bios. 

I have a modern machine and changing the boot OS is easy from the 'BIOS' so called.

---

### Post by UbuntuWho on 2020-09-23
Hello @makem2; just thought I'd offer my two cents. I used to have a dual-boot of Windows 7 and Ubuntu 14.04. Windows was using UEFI, and Ubuntu was using Legacy BIOS. Now, I have Ubuntu 18.04 using the UEFI predominantly, but perhaps I can still give some advice.

UEFI and BIOS are completely different. This [AskUbuntu]("https://askubuntu.com/questions/446968/are-there-any-drawbacks-to-legacy-bios-as-opposed-to-uefi#447014") answer should help you understand the difference, but basically, UEFI provides a better and faster way that the OS can use the native hardware better, while BIOS is used as a fallback. In my experience, it's best to give Windows complete control of the UEFI, especially with versions later than Windows 7, and have Ubuntu or other OSes on legacy BIOS, but since you (the OP) want both to use UEFI, then perhaps what you need is a GRUB alternative. There was already a link to some in that AskUbuntu answer I shared, but [here it is again]("http://www.rodsbooks.com/efi-bootloaders/").

For concerns about *fsck*, here's an article on [Tecmint]("https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/") that should help you. *Fsck* shouldn't wipe your Ubuntu partition unless the problem is really serious, but my guess is that it isn't that bad. Fsck merely checks and corrects partition errors. If you run it and still can't boot, then you might need to reinstall Ubuntu. You can use your Live USB stick to access the hard drive and copy whatever you want to save to external storage before wiping.

That's all I can think of. Hope I helped you today! :)

---

### Post by makem2 on 2020-09-23
Thank you for your input. Ive read the fsck link. and have used it in the past but not from emergency mode.

As for UEFI and BIOS, both machines refer to what I previously called BIOS as BIOS, perpetuating confusion. But, I have been put straight. :-)

I am considering a new machine and passing this one with its working windows on down the family chain.

Just read that you can fsck the dodgy partition from a live usb so have that to look into.

---

### Post by oldfred on 2020-09-23
Many vendors continue to call UEFI as 'BIOS'. And offer BIOS updates, even though really UEFI updates.
Microsoft has required vendors to install in UEFI/gpt configuration since 2012 and release of Windows 8, so not sure why vendors continue to use term BIOS. 

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by makem2 on 2020-09-23
Thanks for the help oldfred,

```

xubuntu@xubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.42 GiB, 1510060032 bytes, 2949336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors
Disk model: OCZ-VECTOR180   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9EFB600C-A9FF-4A05-863B-84E383D8B32F

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    487423    485376   237M EFI System
/dev/sda2     487424  40486911  39999488  19.1G Linux filesystem
/dev/sda3   40486912 464422911 423936000 202.2G Linux filesystem
/dev/sda4  464422912 468860927   4438016   2.1G Linux swap


Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ02ABD1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C79D48CD-4D4D-4DAA-A116-0A83EBA9B7EC

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048      34815      32768    16M Microsoft reserved
/dev/sdb2       34816 1715957759 1715922944 818.2G Microsoft basic data
/dev/sdb3  1715957760 1953521663  237563904 113.3G Microsoft basic data


Disk /dev/sdc: 14.6 GiB, 15664676864 bytes, 30595072 sectors
Disk model: Cruzer Blade    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x60596519

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sdc1  *          0  3247999  3248000  1.6G  0 Empty
/dev/sdc2       3168916  3176851     7936  3.9M ef EFI (FAT-12/16/32)
/dev/sdc3       3248128 30595071 27346944   13G 83 Linux
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

/dev/sda1 contains a vfat file system

xubuntu@xubuntu:~$ sudo e2fsck -f -y -v /dev/sda2
e2fsck 1.45.5 (07-Jan-2020)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      376542 inodes used (30.10%, out of 1250928)
         659 non-contiguous files (0.2%)
         690 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 327959/384/1
     4113478 blocks used (82.27%, out of 4999936)
           0 bad blocks
           1 large file

      283291 regular files
       43417 directories
          55 character device files
          25 block device files
           0 fifos
         268 links
       48537 symbolic links (46902 fast symbolic links)
        1208 sockets
------------
      376801 files
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
                                                                               
      376542 inodes used (30.10%, out of 1250928)
         659 non-contiguous files (0.2%)
         690 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 327959/384/1
     4113478 blocks used (82.27%, out of 4999936)
           0 bad blocks
           1 large file

      283291 regular files
       43417 directories
          55 character device files
          25 block device files
           0 fifos
         268 links
       48537 symbolic links (46902 fast symbolic links)
        1208 sockets
------------
      376801 files
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3
/dev/sda3:                                                                      Inode 2623633 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 2628396 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3:                                                                      Inode 3934686 extent tree (at level 1) could be shorter.  IGNORED.
                                                                               
      418093 inodes used (3.15%, out of 13254656)
        3203 non-contiguous files (0.8%)
          80 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 416969/268/2
    12562303 blocks used (23.71%, out of 52992000)
           0 bad blocks
           1 large file

      382759 regular files
       34296 directories
           0 character device files
           0 block device files
           4 fifos
           0 links
        1023 symbolic links (840 fast symbolic links)
           2 sockets
------------
      418084 files
xubuntu@xubuntu:~$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.45.5 (07-Jan-2020)
Pass 1: Checking inodes, blocks, and sizes
Inode 2623633 extent tree (at level 2) could be narrower.  Optimize? yes

Inode 2628396 extent tree (at level 2) could be narrower.  Optimize? yes

Inode 3934686 extent tree (at level 1) could be shorter.  Optimize? yes

Pass 1E: Optimizing extent trees
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****

      418093 inodes used (3.15%, out of 13254656)
        3203 non-contiguous files (0.8%)
          80 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 416969/268/2
    12562280 blocks used (23.71%, out of 52992000)
           0 bad blocks
           1 large file

      382759 regular files
       34296 directories
           0 character device files
           0 block device files
           4 fifos
           0 links
        1023 symbolic links (840 fast symbolic links)
           2 sockets
------------
      418084 files
xubuntu@xubuntu:~$ sudo e2fsck -f -y -v /dev/sda4
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda4 is mounted.
e2fsck: Cannot continue, aborting.


xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda4
/dev/sda4 is mounted.
e2fsck: Cannot continue, aborting.


xubuntu@xubuntu:~$

```

I don't see any errors.

I had been trying with fsck but only with -p and -A parameters

---

### Post by oldfred on 2020-09-23
You can only run the fsck on the ext family of formats, or ext4, ext3, or ext2.
There are other tools for other formats. And swap is unformatted so you cannot run any fsck on it (not needed).

It did do some correction on sda3.

---

### Post by makem2 on 2020-09-23
> **oldfred said:**
> You can only run the fsck on the ext family of formats, or ext4, ext3, or ext2.
There are other tools for other formats. And swap is unformatted so you cannot run any fsck on it (not needed).

It did do some correction on sda3.

Yes, I now see it. I'm wondering what effect that will have because grub seems to have stopped working and the machine boots straight into windows.

Maybe I need to run Boot-Repair again.

Its late so that for tomorrow.

Thanks again for the help.

---

### Post by makem2 on 2020-09-23
Decided I wouldn't sleep if I didn't try Boot-Repair so tried it. 

I can boot windows but grub boots ubuntu to emergency :-(

[URL="https://paste.ubuntu.com/p/jjyk2sXkfb"]https://paste.ubuntu.com/p/jjyk2sXkfb


[/URL]sleep.............

Had a look at the Boot-repair output and see that the fstab on sda2 is incorrect now. It relates to the old layout of the drives, eg, /media/WinData no longer exists. Ive had failed boots in the past because of incorrect fstab. I need to correct that, chroot I believe if I can remember how.

sleep.............

Edit: I cannot get back to this machine until end of Novermber, but I WILL be back. (No I am not sleeping!)

---

### Post by makem2 on 2020-09-25
Solved using notes I made years ago about fixing grub from a live usb before I left.

Having chrooted into the old /sda2 xubuntu I # out the old entries in the /etc/fstab which were no longer valid, checked with /mount -a that it appeared ok. Rebooted, crossed fingers & legs and up came the previous xubuntu quite happy which made two of us!

My notes below in case it helps anyone else. (If you see errors please point them out to me.)

[https://www.dropbox.com/s/j2nocslu4qzzw5n/notes.png?dl=0](https://www.dropbox.com/s/j2nocslu4qzzw5n/notes.png?dl=0)

---

