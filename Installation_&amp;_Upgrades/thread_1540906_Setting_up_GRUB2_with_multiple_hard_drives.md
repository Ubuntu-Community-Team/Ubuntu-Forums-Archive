---
title: "Setting up GRUB2 with multiple hard drives"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by zSeries on 2010-07-28
Hi,

This is my first post so please be gentle! I have been trying to move away from Windows2000 on Ubuntu for months. I have a few applications that I run on Windows that I have been unable to find usuable equivalents on Ubuntu eg Outlook/Mobile sync application required for my job and a DVB TV card application for home. So it looks like I am stuck ruuning W2K and Linux for at least a while and indeed I have been using GRUB2 to select between W2K and Ubuntu.

I need some basic advice about setting up GRUB2. My philosphy when it comes to PC data is you can never have enough backups and I  avoid any single point of failure. So I have always used two hard drives which I keep in sync almost daily with FreeFileSync. I also swap my most critical encrypted data between a laptop and desktop. Then I also alternate external USB drives stored away from my home.

My current partions are

Hd1 500GB - Primary    20GB NTFS W2K & programs
            Extended  100GB NTFS Windows data on this PC (and copied to external to USB)
            Extended  100GB NTFS Backups of other PCs    (and copied to external to USB)
            Extended  250GB NTFS Non critical data/work files
            Extended   20GB Ext3 Ubuntu 10.04
            Extended   4GB  Swap

Hd2 120GB - Primary    20GB NTFS W2K & programs
            Extended  100GB NTFS Backup of Windows data on this PC

When I installed on the Ubuntu 500GB I let it & GRUB2 take the default options so it boots from Hd1 and I assume certain executables are stored at the begining of the Ubuntu partition as well as configuration files in its file system.

Now I'm replacing the 500GB with a 1.5TB and the old 500Gb will become my backup drive. I want to keep the backup drive bootable in its onw right. If either hard drive fails I want a bootable system and acccess to my data.

So my plan is to use the following partitions

Hd1 1.5TB - Primary    20GB NTFS W2K & programs
            Extended  250GB NTFS Windows data on this PC (and copied to external to USB)
            Extended   20GB NTFS Reserve for Windows upgrade if needed, maybe Windows 7 sigh
            Extended   20GB Ext3 Ubuntu 10.04 (fresh install)
            Extended    4Gb Swap
            Extended   20GB Ext3 Linux /home (shared with other Linux images)
            Extended   20GB Ext3 Ubuntu next release
            Extended   20GB Ext3 Other Linux?
            Extended   20GB Ext3 Other Linux?
            Extended  250GB Ext3 Linux data (Sync with Windows NTFS)
            Extended  750GB NTFS Non critical data/work files

Hd2 120GB - Primary    20GB NTFS W2K & programs
            Extended  100GB NTFS Windows data on this PC
            Extended  100GB NTFS Backups of other PCs (Sync with Hd1)
            Extended  250GB NTFS Non critical data/work files
            Extended   20GB Ext3 Ubuntu 10.04
            Extended    4GB  Swap

I can install W2K on the 1.5Tb from scratch or use Acronis to restore an image file. Then I can install Ubuntu from scratch.

OK now for my questions.

1) Can I get GRUB2 to put its executables and configuration files on a small partition of its own? I see no reason why they should be dependant on a specific Ubuntu partition. I have read posts mentioning this but not sure if this has to be a bootable Linux or just a file system with the config files.

2) Can I run update-grub on any Linux and store or copy the config files to the partition in 1?

3) I will use BIOS to determine which hard drive is first to boot. When I run update-grub (or when it runs during the new Ubuntu install on Hd1) I dont want GRUB2 to do anything with Hd2, not even know Hd2 exists, it that an option?

Thanks,
Tony.

---

### Post by oldfred on 2010-07-28
Do not plan on sharing /home. You can share a linux /data that has all your data files in /home but not the configuration settings without the possibility of issues of different versions of software having different settings. You can also easily share all the NTFS partitions with all linux and also obviously with windows.

I install grub2 to the same partition as the Ubuntu install so each drive is separately bootable. I also have a few boot stanza's in my USB install that will let me manually edit to boot other installs by chainloading or directly without having all the entries that grub2 likes to put in.

You can create a grub only partition. I in effect have that to boot my 4GB USB flash that has several ISOs for emergency repair and all my installs. Install is quicker from the USB and easier just to copy to USB and edit grub.cfg on flash drive.

I am not sure you need a grub partition. I have one but with grub2 do not really use it anymore.
Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
grub2 partition
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

Grub can be nasty on which MBR it installs. It wants to install to sda or the boot drive. They are updating and it seems to change.

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions
The data saved is by drive letter not UUID, so if drives change you need to rerun.

Grub2 will automatically find other installs. You can turn off parts of the update or create totally custom menus of whatever you want. Does require a little effort and understanding of grub2.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by dabl on 2010-07-28
In my desktop rig I run 3 hard drives, containing 10 partitions total, and use Grub 2 to boot two OSs (both Linux), so my first instinct is that you are making your project more complicated than it needs to be.

However, if you are most confident in using the BIOS sequence to select one or the other hard drive to boot, then so be it.  Your scheme will work, as long as you observe a couple of rules.

1. The Windows drive/partition needs to have the "boot" flag set on it, before you install Windows or copy it from Acronis or however you do that.  Whether the Linux drive needs that is probably more a function of your BIOS -- if Grub starts then it will boot Linux and the boot flag doesn't matter to Grub.

2. I don't see anything in your plans that would require that you make a special partition for /boot, in which to have the Grub files installed, but you can do that if you want to. People used to do that to conserve hard drive space when booting multiple OSs, but hard drive space is $0.05 per Gigabyte today so it doesn't make a lot of sense for default installations to make a separate partition for /boot.

3. If your plan is to run these two hard drives separately, then you don't ever want to run update-grub while the Windows drive is connected and running.  update-grub's os-prober will find the Windows partition and add it to your boot menu, thus foiling your plan to keep the booting separate.  So you'll have to disconnect the Windows drive every time an update to Ubuntu includes a new kernel or grub updates.  Kinda clunky, huh?

Personally, with your objectives, and after taking care of partitioning in advance, I would do a clean installation of Windows on its hard drive, followed by a clean installation of Ubuntu on its drive, and install Grub to the MBR of the first hard drive (i.e. the Windows drive) and cope with any needed adjustments to the boot menu afterward. No hard drive disconnecting needed if you do it that way, forever.  ;)


EDIT:  and oldfred types way faster than I do, and gives good advice, too ...  :)

---

### Post by zSeries on 2010-07-29
Thanks for the replies. I'll post some feedback at the weekend when I have tried this out.

---

### Post by zSeries on 2010-08-03
I went ahead and partitioned my new 1.5TB drive. A couple of partitions for windows, a swap, 4 x Ext3 for Linux OS', an NTFS data partiion and an NTFS work partition and a small Grub2 partition. I cloned my primary & backup windows system using Acronis. Then installed Grub2. It found all my OS's. 2 x Windows on the old drive and a Ubuntu. I was able to boot any OS. I removed the old drive and Grub2 boots. I see all the bootable systems listed, thats OK I'll u[date the Grub2 menu later to remove the ones on the removed drive. My Windows boots OK from the new drive. Initially I had a problem with Windows because it still wanted to use a page file on the old drive (it booted using J: as the primary drive and wanted to use C: for paging on the old remove drive, took me a while to resolve that but its a windows issue, OT here!). The whole process is not a job for novices.

Anyway now I have tried 10 times to install Unbutu on one of the Ext3 partitions I allocated on the new drive but cant get past "Installation Failed". I'll begin a new thread.

---

