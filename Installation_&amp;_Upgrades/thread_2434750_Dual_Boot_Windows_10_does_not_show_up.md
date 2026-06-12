---
title: "Dual Boot: Windows 10 does not show up"
date: 2020-01-10
forum: Installation &amp; Upgrades
---

### Post by praesodym on 2020-01-10
Hi,

I know there are several posts about this topic but no one helped me. 
I bought a new 2TB HDD and set it up yesterday using Windows 10: GPT, 1TB Windows stuff (there are no files till now) and 1 TB for Ubuntu installation. 
At first I installed Ubuntu in EFI mode but than saw that my Windows is in Legacy mode and I thought that this was the reason I couldn't see Windows in GRUB. 
I installed Ubuntu again in BIOS mode (?). But I still can't see my Windows in GRUB. 
Strangely enough I can see two old Windows installations on my other HDDs which I don't boot anymore. 
```
os-prober
``` and ```
update grub
``` just show my old Windows installations. And adding an entry manually in ```
/etc/grub.d/40_custom
``` results in a GRUB entry but says something like: 
> device not found, bootmgr not found.
Fast boot is deactivated in Windows and as far as I see my SSD is mounted in Ubuntu. 
If you need more information tell me.

---

### Post by P-I H on 2020-01-10
I think it's easier to install both Ubuntu and Windows in EFI mode.
When you start with Ubuntu an EFI file will be created and at the installation of Window, Window's EFI boot information will be stored in the same EFI file.

---

### Post by praesodym on 2020-01-10
Hm I don't want to reinstall Windows (not now at least).
I ran the boot repair tool and got the following: [https://paste.ubuntu.com/p/w5wY7pb45B/](https://paste.ubuntu.com/p/w5wY7pb45B/) 
Here it even says that  
" => Windows 7/8/2012 is installed in the MBR of /dev/sdc."

---

### Post by westie457 on 2020-01-10
The Windows installation on the GPT partition-table drive needs a small 'EFI' partition to boot from.

This procedure will probably be the most helpful without the need to reinstall Windows. [https://www.tenforums.com/installation-upgrade/52837-moving-recreating-efi-partition.html](https://www.tenforums.com/installation-upgrade/52837-moving-recreating-efi-partition.html)

After this use 'BootRepair' in 'Advanced'mode to reinstall Grub to the EFI partition and finally in the BIOS/UEFI settings pages set this hard drive as the first to boot and set UEFI only (no legacy or CSM)

---

### Post by dragonfly41 on 2020-01-10
What is output of the command ..

```
efibootmgr o
```

(to view all options use efibootmgr --help)

---

### Post by praesodym on 2020-01-10
@dragonfly41 
```
EFI variables are not supported on this system.

```

And to be clear: I still can boot my Windows from BIOS.

---

### Post by oldfred on 2020-01-10
With Multiple installs and drives, do not run Boot-Repair's autofix. It will install grub to the MBR of every drive. And if you have Windows on another drive, you want to keep the Windows boot loader on that drive. You can use Boot-Repair's advanced options where you choose MBR & system to use.

Windows 10 has fast start up which is just a hibernation whether UEFI or BIOS install. And it sets hibernation flag on all NTFS partitions. That may prevent boot of other Windows also, but Linux NTFS driver will not mount NTFS with hibernation flag set to prevent damage/missing files. If you force write from Linux into hibernated NTFS, when Windows reboots it restores old info  & new data is not there.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If installing Ubuntu/grub in BIOS mode to gpt drive, you need a 1 or 2MB unformatted partition with the bios_grub flag, otherwise grub does not correctly install It can be anywhere within the first 2TB of a gpt drive. Boot-Repair comment on this.
You can use gparted, shrink any of your partitions by 3 or 4GB and add a new 1 GB unformatted partition with bios_grub.
Then use Boot-Repair & its advanced options to reinstall grub to MBR. Choose your Ubuntu install and Ubuntu drive to update just that MBR.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

While you have old installs in BIOS/MBR mode, you have new UEFI hardware.
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI. 
Ubuntu does not care about partitioning, but really should only use gpt for UEFI boot and if only Ubuntu on drive you can use new gpt whether UEFI or BIOS.

Microsoft has required vendors to install Windows 8 and then 10 in UEFI/gpt mode since Windows 8 released in 2012. Users could install in 35 year old BIOS/MBR configuration as large companies with many systems did not necessarily want to do complete conversion at once. So wanted newer hardware but be able (back in 2012) install Windows in BIOS mode.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by dragonfly41 on 2020-01-10
Here is my case study.

I will walk through the process I have recently gone through - and I am still trying to understand the mysteries of multi-booting and menu changing. There are many, many links to posts and articles.

I have a host Dell PC with Windows 10.
I shrunk the internal 1 TB drive to add Ubuntu 16.04 (about a year ago, predating 18.04 stable release). 
Added an old drive in USB container to migrate from internal 16.04 to external 18.04.
But this external Ubuntu was created as MBR not GPT (before I began to understood the difference).
Nevertheless they run together with the PC set to UEFI.
I had UEFI enabled and Secure Boot disabled.
This triple boot worked nicely from grub menu.
I did learn that Windows upgrades can screw up multi-boot grub settings.
My old external HDD was chuntering and I added an external SSD 1TB sitting in a two bay docking station connected via USB 3.0.
I used LiveUSB and GParted to partition external SSD.
I read that 10% of SSD should be left unallocated.
I added an NFTS partition for sharing with Windows 10.
The final structure looks like Gparted snapshot at foot of this post. 

Note the EFI partition.  
The idea was to boot up this SSD even if internal (Windows) drive is removed.
In fact I tested this by disconnecting power cable to internal drive and booting up the external SSD.

Now the EFI boot options are still a dark art to me. 
It is still hit and miss whether I can boot up my SSD from a verbose grub menu.
I turn to efibootmgr to setup boot options.
I refer to post#14 here by OldFred ..
[https://ubuntuforums.org/showthread.php?t=2434378&page=2](https://ubuntuforums.org/showthread.php?t=2434378&page=2)

The command line I found useful, and pulling me out of a hole,  was ..

[COLOR=#000000]sudo [/COLOR][COLOR=#000000]efibootmgr[/COLOR][COLOR=#000000] -c -g -w -L "[/COLOR][COLOR=#000000]ubuntu[/COLOR][COLOR=#000000]" -l '\[/COLOR][COLOR=#000000]EFI[/COLOR][COLOR=#000000]\[/COLOR][COLOR=#000000]ubuntu[/COLOR][COLOR=#000000]\[/COLOR][COLOR=#000000]shimx64[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]efi[/COLOR][COLOR=#000000]' -d /[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]sdb[/COLOR][COLOR=#000000] -p 1[/COLOR]

Run efibootgr --help to understand the command options.

Now instead of using Windows to setup your EFI partition in the SSD I used a LiveUSB and Gparted.

The EFI partition in external USB is partition /dev/sdb1.
I added boot flags: boot, esp

Thus the efibootmgr command becomes this ..

[COLOR=#000000]sudo [/COLOR][COLOR=#000000]efibootmgr[/COLOR][COLOR=#000000] -c -g -w -L "Ubuntu 18.04 [/COLOR][COLOR=#000000]SSD[/COLOR][COLOR=#000000]" -l '\[/COLOR][COLOR=#000000]EFI[/COLOR][COLOR=#000000]\[/COLOR][COLOR=#000000]ubuntu[/COLOR][COLOR=#000000]\[/COLOR][COLOR=#000000]shimx64[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]efi[/COLOR][COLOR=#000000]' -d /[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]sdb[/COLOR][COLOR=#000000] -p 1[/COLOR]

The menu name is &#8220;Ubuntu 18.04 SSD&#8221;
The "\EFI\ubuntu\shimx64.efi" file is placed  in /dev/sdb1 (the EFI partition created)

This new entry is added to the Boot menu.

Even if the grub menu to the external SSD does not work (device not found) I just run that efibootmgr command again to restore and I reboot and use &#8220;One Time Boot Option&#8221; (F12) to select that entry.  One day I might learn how to purge the entire grub menu (which also refers to Dell recovery) and start with a leaner menu.

I think that this whole multi-booting process might benefit from an automation script.

---

### Post by oldfred on 2020-01-10
UEFI boot entries for an external drive will be deleted or changed to default if drive is disconnected.
UEFI normally boots external devices from /EFI/Boot/bootx64.efi. 

Old versions of grub did not create bootx64.efi, but users manually copied grubx64.efi or shimx64.efi to bootx64.efi. This full version of grub or shim also needs the /EFI/ubuntu folder as it uses /EFI/ubuntu/grub.cfg to boot. 

Boot-Repair & newer versions of grub create /EFI/Boot/bootx64.efi as fallback or drive boot entry, so external drives can boot. If installing grub you need to use the --removeable option. If installing to a flash drive without Ubuntu, you can install grub and add your own grub.cfg to loop mount ISO, or boot other installs as emergency boot. 

But on a normal install using Ubiquity, it only installs grub to first drive, usually sda or first NVMe drive. This is an Ubiquity issue, not grub issue.
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

### Post by dragonfly41 on 2020-01-10
@OldFred
Thanks for adding to the corpus.
This[ reference to Ubiquity bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379") does explain some of the issues I have experienced.
I am surprised that efibootmgr is not mentioned more as a means of forcing boot options.

---

