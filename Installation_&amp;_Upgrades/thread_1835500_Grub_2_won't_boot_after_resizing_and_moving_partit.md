---
title: "Grub 2 won't boot after resizing and moving partition"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by two4two on 2011-08-29
I have:  WinXP (FAT32) on SDB1, Ubuntu Studio (ext4) 10.4 on SDB2, NetBSD on SDB3, and an extended partition with an NTFS partition, a Linux sap partition, and 3 FAT32 partitions.  I had the GRUB loader on the boot sector of SDB2 and used a tool called BOORPART to install it onto the WinXP partition so I used the NT boot loader to link to the GRUB loader.  The WinXP and Ubuntu Studio partitions were running out of space, so I used GParted to resize and move all the partitions.  I made the FAT32 data partitions smaller and moved them.  I deleted and re-created/re-located the Linux partition, and I relocated the NTFS partition.  I deleted and re-created/re-located (but not formatted or loaded) the NetBSD partition and so it should have been seen as unallocated space. I enlarged and re-located the Ubuntu Studio partition, and I enlarged the WinXP partition.  WinXP booted, but Ubuntu Studio did not.  testdisk did not find the new NetBSD partition (it skipped that empty space), and it showed the NTFS data partition as a primary partition.  I tried to use the Ubuntu Studio DVD to re-install GRUB, but I ended up in the dialog to re-install all of Ubuntu Studio.  But that failed anyway.  I tried Gparted from a live CD but it thought the ENTIRE DISK was unallocated!  I tried Parted and it said a partition went outside of the disk.  I used testdisk to make images of and delete all but SDB1 and SDB2 (WinXP and Ubuntu Studio).  Then Gparted could find my first two partitions and WinXP could still boot.  So I used Gparted to re-create all the other partitions except the first 2.  I loaded the backed up images into the new partitions, and finally Gparted can see ALL my partitions just as I created them and the live CD can see all the recovered data as well.  The live CD can also see all the Ubuntu Studio file system and all the files, so I know it is still there.  So I tried the Ubuntu Studio install DVD again to do a repair install to re-install GRUB to the boot sector of the Ubuntu Studio partition and it fails.  It says re-install grub fails with code 1.  So, how do I get grub to install on that partition so I can boot my Ubuntu Studio partition?  Anyone read this entire post?  Anyone know how to help?

---

### Post by oldfred on 2011-08-29
It seems with all the partition changes, the partition table entries were damaged. You can not have a partition outside of disk and until that is fixed nothing else will work.

If you deleted and recreated a partition its UUID will change. You then have to reinstall grub to make it work.

Backup current partition table first.
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


From Ubuntu liveCD or many Linux repairCDs:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You can also download this:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by two4two on 2011-08-29
Somehow this is reporting backwards:

I've attached results.txt.  I always thought that the first hard drive on the on-board primary controller was sda, and sdb was the next hard drive it finds (either primary slave or secondary master then slave.  And then down the bus to each other controller?


I have one drive connected to the mobo:  my Win98SE drive that has the ntldr and the Win7 loader, and the bootpart software to get all other boot records (512 bytes) and put in a file so they can be chain loaded.  This is SUPPOSED to be sda, right?  Here on this session it is sdc.

My hdd that has the Ubuntu is listed as sda.  This drive is the first HDD on a PCI add-in controller card.  I didn't think that was how it should work.  

The slave drive on that controller is now sdb and it has Win7.  This should be sdc, right?  But it is sdb.


So I'm wondering if the reason re-installing grub fails is beacuase I'm pointing to the wrong drive?  I'm pointing to sdb2 to install grub.




This OS that I'm using to run the script and produce the report is Fedora14 which is the 3rd partition on my Win98SE drive -- listed as sdc here, but I always thought was sda.  Why is it reporting this backwards?


Any way, here is the report.  Maybe you can explain why everything boots up just as I expect:  I get the Win7 boot loader (which is on the Win98SE drive), and from there I chain to the NTLDR (which is also on the Win98SE drive), and from there I used to chain to all other OSs, and the Ubuntu OS was I thought was sdb2 is, but this OS thinks it's on sda2, and it won't boot. 


So, what to do to get Ubuntu Studio to boot?

And how to fix those minor problems with the logical partitions.  All my OSs can read those partitions, so the data is just fine, but is it really a problem that it is reporting?

---

### Post by oldfred on 2011-08-29
Is one or more of your drives IDE and others SATA? Older PATA/IDE only booted from primary master. SATA uses BIOS to set boot order but at least on my system with all SATA port order seems to define mount order in Linux. But mixed PATA/SATA systems usually promote the IDE drive to sda, then you see the SATA drives.

Since you have multiple drives why not install different boot loaders in each drive. With Ubuntu's grub2 and its os-prober you can directly boot everything, although Windows is chainloaded and you may want to chainload any system with grub legacy, so you do not have to boot Ubuntu to update new kernels in grub2's grub.cfg. 

Grub2 does not like to be installed to a partition as it converts to blocklists and any update to grub's files that move them, then breaks the boot. You then have to reinstall grub2 to the partition. But you have many MBRs, so just install to any one of them.

I suggest you also move your Windows 7 boot files from the XP partition. Many windows users do not realize that windows only boots from one partition and litteral moves the boot files from all later installs to the first boot partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)
HowTo: Boot Vista and Windows 7 directly from the Grub menu = meierfra.
Comment on edit PBR to allow booting
[http://ubuntuforums.org/showthread.php?t=1146266](http://ubuntuforums.org/showthread.php?t=1146266)

I would also put a windows boot loader in sdb, so you could boot Win7 directly. I prefer to have operating systems on different drives and make each drive independently bootable. That means MBR, all system files, & swap. Then data can be mounted from various drives and if any one drive fails I have a system on another drive to boot with.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

I do not see the issue with your partitions?

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I stopped using FAT partitions several years ago except for small external devices. FAT only holds a 4GB file and I lost all my backups. It also does not have journaling, so any corruption is harder to recover from. You need to have windows repairCD to run chkdsk or make other windows repairs in case you cannot boot windows. I just used my win7 repair  USB to run chkdsk on XP, but did have to recreate the NTFS  Partition boot - PBR as it converted it from XP to Vista/7.

I would just install grub2 to sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# In BIOS or with one time boot key boot sda or 500GB drive
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by two4two on 2011-08-29
All the standard HDDs are IDE, but there is a SATA BD-RW, and there are two USB external drives (1TB, and 1.5TB)

---

### Post by oldfred on 2011-08-29
I would think IDE's would be primary master & slave & secondary master & slave. But I have also seen some BIOS put external devices in first or even random places. My USB flash drives are always after SATA but may not be next drive letter. Part of why Ubuntu uses UUIDs so device number does not matter.

---

### Post by two4two on 2011-09-02
OK, I want to install GRUB into the partition where I installed Ubuntu.  When I first installed Ubuntu it gives you the choice of where to install GRUB and so I chose to put it into the Ubuntu partition.  I'd like to keep it that way.  So I'm using the Ubuntu Studio install DVD, which is not a live DVD, and I choose repair mode.  I didn't like that because it seems as though it might overwrite my /usr directory.  So I chose another option to simply re-install GRUB.  It fails with a code 1.  So I tried to run a shell in /dev/sdb2 (which is, in fact, my Ubuntu partition).  Contrary to the fact that my Fedora OS identified it as sda2 in the reports I posted for you, this Ubuntu install DVD identifies it as sdb2.  So in the shell I executed the following commands:

sudo fdisk -l   (which verifies it is sdb2)
sudo mount /dev/sdb2 /mnt   (per your instructions)
sudo grub-install --root-directory=/mnt /dev/sdb2 (sort of per your instructions)

I get a message:

warn:  attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.  Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are unreliable and its use is discouraged.  If you really want to do it use --force




I don't understand the difference between what I'm doing in the shell vs what happens in the rescue-mode GRUB re-install, or for that matter what the original install does and why, if it gives the option to install it to the partition, this process gives such a dire warning.  Does it have to do with the fact I'm in a shell in that partition?  What's going on?  I will investigate the grub-install command for now.  

I don't want to have to format and re-install everything.  I like my current Ubuntu Studio setup.  I just wish I could boot to it again.  How can I do that?

---

### Post by oldfred on 2011-09-02
Old grub legacy seemed to work from partitions, but grub2 is larger to accommodate many new features and uses block lists which are hard coded addresses to find the rest of grub instead of file names. When grub is updated it may move on the drive and you will have to reinstall grub to the partition to fix it. That is why it is less reliable, but it will work. 

With 9.04, I used chain loading for everything and with 9.10 I installed grub2 to its partition. It worked as I was able to chain load and I had it that way for a while, but I do not think there were any updates. I then converted to grub2 in the MBR and now like grub2.

If you are using Fedora to boot and its current grub legacy then you should just be able to add a boot stanza in Fedora's grub.conf. Fedora's new alpha uses grub2.

Set X to drive number 0 or 1 that Fedora sees it as. And Y to grub legacy number of partition. Chainload only works if grub is installed to partition.
```
title Ubuntu 11.04
root (hdX,Y)
kernel /grub/core.img
boot

title       Ubuntu 9.04 Jaunty 64 bit @ sdc5
root        (hd2,4)
chainloader +1


title    Most Current Ubuntu on sdc5
root    (hd2,4)
kernel   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

```

---

### Post by two4two on 2012-05-08
All I could do was re-install Ubuntu into the newly resized partition.  Could not figure out how to save it.

---

