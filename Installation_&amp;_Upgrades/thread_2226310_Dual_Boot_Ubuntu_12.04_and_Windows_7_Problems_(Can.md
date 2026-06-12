---
title: "Dual Boot Ubuntu 12.04 and Windows 7 Problems (Cannot start either now)"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by Jeffrey_Shek on 2014-05-26
[HR][/HR]Running into a terrible problem where I have Windows 7 and then tried reinstalling Ubuntu. 

Bought an additional hard drive to put Ubuntu on it. Installed Ubuntu from a disc, and now I can no longer get into Windows 7.

I tried using Boot-Repair, it said that my boot was in Legacy mode  (which ... didn't seem like it, since my BIOS is on EFI), but using  Boot-Repair Ubuntu no longer loads either (Windows still load either).

I can get into Try Ubuntu with the setup USB, and I do have Windows 7  discs, but I don't want to wipe my Windows 7 unless it's last resort.

[http://paste.ubuntu.com/7522692/](http://paste.ubuntu.com/7522692/)

To give some backdrop on my current setup, I have 2 128 SSDs in RAID 0  for my Windows 7 setup (is this the problem?), 1 512 GB recently bought  for the Ubuntu, and a 2 TB HD designed for media.

I've googled in the forums a bit, and someones recommended to boot into  Windows Console and use 'fixmbr' to give it a shot for another type of  situation. Is that advisable here? I'm just trying to avoid cornering  myself into a situation where I mess up things even more.

Thanks!

---

### Post by oldfred on 2014-05-26
Yes.
The standard desktop installer does not install grub correctly when RAID is involved. 
If you unplugged all the other drives it should install without issue. But install in UEFI mode not BIOS.

The fixMBR is to restore the Windows boot loader to the MBR of the Windows boot drive.

If you have a separate drive for Ubuntu you need to unplug other drives (safest if first install) or use Something else to manually partition drive, and ensure that you install grub2 boot loader to the MBR of that drive only.

It also looks like your Windows is in UEFI boot mode with gpt partitioning inside of the RAID. You need to boot Ubuntu installer in UEFI mode so it will install in UEFI mode also. Otherwise the only way to boot is from UEFI menu and you may have to turn on/off UEFI or turn on/off BIOS/CSM boot mode to boot system installed in that mode. Some do auto-switch and let you choose from one time boot key.

Usually if you have gpt inside the RAID, you also have gpt outside or to support the RAID. You drives are showing as MBR(msdos)??

And it looks like now you have Ubuntu booting in UEFI mode from the efi partition with UUID - 28D1-CFF1 which is inside your RAID, but you have Ubuntu in MBR partitions. I have seen one or two others with something similar. UEFI only boots from gpt partitioned drives, but I guess the / (root) partition can be on a MBR drive. Best not to do that.
You really want the Ubuntu drive to be able to boot as if it is the only drive in the system. 

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

I think these are now older, but the issues are still the same.
**Two Drive UEFI installs**
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

If you use Something else instead of disconnectiong drives, you should get screens like this. Note combo box at bottom. Mine still shows sda, but you must change to correct drive where you are installing Ubuntu.

---

### Post by Jeffrey_Shek on 2014-05-26
Thank you! After your instructions ... I unplugged my hard drive with Ubuntu installed, I could get into the Windows environment! I followed your advice about unplugging everything prior to install Ubuntu, so now I have both environments (up and running). 

Slight annoyance as to get to each environment, I actually boot into my EFI BIOS and then select which one I want (windows or ubuntu).

Would using boot-loader now allow for ubuntu environment to see windows and then let me pick when my computer starts, versus that of booting into my bios and selecting each time?

---

### Post by oldfred on 2014-05-26
If you have Ubuntu in UEFI mode, you should be able to add Windows to grub menu.

But you may need to reinstall RAID drivers. Not sure which for your version of RAID.

I think yours is dmraid.

 sudo apt-get install mdadm
or:
sudo apt-get install dmraid
Then mount Windows partition in Nautilus or manually and run this:
sudo update-grub

Normally you just need to run the update to add Windows to menu, but it may need the driver and mounting to correctly see it.

---

### Post by Jeffrey_Shek on 2014-05-26
Thank you so much oldfred. I guess I have a thick skull, but now I finally understand why it wasn't working before (didn't understand that RAID drivers could be missing, which explains why it didn't autodetect Windows on the first install)!

---

### Post by oldfred on 2014-05-26
So did that work. If so you can change to Solved.

With 12.04 they had the alternative text based installer for RAID & LVM as they are not common with desktops. But they did away with that installer and said they would add it to the standard gui desktop installer. The installer now has LVM drivers and may have RAID drivers, but if you do not install using those it uninstalls those drivers.

---

