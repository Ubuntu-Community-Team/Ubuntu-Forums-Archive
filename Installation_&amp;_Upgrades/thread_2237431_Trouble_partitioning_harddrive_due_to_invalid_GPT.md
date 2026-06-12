---
title: "Trouble partitioning harddrive due to invalid GPT"
date: 2014-08-01
forum: Installation &amp; Upgrades
---

### Post by DiscoDave95 on 2014-08-01
Hello, I recently purchased a Dell XPS 8700 that came installed with Windows 8. To get rid of the Windows 8, I booted into a live cd of Ubuntu and deleted EVERY partition on my 2tb harddrive. This included all of the GPT Headers and fake msdos. I then installed Windows 7 in the one giant partition I had made. However, if I boot into a livecd and launch gParted, gParted will give me an error message asking me if this is a GPT drive and if so then it doesn't contain the fake msdos as it should.  Because of this error gParted says my entire harddrive is empty. Is this because I deleted all GPT partitions? Am I better off converting to MBR or restoring GPT? All I need is a Windows Partition, a Xubuntu Partition, and then a shared ntfs data partition to store music, videos, pictures, etc.

I found these instructions from a different thread that had similar problems to me:
> 

[LIST=1]
[*]Boot into the Ubuntu Live CD. Alternatively, get the latest version of [Parted Magic]("http://partedmagic.com/") or [System Rescue CD,]("http://www.sysresccd.org/") boot it, and skip the next two steps. 
[*]Go to the [GPT fdisk (gdisk) download page]("http://sourceforge.net/projects/gptfdisk/files/")  and obtain the latest version (0.6.13) for your architecture. I'm  afraid I missed what that was, if it was stated. It'll be either the  gdisk*i386.deb or gdisk*amd64.deb file. 
[*]Install the  gdisk package file. Double-clicking on the desktop should do this, or  you can type "sudo dpkg -i gdisk*deb" in the appropriate directory. 
[*]Open  a shell and type "sudo sgdisk --zap /dev/sda". It'll complain about  partition problems, but it will still work. Be sure to use the --zap  option, not --zap-all; also, note that the command name is sgdisk, not  gdisk. 
[*]Proceed with your Ubuntu installation. 
[/LIST]


Should I try this? Will this allow gParted to read my hardrive properly?

---

### Post by oldfred on 2014-08-01
Gdisk is overkill and may erase your Windows install also. I think it erases both gpt & MBR partition tables.

Use fixparts, also by same author.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

Windows converts a gpt drive to MBR with a BIOS install, but leaves the backup gpt partition table.

You can convert the Windows 7 installer from BIOS to UEFI to take advantage of newer hardware. But Windows only boots from MBR drives with BIOS or only boots from gpt drives with UEFI.
Ubuntu will boot with either BIOS or UEFI from gpt partitioned drives. 
Make sure you boot Ubuntu in BIOS Mode if Windows is in BIOS mode.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Use Windows partition tools to shrink NTFS partition, but not to create any partitions. Reboot Windows immediately so it can run chkdsk to recognize its new size, otherwise gparted may still have issues as if chkdsk flag set it still may not mount it.

---

