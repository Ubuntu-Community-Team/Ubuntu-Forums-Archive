---
title: "Stupidity with broken win2k boot after ubuntu install"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by CheapAlert on 2005-10-08
I'm in one freaky situation here

- First, I had Win2k installed, then I tried a (quite failing) SLAX installation, which replaced NTLDR on hdb.

- I then installed Ubuntu but Grub installed to hda. I had to go in the CMOS and change my boot order so I can access Ubuntu.

- From Grub, booting Windows 2000 (it found it during setup though) just leaves a Grub > prompt.

- Kfloppy refuses to format any disks, also grub-install can't seem to find the disk, and it just simply won't copy files properly either (doesn't copy at all, though visually it has "ghost" files in the window). It isn't my disk drive, as it can read win98se boot disks fine without error.

What should I do, really? All the Grub HOWTO's i've googled don't deal with a broken br for Win2k.

Win2k is physically installed on hda6.

btw, here are my partitions, copied directly from /etc/fstab:

/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5   /media/hda5 ntfs nls=utf8,umask=0222 0 0
/dev/hda6   /media/hda6 ntfs nls=utf8,umask=0222 0 0
/dev/hda7   /media/hda7 ntfs nls=utf8,umask=0222 0 0

/dev/hdb1 /media/hdb1  vfat iocharset=utf8,umask=000 0 0
/dev/hdb5 /media/hdb5  vfat iocharset=utf8,umask=000 0 0

I don't wanna lose my Win2k install, and I don't wanna lose my kubuntu install either :P

Help?

---

### Post by aysiu on 2005-10-08
The output of ```
sudo fdisk -l
``` might be more helpful than the /etc/fstab in fixing the problem, but have you tried simply [restoring Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113)?

---

### Post by CheapAlert on 2005-10-08
okay!
```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3892    31262458+   7  HPFS/NTFS
/dev/hda2            3893       15730    95088735    f  W95 Ext'd (LBA)
/dev/hda3   *       15731       19457    29937127+  83  Linux
/dev/hda5            3893        7784    31262458+   7  HPFS/NTFS
/dev/hda6            7785       11676    31262458+   7  HPFS/NTFS
/dev/hda7           11677       15568    31262458+   7  HPFS/NTFS
/dev/hda8           15569       15730     1301233+  82  Linux swap / Solaris

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1231     9887976    c  W95 FAT32 (LBA)
/dev/hdb2            1232        4872    29246332+   f  W95 Ext'd (LBA)
/dev/hdb3            4873        4982      883575   83  Linux
/dev/hdb5            1232        4862    29165976    b  W95 FAT32
/dev/hdb6            4863        4872       80293+  82  Linux swap / Solaris

```

The hdb3 and hdb6 were another ubuntu installation attempt actually, i'll be ridding those partitions, they're insufficient anyway so ignore those. They aren't part of the problem

---

### Post by aysiu on 2005-10-08
Did you try the HowTo I linked to on restoring Grub?
Who's currently in charge of the Master Boot Record now? Windows 2000? Ubuntu? Slax?

Generally, the Windows entry looks something like this:
```
title           Microsoft Windows 2000
root            (hd0,0)
savedefault
chainloader     +1
``` This assumes, of course, that your Win2K is at /dev/hda1

---

### Post by CheapAlert on 2005-10-08
Ubuntu's grub is controlling the mbr. M$'s ntldr was overwritten by Slax, which is still resident on hdb's br. I might try that Grub thing, though it might not work unless I do something with Windows 2000 first. I did pop in my win2k cd earlier and accessed the recovery console, tried to run fixmbr, but felt risky as it scared me with a vague "bad stuff will happen to your partitions and you'll lose stuff if you run this!" message, so I was unsure from there.

Should I run fixmbr anyway? :)

---

### Post by aysiu on 2005-10-08
I realize you have 200 GB of hard drive, but is there any place for you to back up your files? After all these crazy installs (Slax and two Ubuntus), it almost might be worth just reformatting. But even if you don't reformat, you probably still want to back up your files.

So if Ubuntu is in charge of the MBR, does that mean you can boot into Ubuntu?

---

### Post by CheapAlert on 2005-10-08
yeah, i'm in ubuntu right now as i type :) I just can't boot into Win2k. As for backing up, that COULD be an option as i've got a PX-716A cd/dvd-rw and alot of cd-r's :D though i have alot of projects that may exceed 600mb. Also i'm using the drive to back up another dead drive of mine with all my 4gb drive's files, i'd hate to lose that. Actually one of the partitions i have of my large drive were just made for compatibility's sake, as my motherboard doesn't like the 160gb hd much, so i only have 120 "safe" gb (the rest of the gb would corrupt the partition's and the partition would be unformatted)

i'm going to run fixmbr from the win2k recovery console, then insert my ubuntu cd and install grub.

---

### Post by CheapAlert on 2005-10-08
Okay

- Windows 2000 had to be reinstalled.
- win2k installs just fine :D
- fixboot and fixmbr don't do anything at all
- ubuntu installer's partitioning tool complains it can't find a root drive and wants me to set one, even though i don't see how
- grub installer refuses to install without a /root/
- aborting the installation, leaves booting windows as "Error: Operating System not found"
- i insert my slax live cd to report this

:(

---

### Post by aysiu on 2005-10-08
It might be possible to save your installation, but I hate to say it... it sounds as if a clean reinstall would be best (you also have quite a large number of partitions). If you have a DVD-RW drive, get some DVDs and back it all up (data really should be backed up all the time anyway, even if everything's working perfectly). If you have a friend with a large external hard drive, that'd help, too.

I'd back up all your files (including your bookmarks and emails), reinstall Windows 2000 on your first hard drive, then reinstall Ubuntu on your second hard drive, placing Grub on the MBR.

---

### Post by CheapAlert on 2005-10-09
Things are working now

- I completely reformatted the big 160
- I made several partitions - one 7gb ntfs (win2k), one 10gb ext3 (ubuntu), a 60gb fat32 partition, a 40gb fat32 and another 41gb fat32.
- Installed Windows 2000 first on the appropriate partition
- Installed ubuntu after
- IT WORKS OMG!

Thanks!

---

### Post by aysiu on 2005-10-09
Awesome.

---

### Post by CheapAlert on 2005-10-27
That awesome just got awful.

I did nothing to the system (i did keep it on for a few days prior to this), and now windows 2000 can't boot. It just stops at "Disk error", next line asking to continue, then hitting a key will result in an attempt to boot the unused broken SLAX install on the second physical drive (hdb).

The partitions are all still intact, Windows 2000's NTFS partition still can be read in Kubuntu

Here's my GRUB loader list:
[http://pastebin.com/407342](http://pastebin.com/407342)

I really don't want to reinstall win2k again :(

---

### Post by CheapAlert on 2005-10-28
pardon my bump

---

### Post by CheapAlert on 2005-11-17
Alright, still stuck here. Returning to this issue If I change my boot order in the BIOS to boot with hdb first, then reinstall Windows 2000 on hdb1, will GRUB/Linux be affected on hda? I really don't want to lose my linux either. After the install i'd change the boot order back again and edit GRUB to boot the second drive.

Will this work out?

---

### Post by CheapAlert on 2005-11-21
it's all working, and I think I found the root of my problem. Interesting post mortem follows:

It appears, copying alot of stuff/installing on my /hda8/ (H:) partition really messed up the /hda1/ (C:) partition, where the NT boot loader is. So if my windows ever breaks again, i'll find C: broken and just reformat the partiton and copy my backed up bootloader files into that partition again, and windows works again.

I did reinstall Windows, however it didn't install into hdb. Hmm. But at least it works!

---

### Post by CheapAlert on 2005-11-27
The saga continues.

I did try making a new partition in Windows 2000 (on NTFS) then it did an emergency reboot, and Grub has an error 17! Used Knoppix, and found only /mnt/hda1 (the boot drive) and /mnt/hda2 (the ubuntu drive) are accessible

WHAT HAPPENED DO I REALLY NEED TO START OVER AGAIN :(

---

### Post by ormus on 2005-12-07
after many yrs of having problems with dual boot etc.. i now only install 1 OS per hdd. i use a caddy system so that i can swap drives very quickly.
with the price of hdd falling so much these days, i dont see any reason whatsoever to have a dual boot hdd.

ps. very important. anyone doing any dual booting MUST backup their data first.
(unless you couldnt care less about the familys piccys collected over the last 3 yrs!)

---

