---
title: "Can a usb drive be partitioned to do a live boot/install?"
date: 2024-01-04
forum: Installation &amp; Upgrades
---

### Post by jeff153 on 2024-01-04
Hello, I'm a Linux newbie but my son will be helping me to try and resurrect a couple of Windows laptops for a friend. He lost the password on one & a virus apparently knocked out the other one.
I downloaded the Ubuntu ISO but I don't have a USB stick large enough to hold it. I am wondering if I or my son could take a 5T usb drive I use for my computer as a way to boot up & install Ubuntu on one or more of those machines without wiping out all of the files I already have on it. eg. could it be partitioned and keep the ISO in a separate partition from my data, and then be used to live boot the laptops & install Ubuntu?

Alternatively, could I install a smaller, lighter version of Ubuntu that would fit on the 3.74 GB stick (4 GB apparently required) that I have and then upgrade from there if needed?

Thank you for any help/recommendations.

---

### Post by ubfan1 on 2024-01-04
Either lubuntu or xubuntu would fit on that USB drive.  It's possible to have the iso on a hard disk, but setting that up involves a bit more work.

---

### Post by oldfred on 2024-01-04
Is your 6TB drive already a bootable device?
I regularly boot ISO directly, but you need grub2 to use its loopmount feature to boot ISOs.

If systems are after 2012, so UEFI, you can create a FAT32 partition with boot,esp flags and just extract 7zip or similar, an ISO into that partition. But FAT32 probably has to be near the beginning of the drive. Not sure what limit is but UEFI recommends the ESP - efi system partition be the first partition. But it can be any partition.

Years ago I stopped using DVDs, and then ISO become too large for DVDs. I used flash drives for years and now have multiple ones from 16GB to 256GB. But they are slow, particularly on writes. 
I now use external SSD. Upgraded my 2016 system from M.2 SSD (when NVMe was very expensive) to newer larger NVMe drive. I then put SSD into M.2 to USB adapter. So much faster I do not plan on any more new flash drives.

If installing to older systems or lower spec systems, you may want a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I use Kubuntu which is  more of a mid-weight flavor, but does work on older systems. 

Be sure to have good backups, particularly before any major change. Most of us have learned the hard way what not to do. And good backups, make recovery easy.

Best to have USB flash drive with Windows repair/recovery tools and an Ubuntu live installer for current version you are using. I still have those, although using SSD for installs. 

The server download is just less than 2GB, you can install server, then install desktop of choice. 
[https://ubuntu.com/tutorials/install-ubuntu-server#1-overview](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)
[http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-live/20240104/](http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-live/20240104/)

---

### Post by jeff153 on 2024-01-04
Thank you, @[[COLOR=#000000]ubfan1[/COLOR]]("https://ubuntuforums.org/member.php?u=1256996")

If we install either of those flavors, would be be able to install another flavor from the now running laptop without requiring another live drive?

---

### Post by jeff153 on 2024-01-04
Sorry, duplicate.

---

### Post by jeff153 on 2024-01-04
Thank you @[[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711")

You give some great information there. Some/much of it is a bit over my head, but hopefully it will be something I can read up on & learn &/or my son will know more about it... plus others may be helped as well.

My big USB drive is not bootable. I've read about partitioning but I have never done so. If I go that route I will need to read up on it. For instance, how to make the partition for the bootable live drive at the beginning of the drive.

On a separate note re: FAT32 formatting. That was on a flash drive that I used to put some portable apps & songs on a friend's computer for a religious service but the app didn't like that. I had to reformat it to NTFS, which I thought was the newer way to format. Do the Ubuntu live drives need to be on drives that are FAT32 formatted?

I'll ask my son about the server idea. That sounds interesting, but again is a bit over my head.

---

### Post by yancek on 2024-01-05
>  If  we install either of those flavors, would be be able to install another  flavor from the now running laptop without requiring another live  drive?                                                                                              

Yes.  If you were to install either Lubuntu or Xubuntu from a flash drive onto the drive you reference, you will then have Grub installed on that drive and will be able to boot Ubuntu (or another Linux) iso file directly from Grub.  That is what oldfred is talking about in the post above and there are countless sites available online explaining how to do this with examples.

Some software used to create a bootable Linux on a flash drive requires/prefers a FAT filesystem.  Since the Linux iso is a different filesystem, you can boot it directly from Grub regardless of the filesystem type on a partition, vfat, ntfs, ext4, ...  The vfat requirement is a limitation of some software not the Linux iso.

---

### Post by oldfred on 2024-01-05
FAT32 is really only for smaller partitions. It does not support files over 4GB nor does it have journal for easier recovery.
So for your large drive is used with Windows NTFS would be a better choice.

The ESP - efi system partition used for UEFI boot is 100 to 600MB used for UEFI boot files. I guess UEFI used FAT32 to be more common back when standard created and they only needed a smaller partition. Early versions of Windows used 100MB and Ubuntu's grub also fit without issue. But multiple boot or use of other boot loaders may need more space in ESP. And since usually first partition and making it larger is then huge hassle, best to allocate a little extra space. When using smaller flash drives I use smaller ESP as I know I will not be needing more space.

Resizing a large drive to add a partition at beginning is a bit more dangerous. Good backups required. 
When trying to make space at beginning of drive, it has to move all data in partition further into drive which can take a long time. Often step-by-step due to space limits. Any interruption totally corrupts partition and data is lost.

While gparted can work with NTFS partitions, often better to use Windows tools for NTFS. 
You should not fill NTFS partition more 70-80% so it has working room. If fuller than that, drive will get slower and defrag may take forever. With very large drive, you may be able to have somewhat higher percent used, just as long as space left for NTFS.

---

### Post by jeff153 on 2024-01-05
@[[COLOR=#000000]yancek[/COLOR]]("https://ubuntuforums.org/member.php?u=1928724") & @[[COLOR=#C61919]oldfred[/COLOR]]("https://ubuntuforums.org/member.php?u=852711") - Thank you both very much for your time and trouble. I have been wanting to learn how to do these types of things for a long time but have gotten a little intimidated with the process the couple of times or so I felt motivated enough to attempt it & chickened out at the end afraid that I would break stuff. I was also forced to use windows with some companies I worked with as they required Internet Explorer to log into their systems. That's no longer the case, of course.

I'm still swimming in deep water for me, but I think that you've given me enough information and guidance to jump in and give it a go.

Thanks again!

---

