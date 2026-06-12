---
title: "Dual Boot Issues, Used Boot-repair, Have pastebin take a look?!?!"
date: 2018-09-07
forum: Installation &amp; Upgrades
---

### Post by jsonde on 2018-09-07
Hello, I cant seem to figure this out at all. Everything was working fine until I tried booting into ubuntu and got an error. I then tried to boot back into windows 10 and that wouldnt work either. Error no device grub rescue kept coming up. Made a Live usb with an updated ubuntu on it and used the boot-repair. It mentioned it made some changes but after restarting I get  Windows boot manager Windows failed to start. Status 0xc000000f. Any suggestions would be helpful. The pastebin url is below. Thank you
[http://paste.ubuntu.com/p/cjmz89Jvsr/](http://paste.ubuntu.com/p/cjmz89Jvsr/)

---

### Post by westie457 on 2018-09-08
Hello jsonde
Looking at your report your first Hard drive has an issue that should never happen and I have never seen a situation where all partitions end after the last sector of the hard drive. This might be caused by the 'Unknown MBR' message, I am not sure and it might something more serious.

We will attempt to fix Windows first.
Do you have Windows install media, either USB or DVD or can you access the machines recovery software?
If it is only the first one boot from that and at the Welcome screen click on 'repair your computer', go to 'Advanced' and open a command prompt.
In the command prompt type and run ```
sfc /scannow
```wait for this to do what it has to and reboot when finished..
If this is successful and you can start Windows we can then look at fixing any other problems.

The above suggestion came from here. [https://malwaretips.com/threads/help-unknown-mbr-code-virus.69236/](https://malwaretips.com/threads/help-unknown-mbr-code-virus.69236/)

Is Windows running okay? 
Now boot your Ubuntu Live and post another report without attempting any repairs.
Further info will be provided as necessary.

Good luck.

---

### Post by yancek on 2018-09-08
It isn't really clear to me whether your Ubuntu ever worked/booted, did it?  You have windows boot code in the MBR of two drives (sda, sdb) and sdb appears to be the drive on which you installed or tried to install Ubuntu (sdb3).  If this is a new install it didn't work as most of the files one would see after running boot repair are not shown on sdb3.  If Ubuntu was working and installed, some major change must have been made.  Note the message about windows being in an unsafe state.  You need hibernation/fastboot off otherwise even if your Ubuntu was working you would not get a boot entry for windows.  A linux system will not mount a partition which is hibernated.

Some pretty unusual message so post back after making the changes suggested above.

---

### Post by jsonde on 2018-09-09
Thank you for the reply, I attempted to run sfc /scannow and got the  following response " There is a system repair pending which requires a  reboot to complete. Restart windows and run sfc again." Ive tried this  twice and got the same response. I had dual boot setup successful for  ubuntu and windows 10. I also had a partition for windows 7 setup as  well but I dont think I got that working and that might of been the  issue. In grub there was several options for dualbooting. ubuntu/windows  10/windows7/memtest and such. Ive tried a couple of suggestion to fix  the problem but im now thinking i screwed something up :/ Should my main  focus first to fix mbr for windows and then work on grub bootloader?  Thanks again for the help.

---

### Post by oldfred on 2018-09-10
You have a newer UEFI hardware based system.
But Windows & Ubuntu in stalled in the now 35 year old BIOS based configuration which requires MBR partitions.
But you booted Boot-Repair in UEFI boot mode.

Your sdb drive looks mostly correct. Windows hibernation may be the issue there. You have to restore Windows boot loader to sdb and set BIOS to boot sdb.
You may need f8 then to get into Windows repair console or your Windows repair flash drive or installer with repair console.
Windows 10 will turn fast start up back on with updates, and then you cannot boot Windows from grub menu. And with BIOS the only way to boot Windows is then to temporarily restore a Windwos boot loader, fix Windows and then restore grub boot loader manually or with Boot-Repair. 
With UEFI installs, you can always directly boot Windows from UEFI to possibly make fixes, and then boot Ubuntu/grub from UEFI with out having to re-install boot loaders.
Note that Windows 10 hibernation also has to be off to use another install with Windows 7 as it would then be hibernated.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
But sda is show major partition issues. It probably is random data written into the MBR part of the drive which then partition tools try to see as partitions but it does not translate. 
You may be able to use testdisk on sda, to see if it can find old partition data. It usually finds all old partitions, so if changed multiple times you have to select correct set of partitions that do not overlap.

Newer UEFI systems use gpt partitioning that has a backup at end of drive, so often can be directly repaired with gdisk.

 Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by jsonde on 2018-09-15
I did recently have to install a new motherboard from an asus m5a97 to gigabyte 970A because my liquid cooling cpu fan leaked all on the motherboard, psu, and gpu. So apparently I grub got screwed up once I tried to load into ubuntu because of the mobo switch? Which in turn I messed things up even more trying to fix grub from there. I will go through the steps As you mentioned and see what I can do. Will these steps wipe my windows 10?? I dont mind ubuntu being gone but its windows that is of importance.

---

### Post by jsonde on 2018-09-15
Things done

-Turned FastStartup off
-In the process of getting a usb flashdrive to run testdisk.

---

### Post by oldfred on 2018-09-15
With newer UEFI motherboards you need several UEFI settings & often boot parameters.

Some other similar model motherboards:
 Ryzen + Gigabyte installation problem Newer kernels & IOMMU
[https://ubuntuforums.org/showthread.php?t=2362773](https://ubuntuforums.org/showthread.php?t=2362773)
Some Gigabyte boards need acpi=off boot parameter also
Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by jsonde on 2018-09-26
Running Testdisk as we speak and ill try to post a log file.

---

### Post by jsonde on 2018-09-27
I got a Log file, do you mind checking it out to see any discrepancies? What would be the best way to restore windows bootloader and set it to sdb and bios? Thanks for the input. 

[https://www.dropbox.com/s/u8nsozgdez66u0y/Test.log.LOG?dl=0](https://www.dropbox.com/s/u8nsozgdez66u0y/Test.log.LOG?dl=0)

---

### Post by oldfred on 2018-09-27
I have never looked at a testdisk log file. But it looks like it was showing NTFS partitions. 
If that is the case you need to write that.
Or if you had converted drive to dynamic partition, then you need to use Windows repair tools to try to repair partition table.

You should be able to put a Windows type boot loader in the MBR of sdb, if you have a bootable Windows on sdb. But Boot-Repair report shows a Windows boot loader is already there.

---

