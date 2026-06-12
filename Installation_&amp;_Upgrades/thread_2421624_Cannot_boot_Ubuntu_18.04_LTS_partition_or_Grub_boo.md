---
title: "Cannot boot Ubuntu 18.04 LTS partition or Grub bootloader"
date: 2019-06-24
forum: Installation &amp; Upgrades
---

### Post by yeedyourlasthaw on 2019-06-24
I was dumb and removed Ubuntu 16.04 without correctly removing the grub bootloader first. My Windows 10 is EFI.
After I removed Ubuntu I have not been able to boot my newly partitioned Ubuntu 18.04 lts and grub bootloader does not pop up anymore.

Additionally I have somehow got an old fedora boot that I can still see in bios, I think I have really messed things up at this point (I am clearly a noob).

Please let me know if there is any info I can provide for you to better help me with this issue, any help would be appreciated greatly.

---

### Post by oldfred on 2019-06-24
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Did you install in UEFI boot mode?
You can use efibootmgr to remove UEFI boot entries. And remove folders in ESP - efi system partition for old installs.
Your new install should have added a new UEFI ubuntu entry, but you now may have old ones also.
Report above will show this which shows all your UEFI boot menu entries:
sudo efibootmgr -v

---

### Post by yeedyourlasthaw on 2019-06-26
> **oldfred said:**
> Did you install in UEFI boot mode?
You can use efibootmgr to remove UEFI boot entries. And remove folders in ESP - efi system partition for old installs.
Your new install should have added a new UEFI ubuntu entry, but you now may have old ones also.
Report above will show this which shows all your UEFI boot menu entries:
sudo efibootmgr -v

I did install UEFI boot mode. Excuse my lack of knowledge but I do not think I can use teh efibootmgr without access to my Ubuntu partition right?

When I go to the bios and try to boot Ubuntu, it either boots Windows 10 instead, or some old version of Fedora that I thought I removed a while back.

---

### Post by oldfred on 2019-06-26
You can run Boot-Repair from Live installer.
And you can run efibootmgr from live installer. 
Boot-Repair actually runs efbootmgr -v as part of report to see what entries you have.

---

### Post by yeedyourlasthaw on 2019-06-27
Thank you I will try this.

Just for reference, I ran sudo fdisk -l and got the following.

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1905045504 bytes, 3720792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x080ab78e

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048    1026047    1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2          1026048 1260310436 1259284389 600.5G  7 HPFS/NTFS/exFAT
/dev/sda3       1260310528 1261314047    1003520   490M 27 Hidden NTFS WinRE
/dev/sda4       1261316094 1953523711  692207618 330.1G  5 Extended
/dev/sda5  *    1261316096 1262364671    1048576   512M ef EFI (FAT-12/16/32)
/dev/sda6       1262366720 1953523711  691156992 329.6G 83 Linux

Partition 4 does not start on physical sector boundary.


Disk /dev/sdb: 28 GiB, 30016659456 bytes, 58626288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2AF2F925-7EEE-4A64-9778-035F012145EA

Device     Start    End Sectors  Size Type
/dev/sdb1   2048 411647  409600  200M EFI System


Disk /dev/sdc: 28.7 GiB, 30752636928 bytes, 60063744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xccd4ebea

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *       63 60063743 60063681 28.7G  c W95 FAT32 (LBA)

```

I will continue with the boot repair process.

---

### Post by yeedyourlasthaw on 2019-06-27
> **oldfred said:**
> You can run Boot-Repair from Live installer.
And you can run efibootmgr from live installer. 
Boot-Repair actually runs efbootmgr -v as part of report to see what entries you have.

I tried all of the above and still I cannot boot into Ubuntu.

Is it possible that having an SSD and HDD is causing this?

Here is the output to efibootmgr -v 
```
ubuntu@ubuntu:~$ efibootmgr 
BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0000,0003,000C,000E,0006,000A,0009,0008,0010,0011
Boot0000* ubuntu
Boot0003* Windows Boot Manager
Boot0006* Fedora
Boot0008* Fedora
Boot0009* UEFI OS
Boot000A* UEFI OS
Boot000C* Hard Drive 
Boot000E* UEFI OS
Boot0010* ubuntu
Boot0011* UEFI: SanDisk
ubuntu@ubuntu:~$ efibootmgr -v
BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0000,0003,000C,000E,0006,000A,0009,0008,0010,0011
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* Windows Boot Manager    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0006* Fedora    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\FEDORA\shim.efi)
Boot0008* Fedora    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\fedora\shim.efi)
Boot0009* UEFI OS    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot000A* UEFI OS    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot000C* Hard Drive     BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .D.T.0.1.A.B.A.1.0.0.V.................>..Gd-.;.A..MQ..L. . . . . . . . . . .Z. .2.5.9.V.J.X.S.N........BO..NO........O.K.I.N.G.S.T.O.N. .S.S.2.0.0.S.3.3.0.G.................>..Gd-.;.A..MQ..L.0.5.2.0.B.6.2.7.4.3.6.0.A.4.5.7. . . . ........BO..NOq.......O.S.a.n.D.i.s.k.................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.0.0.1.0.5.2.3.1.1.2.3.6.5........BO
Boot000E* UEFI OS    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0010* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0011* UEFI: SanDisk    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)/HD(1,MBR,0xccd4ebea,0x3f,0x3947fc1)..BO

```

When I went to bios I tried booting and it returns: 
[HTML]Failed to open \EFI\BOOT\grubx64.efi _ Not Found
Failed to load Image \EFI\BOOT\grubx64.efi: Not Found
start_image() returned Not Found[/HTML]

---

### Post by jeremy31 on 2019-06-27
The file should be in \EFI\ubuntu

---

### Post by yeedyourlasthaw on 2019-06-27
Thanks, but how do I find that file? From bios?

---

### Post by Dennis N on 2019-06-28
Please post boot info summary as suggested earlier in post 2. Things are not clear from the given information.
For example:
```
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
```
doesn't look like UEFI boot manager entry for a UEFI install. Maybe this is a CSM entry? Since there is no path defined to a UEFI grub boot loader as in your Fedora entries, what does this point to? Boot info summary may help us understand how this is working.

Your sda is MSDOS partitioned. You should use GPT for UEFI installations.

---

### Post by yeedyourlasthaw on 2019-06-28
> **Dennis N said:**
> Please post boot info summary as suggested earlier in post 2. Things are not clear from the given information.


Are you referring to the efibootmgr -v?

```
[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ efibootmgr -v[/FONT][/COLOR]BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0000,0003,000C,000E,0006,000A,0009,0008,0010,0011
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* Windows Boot Manager    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0006* Fedora    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\FEDORA\shim.efi)
Boot0008* Fedora    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\fedora\shim.efi)
Boot0009* UEFI OS    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot000A* UEFI OS    HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot000C* Hard Drive     BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .D.T.0.1.A.B.A.1.0.0.V.................>..Gd-.;.A..MQ..L. . . . . . . . . . .Z. .2.5.9.V.J.X.S.N........BO..NO........O.K.I.N.G.S.T.O.N. .S.S.2.0.0.S.3.3.0.G.................>..Gd-.;.A..MQ..L.0.5.2.0.B.6.2.7.4.3.6.0.A.4.5.7. . . . ........BO..NOq.......O.S.a.n.D.i.s.k.................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.0.0.1.0.5.2.3.1.1.2.3.6.5........BO
Boot000E* UEFI OS    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0010* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb) 
Boot0011* UEFI: SanDisk    PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)/HD(1,MBR,0xccd4ebea,0x3f,0x3947fc1)..BO
```

---

### Post by Dennis N on 2019-06-28
I will elaborate a bit:

See OldFred's second link in post 2:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

First, see the "Get Boot-Repair" section. You would boot into live Ubuntu session, then install Boot Repair in the live media from the PPA given at:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
First, read the top, then follow 2nd option under "Getting Boot Repair".

Once installed, start it from terminal (command: boot-repair). Only choose the 2nd option, "Create BootInfo Summary" and post the link it gives you.

The installation experts here can then analyze the problem and they can suggest what to do.

---

### Post by yeedyourlasthaw on 2019-06-28
Sorry, here is the link: [http://paste.ubuntu.com/p/9y3QygWMxM/](http://paste.ubuntu.com/p/9y3QygWMxM/)

---

### Post by yancek on 2019-06-29
Your boot repair shows Grub code in the MBR of the first disk (sda) which should not happen with an EFI install.
It shows sda4 as an Extended partition and it shows sda5 as an EFI partition.  Problem here is sda5 is a logical partition and windows needs boot files on a primary partition to boot.  Not sure how/if you can repair that.
The disk label type for your primary 1TB drive is dos, it should be gpt for an EFI install of windows.  Don't know how that happened.

It appears from this info you had a Legacy install of windows and tried to do an EFI install of Ubuntu.  The only sign of windows EFI files I can see are on the flash drive (sdb) although the efibootmgr output appears to show an entry for windows and fedora on that drive showing as gpt.

Did you actually have a functioning install (EFI) of windows/fedora and/or ubuntu?

---

### Post by Dennis N on 2019-06-29
My analysis:

sda is a 1 TB Toshiba HDD with msdos partitioning. 
Ubuntu installed sda6, with esp on sda5. 

sdb is a 30 GB Kingston SSD with gpt partitioning.
Only contains an EFI system partition with Windows boot manager.

sdc is a usb drive

sda5 has the correct files to boot Ubuntu, but there is no link to this in the UEFI boot manager because of incorrect entry (previously noted in post #9) so computer fails to boot to grub menu:
```
Boot0000* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
```
Windows was hibernated when boot repair ran so would not mount. It should be shut down completely when installing Ubuntu.

Running recommended repair should create this corrected entry into UEFI boot manager:
```
Boot0000* ubuntu	HD(5,MBR,0x80ab78e,0x0,0x0)/File(EFIubuntushimx64.efi)
```
Computer should work.

Note: you have an unusual UEFI install on an msdos disk with OS and EFI system partitions on logical partitions (sda5 and sda6). Apparently you had this setup previously so this is doable, but it's the first one I have seen.

---

### Post by yeedyourlasthaw on 2019-06-29
> **yancek said:**
> Did you actually have a functioning install (EFI) of windows/fedora and/or ubuntu?

Yeah, I had a working install of Win10/Ubuntu 16.04 before I messed it all up.

One thing to note is that I bought this PC in Japan where they had pre installed Windows 10, all I did was add Ubuntu.

---

### Post by yeedyourlasthaw on 2019-06-29
> Windows was hibernated when boot repair ran so would not mount. It should be shut down completely when installing Ubuntu.

Running recommended repair should create this corrected entry into UEFI boot manager

I have no idea how Windows was hibernated whilst I was using Ubuntu live. My process was to restart the computer and then boot ubuntu live.
I'll try the PC down this time, power n and go straight to the Ubuntu live boot, then run the boot-repair again, and return with an update.

Thanks

---

### Post by yancek on 2019-06-29
Turning off hibernation in windows 10 is explained at the microsoft site below.  Note that many windows updates will turn it back on again.  You will not be asked if you want this nor will you be informed.

[https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running](https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running)

---

### Post by yeedyourlasthaw on 2019-06-29
Thanks for all the info!

So I ran the boot-repair again, rebooted the PC and it took me straight to Windows 10.
Should I have to re-arrange my boot order? I wish I could get rid of all the useless stuff such as Fedora and the non working boots.

I also have a new link: [http://paste.ubuntu.com/p/SnPrm3ngG2/](http://paste.ubuntu.com/p/SnPrm3ngG2/)

Thanks

---

### Post by Dennis N on 2019-06-30
On the first bootinfo report (dated 27 Jun), I assume lines 993-1004 show what the boot menu entries were after the suggested boot repair, while 303-316 show the boot menu entries before the repair. Anyone disagree with that?

On the second bootinfo report (dated 29 Jun), lines 755-768, that I assume show the current state, have the old incorrect Ubuntu entry again (as in post #9). It should have changed.

To be sure on this, check what the ubuntu entry is  now (after your repair) from the live media, using **sudo efibootmgr -v**

(If you see the incorrect entry, I would run the boot repair again, but **before** rebooting the computer, run sudo efibootmgr -v again see what (if anything) got changed by boot repair.)

---

### Post by oldfred on 2019-06-30
If it resets again, you may have one of the systems that only lets you change boot order inside UEFI.
Many with HP complained about that issue. Some have reported that UEFI updates have resolved that issue.
So if Boot-Repair or grub install which both use efibootmgr, do not work, try changing within your UEFI on the settings/tab that are for boot entries, not just the boot menu.

But if you have not updated UEFI from vendor you probably should do that also as other issues related to various cpu related virus have needed UEFI updates, Windows updates & Linux updates.

---

### Post by yeedyourlasthaw on 2019-07-15
Sorry for the delay, just got back from paternity leave.
So I ran the boot-repair again and before restarting I ran sudo efibootmgr -v. The results are as follows:

```
ubuntu@ubuntu:~$ sudo efibootmgr -vBootCurrent: 0013
Timeout: 1 seconds
BootOrder: 0000,0003,000C,000E,0006,000A,0009,0008,0013
Boot0000* ubuntu	HD(5,MBR,0x80ab78e,0x0,0x0)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* Windows Boot Manager	HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0006* Fedora	HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\FEDORA\shim.efi)
Boot0008* Fedora	HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\fedora\shim.efi)
Boot0009* UEFI OS	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot000A* UEFI OS	HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot000C* Hard Drive 	BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .D.T.0.1.A.B.A.1.0.0.V.................>..Gd-.;.A..MQ..L. . . . . . . . . . .Z. .2.5.9.V.J.X.S.N........BO..NO........O.K.I.N.G.S.T.O.N. .S.S.2.0.0.S.3.3.0.G.................>..Gd-.;.A..MQ..L.0.5.2.0.B.6.2.7.4.3.6.0.A.4.5.7. . . . ........BO..NOq.......O.S.a.n.D.i.s.k.................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.0.0.1.0.5.2.3.1.1.2.3.6.5........BO
Boot000E* UEFI OS	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0013* UEFI: SanDisk	PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)/HD(1,MBR,0xccd4ebea,0x3f,0x3947fc1)..BO
Boot0014  Could not parse device path: No such file or directory
```

And the generated link: [http://paste.ubuntu.com/p/VXgvpzB4nq/](http://paste.ubuntu.com/p/VXgvpzB4nq/)

Thanks

---

### Post by oldfred on 2019-07-15
Again very non-standard configuration.

Windows only boots in BIOS mode from MBR (msdos) partitioned drives. But you have a Windows UEFI boot in the sdb drive's ESP. Not sure if then it is possible to boot Windows from a gpt drive but using MBR drive for most of Windows. (Ubuntu can do that, but not recommended).

The Fedora & Windows are/were using the ESP on sdb for UEFI boot. The UEFI entry uses GUID that matches GUID of sdb1.
But Ubuntu install now uses sda5, which is new and only has Ubuntu entries.

Normally on MBR partitioned drives Windows has boot loader in MBR and Windows sda1 partition has boot files and has boot flag. 
But gparted uses boot flag to know which partition is ESP, so boot flag for Windows BIOS boot was moved to sda5. If you were booting in BIOS mode from sda?

Do you have good backups. I would make sure you do that before any other changes.

You can remove the /EFI/fedora folder in sda1's ESP. You may want to also remove some of the older Boot-Repair logs before ESP fills up (only showed 22% used so far).

And you can remove the Fedora UEFI boot entries with efibootmgr.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

I do not think that works if booted in BIOS mode.

---

### Post by yeedyourlasthaw on 2019-07-15
> **oldfred said:**
> 

Windows only boots in BIOS mode from MBR (msdos) partitioned drives. But you have a Windows UEFI boot in the sdb drive's ESP. Not sure if then it is possible to boot Windows from a gpt drive but using MBR drive for most of Windows. (Ubuntu can do that, but not recommended).

The Fedora & Windows are/were using the ESP on sdb for UEFI boot. The UEFI entry uses GUID that matches GUID of sdb1.
But Ubuntu install now uses sda5, which is new and only has Ubuntu entries.

Normally on MBR partitioned drives Windows has boot loader in MBR and Windows sda1 partition has boot files and has boot flag. 
But gparted uses boot flag to know which partition is ESP, so boot flag for Windows BIOS boot was moved to sda5. If you were booting in BIOS mode from sda?


If I understand correctly, I have Windows on my SSD and when using auto partition for Ubuntu, it did not go on the same disk?
So I can try manually partitioning Ubuntu.

Also thank you for the info on how to remove the old UEFI boot entries.

---

### Post by oldfred on 2019-07-15
You have what looks like full BIOS install of Windows in sda1 & sda2. And the two partitions are typical BIOS configuration, not the newer UEFI configuration.

And you have an UEFI install of Ubuntu also on sda using a new ESP -efi system partition sda5.
And sda is MBR(msdos), but if Windows was BIOS then it also was MBR. 

But then I do not know how you got Windows UEFI boot loader files into sdb1 and UEFI boot entry?

If you want to boot in BIOS mode, you can install a Windows boot loader to MBR of sda using Boot-Repair in BIOS mode & its advanced options or a Windows repair disk. But first must move boot flag from sda5 to sda1 for Windows to boot in BIOS mode. But then Ubuntu will not boot in UEFI mode.

You can also then install grub in UEFI mode using the ESP on sdb. But mixed BIOS & UEFI boot is not really recommended. Better to have all systems BIOS/MBR or all systems UEFI/gpt. 
If you do want Ubuntu in BIOS mode, use Boot-Repair to install grub to sdb, but not auto fix as that will overwrite the Windows BIOS boot loader. And with grub in sdb, you can boot both Windows & Ubuntu if you set UEFI/BIOS to boot sdb. And when Windows breaks and grub does not boot it, you can directly boot sda to get into Windows.

But that is not using sdb for anything but BIOS boot loader or wasting 30GB which is also faster SSD?
I would reconfigure to put just / (root) on sdb and have either /home or data partitions on sda. 

Ubuntu's installer defaults to sda.
So with BIOS you can only use Something Else to specify where to install grub. And UEFI install still has selection, but it does not work with UEFI. Ubiquity installer (not really grub) only installs grub to first ESP or usually the ESP on sda or first NVMe drive. There are workaounds.

---

### Post by yeedyourlasthaw on 2019-07-15
So I have removed all the old entries thanks to you! 

I will remove my current Ubuntu partition and install in BIOS mode.

I used Gparted to move the bootflag, and I THINK that I installed [COLOR=#000000]Windows boot loader to MBR of sda using Boot-Repair.

[/COLOR]http://paste.ubuntu.com/p/jTnfpSZctC/

```
ubuntu@ubuntu:~$ sudo efibootmgr -vBootCurrent: 0015
Timeout: 1 seconds
BootOrder: 0000,0003,000C,0014,0015
Boot0000* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* Windows Boot Manager	HD(1,GPT,ced22be2-d879-482c-8267-c3a6e955d146,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot000C* Hard Drive 	BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .D.T.0.1.A.B.A.1.0.0.V.................>..Gd-.;.A..MQ..L. . . . . . . . . . .Z. .2.5.9.V.J.X.S.N........BO..NO........O.K.I.N.G.S.T.O.N. .S.S.2.0.0.S.3.3.0.G.................>..Gd-.;.A..MQ..L.0.5.2.0.B.6.2.7.4.3.6.0.A.4.5.7. . . . ........BO..NOq.......O.S.a.n.D.i.s.k.................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.0.0.1.0.5.2.3.1.1.2.3.6.5........BO
Boot0014* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0015* UEFI: SanDisk	PciRoot(0x0)/Pci(0x14,0x0)/USB(15,0)/HD(1,MBR,0xccd4ebea,0x3f,0x3947fc1)..BO
```

---

### Post by oldfred on 2019-07-15
I would not expect UEFI entry for Windows to work, but the hard drive entry then should boot in BIOS mode.

You do not have to totally reinstall Ubuntu. The real difference between UEFI & BIOS is just the grub2 boot loader and a bit of configuration that reinstalling grub takes care of.
From Boot-Repair's advanced mode (in BIOS mode), you can select an install and select a drive to install grub into. You select sdb to install grub to MBR of sdb.

---

