---
title: "Fresh Install/Upgrade Natty from Lucid, moving / BUT NOT /home, + dualboot Win7"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by silentstone on 2011-06-01
I have lots of precious data and decided to go the safer upgrade route of just freshly installing the new distro version from liveUSB to my netbook.  Currently, I have Ubuntu (Netbook Remix) 10.04 dualbooting with Windows 7 Starter.  /home is not on a separate partition, but I don't have enough free space anywhere else to store it conveniently.  But, the Windows 7 partition has enough unused space to hold my current system minus /home!  So, if I resize the Windows partition, create a new partition with the freed space, and install Ubuntu 11.04 to that new partition, I can turn my current / partition into /home.  

The steps I'd use:
-Windows

[LIST]
[*]   -Boot into Windows,
[*]   -defrag,
[*]   -defrag in safemode,
[*]   -resize down (in safemode?)
[/LIST]
 -Ubuntu (Lucid installed)

[LIST]
[*]   -Reboot into Ubuntu recoverymode,
[*]   -Backup system files to backup partition:
[/LIST]
      ```
root@netbook #: mkdir -p /media/BACKUPS/pre_natty/{usr-share,root-docs,etc}
  root@netbook #: rsync -a /usr/share/ /media/BACKUPS/pre_natty/usr-share
  root@netbook #: rsync -a /root/documents/ /media/BACKUPS/pre_natty/root-docs
  root@netbook #: rsync -a /etc /media/BACKUPS/pre_natty
  
```
[LIST]
[*]-Get list of installed programs:
[/LIST]
      ```
root@netbook #: dpkg --get-selections > /media/BACKUPS/pre_natty/lucid-installed-apps.list
 
```-Ubuntu (Natty liveUSB)

[LIST]
[*]   -Reboot into liveUSB, and mount Lucid's / partition
[*]   -Delete everything except /home
[/LIST]
      ```
ubuntu@ubuntu #: sudo rm -r /media/lucidpart/{boot,bin,cdrom,dev,etc,lib,lost+found,media,mnt,opt,proc,root,sbin,srv,selinux,sys,tmp,usr,var,windows}  
  
```
[LIST]
[*]-Move /home up one directory:
[/LIST]
      ```
ubuntu@ubuntu #: sudo mv /media/lucidpart/home/* /media/lucidpart

```
[LIST]
[*] And then proceed with installing Natty from liveUSB, formatting the newly created partition for /, and mounting /home on Lucid's former / partition.
[/LIST]
 
Questions...
Will Windows be bootable after this?  Currently, Grub2 handles booting into both operating systems, so will the Natty installer detect Windows and the Windows restore  partition, and set it up appropriately?
Am I missing anything?

---

### Post by TheAJGman on 2011-06-01
Yes Natty will pick up on Win7 but on the live install you must select ether install alongside Win7 or something else

---

### Post by silentstone on 2011-06-03
The defrag went well, though resizing the Windows partition did not.  The Win7 partitioner only want to release about 250MB.  I recall that while resizing with Windows own partitioner may avoid boot problems, Win7 likes to plant essential, immovable system files at the end of the partition.  When I installed Ubuntu the first time on this machine, I just used Gparted or something Linux, but couldn't access the Windows install at all, and had to restore the Windows install from the recovery partition, which was not fun.

There seems to be a way to create a Windows Recovery bootable USB, which would be a very good thing since I lack an optical drive and any external Windows recovery/install media.

Have the Linux partitioning tools found a way to shrink a Windows 7 partition without losing those essential, immovable system files typically placed at the end?

---

### Post by oldfred on 2011-06-03
Is the issue maybe that you are shrinking too much. Windows NTFS partitions need about 30% free space to work well. When at 20% it starts to slow down and at 10%, it you attempt a defrag plan on days, not hours if a larger partition. 

Ubuntu also need free space to work well also but it hides 5% to prevent you from crashing system.

---

### Post by silentstone on 2011-06-03
But the Windows disk partitioner reported a maximum shrinkable amount of 242MB.  That's a pitiful portion of the amount of actual free space on that partition (24GB free).  But I didn't realize that Windows would need that much free space on the system all the time, and I was planning on shrinking it down to only 7GB larger than it's current used space (25% free space).  Same deal with the future Ubuntu / partition--it would be 7GB larger than it's current used space minus /home (33% free).

---

### Post by oldfred on 2011-06-03
This was for Vista but 7 is just about the same.

Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC.

---

### Post by silentstone on 2011-06-18
Thank you for the link on Windows 7 partition shrinking.  Even following all the tips and installing a 3rd-party commercial defragmenter (**Perfect Disk**) that specified moving/defragging the troublesome MFT files and clearing free space at the end of the partition...only got me 6GB of shrink space.  This and no more; it shrank down once, but despite defragging and rebooting and boot-time defragging numerous times...despite 10+ GBs empty space at the end of the partition, Windows partitioner reported 0 shrink space.  This is where I tore my hair out, screamed, and grabbed a basket of chocolate.

I gave up on nicely using Windows tools to manipulate Windows partitions, and grabbed Gparted.  One last precaution was to make a Windows 7 Recovery boot USB, instructions here: [http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/](http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/)  This made me feel a lot better about potentially borking my system ;)

Booted Ubuntu Natty USB, used **Gparted** to resize Win7 from 38GB to 29GB (still leaves 30+% free space on that partition), and [COLOR=Red]grow the extended partition to the left as I realized I already had maximum primary partitions[/COLOR]!  After this, I rebooted into Windows to check (possibly repair) that system partition.  And it booted normally with a **chkdsk** call, to my utter surprise and glee!  :D  So, *why* couldn't Windows shrink itself? *throws hands up*  I need more chocolate.

---

### Post by oldfred on 2011-06-18
I hope it is good chocolate. And of course you left some for the rest of us.:)  We are all about sharing.

---

### Post by silentstone on 2011-06-18
Even better, I have an easy recipe so anyone can make it fresh themselves!

[SIZE=2][COLOR=DarkRed]**Chocolate-covered Strawberries**[/COLOR][/SIZE]
```
-1.5 cup fresh strawberries
-0.5 cup semi-sweet chocolate chips

1) Remove stems from strawberries, rinse and pat dry
2) Melt chocolate in microwave-safe bowl until smooth, stirring every 40 seconds. Try 50% power in 1-minute increments if your microwave doesnt have a preset for this.
3) Spear strawberries with a fork on one end, and dip each into melted chocolate, rolling around to coat strawberry thoroughly.

```At this point, I just flopped on the sofa and gorged myself on sweetness.  But for the more patient:
```
4) Sit coated strawberries on waxed paper and chill in refrigerator 30 minutes
5) Serve with whipped cream 

```Yeah, my version doesn't look nearly as good as this:
 [http://allrecipes.com/Recipe/chocolate-covered-strawberries/detail.aspx](http://allrecipes.com/Recipe/chocolate-covered-strawberries/detail.aspx) 
but it's quick and very chocolicious.
[I]
Installation will resume after the sugar cloud disperses.[/I]

---

### Post by silentstone on 2011-06-18
I'm currently running the 11.04 system installed to the new partition.  I got nervous and just kept the whole new installation on one partition.  After a more extensive test period, I can puzzle through switching /home to the old 10.04 partition for completely .  Yay for impatience plus caution!  There were several notes for configuring that old Ubuntu release for my netbook model (EeePC 1005HAB), but I've heard absolutely nothing about the 11.04 release and its suitability for my netbook.  So, baby steps.

[SIZE=3] What I've learned so far:[/SIZE]


[LIST]
[*] Windows 7's disk manager/partitioner does NOT shrink the system partition in Safe Mode.  As a matter of fact, it just completely sucks and I hate it and will hate all over it for the next 2 years.
[*] There are several simple backup utilities in the software repos.  Simple Backup doesn't preserve ownership/permissions.  LuckyBackup has some promise, but didn't save backup tasks/jobs/profiles, although it definitely copied the files and folders sufficiently.  Rsync worked fine as usual.
[*] You can grow an extended partition to the left, add another partition in the newly made area, and still access the old partitions (system and otherwise) without fault (yet)...My new partitions (**sudo parted -l /dev/sda**):
[/LIST]
 ```
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  29.5GB  29.5GB  primary   ntfs            boot
 2      29.5GB  239GB   210GB   extended
 9      29.5GB  47.6GB  18.1GB  logical   ext2
 5      47.6GB  154GB   107GB   logical   ext2
 6      154GB   202GB   47.4GB  logical   ext4
 7      202GB   238GB   36.3GB  logical   ntfs
 8      238GB   239GB   1343MB  logical   linux-swap(v1)
 3      239GB   250GB   10.7GB  primary   fat32           hidden
 4      250GB   250GB   16.5MB  primary                   hidden

```*1=windows7, 5=ubuntu1004nr, 9=ubuntu1104.  5 used to be at the start of the extended partition.  The old partitions*:
```
Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  47.6GB  47.6GB  primary   ntfs            boot
 2      47.6GB  239GB   192GB   extended
 5      47.6GB  154GB   107GB   logical   ext2
 6      154GB   202GB   47.4GB  logical   ext4
 7      238GB   239GB   1343MB  logical   linux-swap(v1)
 3      239GB   250GB   10.7GB  primary   fat32           hidden
 4      250GB   250GB   16.5MB  primary

```
[LIST]
[*]Unity desktop runs on this netbook model, but battery life is shorter so far.
[*]Ubuntu's installer (Ubiquity?) recognized Windows and Ubuntu pre-existing installations, and added all the boot choices to the new boot menu.  It's cluttered now, because I kept 5+ 10.04 kernels, plus their "recovery mode", memtests, and two measly Windows lines at the very bottom--the new Ubuntu is now top of the list, and only differentiated from the Lucid boots by their differing kernel numbers.
[/LIST]
Now, I have a clean new Ubuntu system to play with, so next up is to install the security and bugfix updates.

---

