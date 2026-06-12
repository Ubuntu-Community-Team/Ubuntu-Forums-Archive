---
title: "Windows 10 dual boot - tried several times - Need a plan"
date: 2019-10-05
forum: Installation &amp; Upgrades
---

### Post by yaminb on 2019-10-05
Hi all,

I've tried a few times to install Ubuntu and Debian on my PC. 
It has Windows 10 installed.
Every time, I just can't get it to boot and it always destroys even my Windows 10 boot. I always end up having to use a Windows recovery to fix the Windows boot.

I was hoping someone could help me plan through it. 

My current HD configuration

[IMG]https://ibb.co/BZRNKkB[/IMG]
(trouble uploading/linking image... typing it out)

SYSTEM RESERVED: 300 MB (active, system)
C: 1.3 TB NTFS (Windows drive) Primary (boot, recovery)
E: 250 MB FAT32 (attempted EFI partition) Primary (active)
*: 500 GB EXT3 (attempted Ubuntu partition... ext 4) Logical
*: 500 MB NTFS Primary (Recovery) 

The C: Drive is of course my main windows drive.
the E:, Ext3/4 drives were created when I've been trying to install Ubuntu. I don't mind wiping them out or restarting.
The E: Drive probably shouldn't be there. I just created it in a wild ditch attempt to create an EFI partition.


I should mention that I do have RAID 1 enabled (motherboard based) on as it's dual 2 TB drives. I'm not sure if that's a complicating factor.
My motherboard is [http://www.asrock.com/mb/Intel/H87M-ITX/?cat=Download&os=Win864](http://www.asrock.com/mb/Intel/H87M-ITX/?cat=Download&os=Win864)

Things I've learned already.
[LIST=1]
[*]Getting into the boot menu/bios is trickier than it used to be. My mouse/keyboard are wired USB. I have turned off fast-boot, but it still doesn't solve it
[LIST=1]
[*]What I've had to do is reboot, then use the 'reset' button on my PC. Not the power button. Then when it reboots, it looks like it has knowledge of the USB keyboard/mouse and I can enter the menus. An annoyance, but it works 
[/LIST]
  
[*]I've tried the boot-repair program (yannubuntu) from the live Ubuntu usb key, but it always fails
[LIST=1]
[*]Please enable a repository containing the [linux-generic] packages in the software sources of Ubuntu 18.04 LTS... 
[*]Unfortunately, I don't have the paste-bin saved of it. I was just working off the live ubuntu and forgot to save the link. Is there a way to search for  it based on day/time? 
[/LIST]
   
[/LIST]

I do have a linux VM i have on my windows (Kali based) if you need me to run any linux commands for more information.

Thanks for any help here,

Yamin

---

### Post by CatKiller on 2019-10-05
> **yaminb said:**
> 
[LIST=1]
[*]Getting into the boot menu/bios is trickier than it used to be. My mouse/keyboard are wired USB. I have turned off fast-boot, but it still doesn't solve it
[LIST=1]
[*]What I've had to do is reboot, then use the 'reset' button on my PC. Not the power button. Then when it reboots, it looks like it has knowledge of the USB keyboard/mouse and I can enter the menus. An annoyance, but it works 
[/LIST]
[/LIST]

You'll likely have a BIOS option - probably called something like "Legacy USB" - that will provide access to USB devices before an OS has loaded.

---

### Post by oldfred on 2019-10-05
While you mention ESP - efi system partition, your Windows partitions and mention of logical partitions implies BIOS/MBR.

Windows only boots in BIOS mode from MBR partitioned drives.
Windows only boots in UEFI mode from gpt partitioned drives.
Ubuntu will let you install in either boot mode from either partitioning, but really should not. You need to be sure to use same boot mode as Windows. 

You cannot have Ubuntu in UEFI mode on one BIOS/MBR drive with Windows as only one boot flag is allowed per drive. Windows requires boot flag on its NTFS partition with boot files in BIOS mode and UEFI requires boot flag on ESP - efi system partition. 

RAID is a major complication. Many with RAID 1 just break the RAID and install Ubuntu on one drive & Windows on the other.
If the RAID is really Intel SRT, that is only used to speed Windows boot and needs to be turned off. You then install AHCI drivers into Windows and change BIOS setting from RAID/Intel RST to AHCI.

Whatever you do be sure to have good backups.

---

### Post by yaminb on 2019-10-27
Just a FYI on a resolution to this.

I decided to just reinstall everything fresh.
I got rid of RAID
1 HD dedicated to Windows 10
1 HD dedicated to Ubuntu

Worked surprisingly well actually. Most of documents were stored on Onedrive anyways, which I managed to get synced onto Ubuntu as well.
Kind of surprising how much is stored in the cloud these days. I didn't lose anything.
For everything else, I have my NAS which backed up the rest.

Even some of my steam games worked straight.

---

