---
title: "Install/partition question - multiple OS and partitions setup?"
date: 2021-07-16
forum: Installation &amp; Upgrades
---

### Post by linuux on 2021-07-16
I'm pretty sure this question has been answered before.  There's a similar question from March 2021.  I did read through it but I have my own spin I want to ask about.

I am wondering about this - which is kind of a two-part question:

Ubuntu 20.04/21.04 etc. - it doesn't matter?:  partitions for / (root)  |  /home  |  (data) - how is that set up?

I have always had one partition and then a separate data partition - maybe FAT32?  Although, I would probably use a HDD for a FAT32 partition

E.g.  1tb SSD - please provide me an example of how you would partition a 1TB SSD - and it can be 100% Linux - then do the same for a 2nd example if it was a dual boot?


The other thing I was thinking about is what if you wanted to boot other Linux operating systems?  Is this a good/bad idea on an SSD?   Since, you have to worry about read/write cycles?  Or maybe it doesn't matter so much as long as the 'new installs/fresh installs' aren't done too often?   I only have experience with legacy hard drives so far and I never cared how often I re-installed or 'formatted/fresh installed.'

My current computer only has room for one drive - so I plan on getting a 1TB SSD and plan on dual booting Windows 10 and Linux (Ubuntu).

Although, my plan in the future is to invest in a current gen Ryzen or Rocket Lake (Intel) computer - with M.2 NVME and maybe 2 SSDs - allowing for separate Windows 10 drive and a separate Linux drive - thus, allowing for more possible configurations. 

I read about separate root, home and swap partitions but I am inclined to think it's better to have less partitions than more - when dealing with solid state drives.   Right?  

With the older computer I have, I would probably use a simple setup so just two partitions - one for Linux and one for Windows.   But, the question in this setup is how many partitions for the Linux setup (assuming, I use only one Linux OS)?   I typically have my data on a separate HDD - so even if I have some data in the /home directory, I will copy it to the HDD.   So, I am not too worried about the data in /home since I have a copy.

---

### Post by oldfred on 2021-07-16
Partitioning is very opinion based. Even my own "optimal" partitioning is usually not very good after a few years. But then I get new drive & start over.

My examples.
Oldfred's partitions with new NVMe Feb 2020 UEFI 
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)
Oldfred's partitions Dec 2015 has ESP & bios_grub
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

TheFu really likes LVM, but it is a bit more advanced. 
Disk setup, Partitioning, Mounting, Adding - Where to begin ? 
[https://ubuntuforums.org/showthread.php?t=2459660&p=14027975#post14027975](https://ubuntuforums.org/showthread.php?t=2459660&p=14027975#post14027975)
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

---

### Post by Bashing-om on 2021-07-16
linuux; Yup - Uh Huh

+1 to oldfred's advise. Partitioning is subjective to "your" use case.

As an aid, howver, in your thought process - here is my multi-boot configuration.
> 
sysop@2004x-c:~$ sudo fdisk -lu
[sudo] password for sysop: 
Disk /dev/sda: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfdddae1a

Device     Boot    Start       End  Sectors  Size Id Type
/dev/sda1  *        2048  58593279 58591232   28G 83 Linux
/dev/sda2       58593280 156250111 97656832 46.6G 83 Linux


Disk /dev/sdb: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk model: PNY CS900 120GB 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc6c4079f

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1  *         2048  16386047  16384000  7.8G 83 Linux
/dev/sdb2        16386048  36866047  20480000  9.8G 83 Linux
/dev/sdb3        36866048  49154047  12288000  5.9G 83 Linux
/dev/sdb4        49154048 172034047 122880000 58.6G  5 Extended
/dev/sdb5        49156096 110596095  61440000 29.3G 83 Linux
/dev/sdb6       110598144 131078143  20480000  9.8G 83 Linux
/dev/sdb7       131080192 151560191  20480000  9.8G 83 Linux
/dev/sdb8       151562240 160163839   8601600  4.1G 82 Linux swap / Sol

//

sysop@2004x-c:~$ sudo blkid
/dev/sda1: LABEL="x2004c-root" UUID="7e618077-2513-4f99-bddf-ebd39ec3fdcf" TYPE="ext4" PARTUUID="fdddae1a-01"
/dev/sda2: LABEL="x2004c-home" UUID="3c6e37ac-b77c-4701-8439-089efc60290f" TYPE="ext4" PARTUUID="fdddae1a-02"
/dev/sdb1: LABEL="x1804root" UUID="1460de17-30e4-4566-b181-18c17b62887a" TYPE="ext4" PARTUUID="c6c4079f-01"
/dev/sdb2: LABEL="x1804home" UUID="5cd50446-1330-4130-a521-1ea936c9fc2a" TYPE="ext4" PARTUUID="c6c4079f-02"
/dev/sdb3: LABEL="x1804var" UUID="69b1f02a-5e00-415e-ab75-78fdd63f72a3" TYPE="ext4" PARTUUID="c6c4079f-03"
/dev/sdb5: LABEL="u1804" UUID="0b89d785-9ba8-4bd5-a41a-43462459c230" TYPE="ext4" PARTUUID="c6c4079f-05"
/dev/sdb6: LABEL="bups" UUID="a0c6dc1f-51d3-4824-b770-ce42d777277a" TYPE="ext4" PARTUUID="c6c4079f-06"
/dev/sdb7: LABEL="data" UUID="fe9cee2e-6812-46e1-b0a0-b03d5094763a" TYPE="ext4" PARTUUID="c6c4079f-07"
/dev/sdb8: UUID="5e1c0b41-6fda-4231-877c-1e0601a626b5" TYPE="swap" PARTUUID="c6c4079f-08"
sysop@2004x-c:~$ 


As you can see, the bare operating system does not require a lot of disk space.

[INDENT]hope this helps
[/INDENT]

---

### Post by grahammechanical on 2021-07-17
> Is this a good/bad idea on an SSD?   Since, you have to worry about  read/write cycles?  Or maybe it doesn't matter so much as long as the  'new installs/fresh installs' aren't done too often?

If my memory serves me well, which it often fails to do, read/write cycles were a concern when SSDs were first introduced. There was a lot of talk about using something called "trim" to extend the life or reduce "wear & tear" of an SSD. The other year when I purchased a second hard drive I decided not to have an SSD because i often do multiple installs of different flavours of Ubuntu. I made this choice because of the information I read about read/write cycles. Now, I am not sure my information was up to date.

Today, when I did an internet search I could find no modern posts that expressed concern about read/write cycles of SSDs. Ubuntu has activated "trim" by default for some years. Physical hard drives fail and so do solid state drives. Some claim that SSDs are more reliable than hard drives because giving the computer a knock could cause the physical drive to damage data but not with an SSD.

This is a fairly recent article.

[https://www.n-able.com/blog/ssd-lifespan](https://www.n-able.com/blog/ssd-lifespan)

Apparently, read/write cycles is the wrong term. We should be saying program/erase cycles. Learning all the time.

Regards

---

### Post by TheFu on 2021-07-17
I think Oldfred and others provided good advice above, so I'll leave those alone.

> **linuux said:**
> Ubuntu 20.04/21.04 etc. - it doesn't matter?:  partitions for / (root)  |  /home  |  (data) - how is that set up?
If this is a layout question, then that's answered already. Sometimes we forget that normal people coming from some other OS are used to storage setup being a wizard that guides them through. That isn't the way it works on Unix.  This is all dangerous and the person doing the work is expected to know some things - like only make a partition table if there isn't one there already. Creating a new partition table will wipe the old one and you'll be having a really bad day. If that isn't obvious to you why, then you should stop now and take the computer so someone who does understand why.

If you get a new HDD/SSD, here are the steps to make that storage available:
>  These steps apply to local, directly connected, storage:

1. Connect the drive; sata, esata, usb, infiniband. Just needs to be directly connected - with a wire and not over networking.
2. Use gparted to force-create a GPT partition table and 1+ partitions.
3. Still in gparted, format the partition as ext4 ; for Flash storage, may wan to choose f2fs as the file system.
4. Still in gparted, label the partition, say "[COLOR="#008000"]STUFF-1[/COLOR]" ;
        > Tips: No spaces, no funny characters or punctuation, must be unique 
5. Still in gparted, click the "Apply" check icon to actually carry out the prior choices.
6. Choose where to mount the storage and create an empty directory in that location. /mnt/[COLOR="#FF0000"]stuff-1[/COLOR]
        > Tips: choose storage under /mnt/ or /media/ if you use snap packages. However, any empty directory at any level can be used, except /. I put data drives under /d/D1, /d/D2, /d/D3, /misc, /stuff and backups under /d/b-D1, /d/b-D2, /d/b-D3, for example. Snap programs cannot access any of those locations outside /mnt/ or /media/ and only if the constraints for the snap package supports the removable media option.
7. Edit the /etc/fstab to mount the storage.
    ```
sudoedit /etc/fstab

```        > Tip: sudoedit is the safe way to edit system files. Any editor we prefer can be configured to be used and still be safe.
8. Add this line:
```
    LABEL=[COLOR="#008000"]STUFF-1[/COLOR]  /mnt/[COLOR="#FF0000"]stuff-1[/COLOR]  ext4  nofail,noatime,errors=remount-ro   0   2
```
        > Tip: spacing (AND lack of spaces) is very important in this line. The options area cannot have any spaces. Between each grouping, 1 or more spaces is fine. It must be a single line per mount. Also, add 1 blank line to the end of the file. That's a good tip for all Unix config files. Never have the last config line end the file, always have an <CRLF>, then <EOF> marker.
1. Mount the storage:
```
    sudo mount -a
```
2. Verify the mount happened:
```
    df -Th | egrep -v 'tmpfs|loop'
```
      or
```
    df -Th | egrep [COLOR="#FF0000"]stuff[/COLOR]
```
3. Change the owner of the mounted storage to your userid.
```
    sudo chown -R $USER: /mnt/[COLOR="#FF0000"]stuff-1[/COLOR]
```
        > That command recursively changes the owner to the current USERID and default GROUPID, probably you. For a single-user system, this is probably what you want. On a multi-user system, maybe that storage needs to be shared? Be very careful with chown. If you do it on the OS files, you'll get a system that won't boot or a completely non-secure system. Reinstall is the only fix - or restore from backups.

That's it. Use the newly formatted, mounted, and storage under /mnt/[COLOR="#FF0000"]stuff-1[/COLOR] . Order of the commands matters for some parts, but not all.

I copy/pasted that stuff.

> **linuux said:**
> I have always had one partition and then a separate data partition - maybe FAT32?  Although, I would probably use a HDD for a FAT32 partition

E.g.  1tb SSD - please provide me an example of how you would partition a 1TB SSD - and it can be 100% Linux - then do the same for a 2nd example if it was a dual boot?
Never use FAT32 anymore unless absolutely mandatory - mandatory means there is a hardware device limitation which prevents using a better file system.
[LIST]
[*]If the storage is for Linux systems, use ext4 (ssd/hdd) or f2fs (flash USB/SD).
[*]If the storage is has to be unplugged and connected to other computers for access, use NTFS or exFAT.
[*]If the storage needs to be accessible over the network, then follow the Linux-Systems rules.
[/LIST]
Linux has 50+ different file systems. Each has a specific design goal. Some are trying to be fast. Some safe. Some want to limit writes which is good for SSD and flash storage lifespans. Some want POSIX capabilities. Some are compatible with MS-Windows or OSX. Most are a mix of those goals.  My 3 rules are trying to make life easy and simple. More experienced people (including me) could need some other file systems.

> **linuux said:**
> The other thing I was thinking about is what if you wanted to boot other Linux operating systems?  Is this a good/bad idea on an SSD?   Since, you have to worry about read/write cycles?  Or maybe it doesn't matter so much as long as the 'new installs/fresh installs' aren't done too often?   I only have experience with legacy hard drives so far and I never cared how often I re-installed or 'formatted/fresh installed.'

Today, reputable SSD makers have gotten the lifespan to be fairly high compared to just 5 yrs ago. All storage is going to die. That's what storage does - it dies.  Our goal is to keep it working as long as we need it and have it die when it becomes unimportant to our needs.  I have some spinning disks from 2003 that are still working well.  I have many more spinning disks that failed after 1-4 yrs of use, unfortunately.  I've had cheap SSDs fail after 2 yrs of use, but I have newer, reputable SSDs that are coming up on 3 yrs of use and still have less than 20% of their predicted "write" counts used.  So, in theory, those SSDs will last 15 yrs.  I'm hoping for 10 yrs from them. One is inside a laptop and I use it without any consideration for write counts at all.  The other is in a virtual machine server which usually has 10 VMs running 24/7/366. This one gets abused by all those VMs running and writing.

> **linuux said:**
> My current computer only has room for one drive - so I plan on getting a 1TB SSD and plan on dual booting Windows 10 and Linux (Ubuntu).
That's fine.  What are you doing for backups? Those are extremely important.
I wouldn't dual boot or duel boot.  About once a year, MSFT will decide it needs to "fix" the boot solution for you and that will break booting for any other OS.  OTOH, if you put MS-Windows into a virtual machine, it will think it is the only OS there and work fine for 90% of the reasons we still run MS-Windows.  Plus, you have access to both OSes at the same time ... or 10 OSes at the same time, if you like.  Virtual machines are pretty handy for all sorts of reasons.  Highly recommended instead of duel-booting.

> **linuux said:**
> Although, my plan in the future is to invest in a current gen Ryzen or Rocket Lake (Intel) computer - with M.2 NVME and maybe 2 SSDs - allowing for separate Windows 10 drive and a separate Linux drive - thus, allowing for more possible configurations. 
Invest?  Computers are like boats.  They rot, smell, take our money, and eventually sink.  I always find it odd when someone things putting a different OS on a different HDD somehow keeps those OSes separate.  There's only 1 boot EFI location.  That will be screwed by either Linux or Windows OSes. If it were me, I'd put the OSes on the SSD and data onto a spinning rush HDD. Heck, 1TB USB3 flash storage might be even more convenient.  I know people with 10 Linux systems on a 256G USB flash drive that they boot whichever Linux is needed.  A few of their Linux boots have persistent storage, so updates and data stored on the flash drive are separate from any storage inside their computer.

> **linuux said:**
> I read about separate root, home and swap partitions but I am inclined to think it's better to have less partitions than more - when dealing with solid state drives.   Right?  
Doesn't relate.  It is best to have the most convenient setup possible.  All SSD storage is virtual. The OS doesn't see what is happening inside the SSD.  If you want to increase the lifespan of an SSD, leave 20% of it unused.  Because it is all virtual, that means we don't need to not partition 20% or not allocate 20%, just leave 20% free.  If you use LVM, there are some other handy things possible.

In the links Oldfred provided are my disk layout recommendations.  I think at least 3-4 LVs are needed. If using LVM, size them smaller than you would for a partition.  All the LVs will be inside 1 huge partition, most likely.  See attachment for LVM relationships with PV, VG, and LVs to partitions. 
[ATTACH=CONFIG]288826[/ATTACH]

> **linuux said:**
> With the older computer I have, I would probably use a simple setup so just two partitions - one for Linux and one for Windows.   But, the question in this setup is how many partitions for the Linux setup (assuming, I use only one Linux OS)?   I typically have my data on a separate HDD - so even if I have some data in the /home directory, I will copy it to the HDD.   So, I am not too worried about the data in /home since I have a copy.

You really don't want only 1 partition per OS. That makes all sorts of simple assumptions and limits you from doing advanced stuff.  There's a reason we all drive cars and not unicycles. BTW, I can ride a unicycle. ;)

---

### Post by tea for one on 2021-07-17
> **TheFu said:**
> I always find it odd when someone things putting a different OS on a different HDD somehow keeps those OSes separate.  There's only 1 boot EFI location.  That will be screwed by either Linux or Windows OSes. If it were me, I'd put the OSes on the SSD and data onto a spinning rush HDD.

I agree - one EFI partition controlling two or more operating systems can be affected by updates from either OS.

However, each OS on a separate disk with its own EFI partition is a better solution.

---

### Post by oldfred on 2021-07-17
While I like to have an ESP on every drive, and it is required for external drives, UEFI controls boot.

With BIOS, I do not think any Windows or grub update would change which drive is booted if two drives. But with one drive, each would reinstall its boot loader into MBR, changing default boot.

With UEFI you only have one boot order setting whether using one ESP or multiple ones. So a major update from either Windows or Ubuntu/grub resets boot order to make that system the default. 

So if dual booting different systems with different boot loaders, major updates can change default boot.
An advantage of UEFI is that it is like having multiple MBR with BIOS. So you can at any time choose which system to boot from UEFI boot menu. Grub only boots working Windows, so fast start up or hibernation must be off. 
All flavors and many unofficial flavors of Ubuntu use an Ubuntu entry in UEFI. So only one grub to boot all installs. But other distributions may put a Fedora or a grub entry in UEFI, so you can directly boot another installs.

---

