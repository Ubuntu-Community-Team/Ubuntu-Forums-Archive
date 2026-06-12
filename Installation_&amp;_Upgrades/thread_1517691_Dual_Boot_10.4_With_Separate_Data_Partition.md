---
title: "Dual Boot 10.4 With Separate Data Partition"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Beacon Hill on 2010-06-25
Thanks in advance for any help on this topic.  I have previously used Ubuntu set up as a dual boot with Windows, but not in a way where I can access my data from either Windows or Ubuntu.  I find myself switching back and forth too often and saving data on a flash drive to access it in both environments.  I've read a few articles on how to have a separate partition for my data, and I think this will work best for me.  I haven't found step by step instructions that seem to fit my exact situation because my new laptop with Windows 7 seems to already have more partitions than I'm used to.  I am including a screen shot of the current hard drive configuration.
Thanks very much again.

---

### Post by darkod on 2010-06-25
Yes, with 4 existing primary partitions you can't even install ubuntu, let alone have a data partition. You gotta love these branded machines. :)

Here is how my suggestion would go:
1. Create recovery DVDs from the recovery partition. There should be instructions in a manual, online, or from HP support if all else fails. This is best because not only you can delete the recovery partition to create new extended partition, but also you will be able to use up the 17GB space. After you have created the DVDs simply delete this partition.

2. Make a plan how much space you need for your win7 + programs. If you plan to keep your personal data on the data partition for access from ubuntu, calculate the space needed only for the necessary win7 system files and your software. Move the data to external hdd. Then use windows Disk Management and shrink the win7 partition to the size you decided. You might need to turn off system restore if it doesn't allow you to shrink as much as you want, or even defragment before shrinking. Boot win7 few times after the resize to do its disk checks.

3. Boot with the ubuntu cd in live mode and use Gparted to create the ntfs data partition as LOGICAL, with the size you want. Depending how you organize your computer, I guess you can give minimum size for / and /home, and keep all huge files on the ntfs data partition. I still recommend to have separate /home for easier clean install in future. After creating this logical ntfs partition leave the rest of the space as unallocated.

4. Start the ubuntu installer and use Manual Partitioning. From the unallocated space you left, create 10-15GB / partition, 10-15GB /home partition and 2GB swap partition, or swap should be 1.5 x RAM size if planning to hibernate regularly.

You should have all these partitions sizes calculated in advance and planned.

That should be it. Any specific questions, ask.

---

### Post by yeleek on 2010-06-25
Why not dual boot again (below)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And then create a partition of a FAT32 file type which you then use to share files between ubuntu and windows.  This partition could be mounted in both os's....
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by darkod on 2010-06-25
> **yeleek said:**
> 
And then create a partition of a FAT32 file type which you then use to share files between ubuntu and windows. 

Why FAT32? Linux is OK reading and writing to ntfs since years ago. Having a ntfs partition is much better for windows too.

---

### Post by yeleek on 2010-06-25
' The present limitations of this driver are:

    * writing files encrypted or compressed at the filesystem level (does not include .zip, .gz, .rar files since they are compressed on the file, not the file system level)
    * changing NTFS file ownership and access rights '

No access right changes, no ownership changes, no ntfs encrypted files or ntfs compressed files.

Question should then be - why have NTFS :)

Oh and I don't dispute NTFS use under windows, its a no brainer.  OP was asking about sharing files, so easiest/quickest/most supported way is FAT32 - i think so anyway.

Edit - only reason for NTFS in this case i can see would be cluster size, NTFS performs better, but is that reason enough?

---

### Post by darkod on 2010-06-25
I guess they both have their pros and cons. And the performance under windows needs to be taken under consideration because if you don't plan using the files under windows there will be no need to share them at all. :)

I guess I still consider ownership changes or encryption as more advanced features.

I'm more concerned about fat32 limitation to 4GB files. That means no DVD images, not to even mention HD videos or similar...

It sounded impossible even to me few years ago, but these days there are more and more single files with over 4GB.

---

### Post by yeleek on 2010-06-25
That is a good point actually re max file size - hadn't considered it.

I agree with you in the light of that, NTFS it should be :)

---

### Post by Beacon Hill on 2010-06-25
Thanks for all the help.  I actually work with a lot of digital video files, some of which are over 4 gigs so I guess I'll use NTFS.  There isn't an optical drive on my new HP Touchsmart tm2, so it's too bad I have to erase the recovery partition.  Can I run recovery through a flash drive?

---

### Post by darkod on 2010-06-25
> **Beacon Hill said:**
> Thanks for all the help.  I actually work with a lot of digital video files, some of which are over 4 gigs so I guess I'll use NTFS.  There isn't an optical drive on my new HP Touchsmart tm2, so it's too bad I have to erase the recovery partition.  Can I run recovery through a flash drive?

Hmmm... again, there are few options, up to you. The HP Tools partition is also rather useless, people on this forum have deleted it without noticing any issues. That way you can keep the recovery partition. You only need to delete one. Not sure if the recovery process can run from usb stick.
But the thing about that recovery, is that it usually creates "as from factory state" on your computer. Which would mean it would wipe your hdd and set it as it was when bought.
IMHO that's no recovery at all. Not only it would wipe your ubuntu and all data on it, but also your data ntfs partition too. Would you call that success?

And all that just because MS and manufacturers don't want to give you install media. With install dvd you can just reinstall into the existing partition, no need to wipe your hdd.

You might want to discuss this with HP Support, and see what they say. On rare occasions some recovery partition actually leave the rest of your hdd alone, but I think that's very rare. Also, talk tough to them, and sometimes you can get them to ship you install media. Simply tell them that because of your work it is not acceptable your ntfs data partition to be also wiped just because win7 had few files corrupted. With install media you can simply repair.

Other options are to turn to open source backup software.
Like CloneZilla: [http://www.clonezilla.org/](http://www.clonezilla.org/)
Or what I recently found out and prefer better, because you can restore to partitions smaller in size than the source partition as long as the data fits:
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

Both of this you can run from bootable usb stick and have usb hdd as backup destination. Once you decide on the best way for you to backup, and do a one full backup of the computer as it is, you don't need the recovery partition any more. Even if you need to restore, you restore your backup and that will even restore all software currently installed instead of having to install everything again in blank win7.

Also you could consider investing in usb dvd drive, they're not too expensive and might be better for you.

Like always with Linux, IT'S ALL UP TO YOU!!! :)

---

### Post by Beacon Hill on 2010-06-26
I have created disks, so I suppose I can delete the recovery partition.  But if hp tools is unnecessary, maybe I should delete that one instead.  I can't seem to find a way to copy these partitions onto an external hard drive.  If I was secure in knowing that I had the information on these two partitions properly backed up, I'd probably just delete both of them.

---

### Post by darkod on 2010-06-26
> **Beacon Hill said:**
> I have created disks, so I suppose I can delete the recovery partition.  But if hp tools is unnecessary, maybe I should delete that one instead.  I can't seem to find a way to copy these partitions onto an external hard drive.  If I was secure in knowing that I had the information on these two partitions properly backed up, I'd probably just delete both of them.

CloneZilla should be able to clone them to an image file, if you want to keep them.

---

### Post by Beacon Hill on 2010-06-27
Unfortunately I need an optical drive to use Clonezilla.  I have the DVD recovery disks, so will probably just erase the HP Tools and proceed.

---

### Post by darkod on 2010-06-27
> **Beacon Hill said:**
> Unfortunately I need an optical drive to use Clonezilla.  I have the DVD recovery disks, so will probably just erase the HP Tools and proceed.

No you don't.

If you talk about running it, you can run it from bootable usb stick, like ubuntu.
And for target of saving the image file, you can have usb hdd set.

---

### Post by Beacon Hill on 2010-06-27
> **darkod said:**
> No you don't.

If you talk about running it, you can run it from bootable usb stick, like ubuntu.
And for target of saving the image file, you can have usb hdd set.
Thanks.  My bad.  The first tutorial I read on the subject explained that to use Clonezilla it requires:
"...that you be able to burn ISO files to  CD/DVD, boot from a live CD..."
I should have realized I could boot from a live flash drive.

---

### Post by Beacon Hill on 2010-06-27
Tried to make a bootable Clonezilla flash drive.  When trying to boot from it, got this error message: 
No bootable partition in table.

---

### Post by oldfred on 2010-06-27
Another way to create a bootable disk is to use grub2. 

I copied one or two of the commands to format and install grub from panticz and some of the entries for grub.cfg. panticz is a script to download and create the entire USB flash.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

If you understand the grub.cfg entry this script has the format required and may be able to make your flash drive. I have not tried it yet.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

If you look into the MultiBootUSB.sh file you can see how the format of the Clonezilla stanza should be.

---

### Post by bondo101 on 2010-06-28
I have saved my recovery partion on an external usb drive with all the files i want to keep. When my dell went down a few years back , I re formated reinstalled the operating system , then fund all the drivers i needed it ran better than the first day i bought it. I had a friends Hp do the same thing ,he did the same thing machine runs fine without the manufactured propaganda soft ware on it .Propritery software sucks. Even Sony is the same way.

---

