---
title: "Need partition advice for dual boot on SSD"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by Claire on 2012-07-21
Thought I would query for a little bit of advice here.  Just got a new laptop (Vizio CT15-A2), and I'm hoping to set up a dual boot with Windows 7 and Ubuntu (or Linux Mint).  I've been using Ubuntu for about 6 years now and have set up a dual boot in the past, but I'm not sure if best practice has changed, especially in light of the SSD (256GB).  This laptop came with Windows 7 ("Signature" which is supposedly low on bloatware, though somehow the installation already takes up 20+ GB) installed, and ideally I don't want to deal with the hassle of reinstallation.

The current partitions are:
600MB (labeled as "Active, Recovery Partition")
224.17 GB NTFS (Windows installation - currently 28GB used)
11.72 GB (labeled as "Recovery Partition")
2 GB (labeled as "Hibernation Partition")

I'm thinking about blowing away the 11 GB recovery partition and the hibernation partition, shrinking the Windows installation, then adding an Ubuntu partition and a data partition.  I have a couple questions though:

1) Is it bad to get rid of the recovery and/or hibernation partitions?
2) Why does Windows take up so much space?  How much space should I allocate for it to allow for any extra program files?
3) How much space is recommended for a modern installation of Ubuntu?  Is 10 - 15 GB sufficient?
4) I'm thinking I should avoid creating a swap partition in order to maximize the lifespan of the SSD - is this the correct way to go about it?  Is there anything else I should be doing that's SSD specific?
5) I'm not a huge fan of Unity so I might be switching over to Linux Mint with Cinnamon - is there anything that might be different with the partitioning and installation between Ubuntu and Linux Mint?

Thanks for any help!

---

### Post by oldfred on 2012-07-21
I consider partitioning a personal decision as it depends on how you will want to use system. My own optimal/ perfect partitioning is not so good after a year or two as I have changed what I do. But I will make a few suggestions, other should have different opinions.

My goal has always been reliability, so I put a full install of Ubuntu on every hard drive (ok my old drive still has just XP on it). But I want each drive to fully boot even if another drive dies or has major issues. I then may have data partitions on other drives or backups, so most data is in more than one place. I do like to have Windows separated from system & data also. You then can share any data in a NTFS shared partition with both Ubuntu & Windows.

With my new SSD as a boot drive I kept the full system in a 25GB / partition including /home but no swap. I have 4GB of RAM and almost never use swap. System does find swap on rotating drives so that does get mounted, but rarely used. My /home only has my hidden configuration files & folders,  any data is moved to a data partition.

Windows NTFS partitions seem to work best with 30% free space & slow at 20% free, so depending on what you plan to install keep space available.

As a new system is it still BIOS/mbr or the newer UEFI/gpt? You do not mention the first partition as efi which would be the case if UEFI, so it probably is BIOS. But normally the first partition (active or boot flag) is 100 or 200MB and just has Windows boot files and Windows recovery/repair program, you have 600MB?

I do not know about Windows now doing a separate hibernation partition? I do know the new Windows 8 defaults to hibernation on shutdown and can cause dual boot issues.

Most suggest making the recovery DVDs as that is the image of drive as purchased. Mostly only if you later sell system and user wants only Windows and you want to reimage.

Best to make a full image backup. Then you can restore easily. The recovery DVD or partition normally wants the entire drive and cannot easily be run as long as Ubuntu is installed.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

If MBR you do need to resolve the 4 primary partition issue, so you can make one extended partition (which is one of the primaries) and then can create as many logicals as you want or need.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There&#8217;s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)
Discussion of swap on SSD - best not to)
[http://ubuntuforums.org/showthread.php?t=1937251](http://ubuntuforums.org/showthread.php?t=1937251)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Sorry for long post, but you asked an open ended question. If you want more details please post back. Others may have suggestions that are more simple. :)

---

