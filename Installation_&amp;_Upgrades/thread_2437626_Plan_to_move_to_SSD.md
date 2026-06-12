---
title: "Plan to move to SSD"
date: 2020-02-26
forum: Installation &amp; Upgrades
---

### Post by yaminb on 2020-02-26
Hi all,

I'm trying to move my root partition to an SSD.

Current Setup is as follows:

```

/dev/sda - SSD - unallocated (500 GB)

/dev/sdb[1-5] - HD - Windows Partition

/dev/sdc1 - HD - Ubuntu root (500 GB) ~40 GB used
/dev/sdc2 - HD - Ubuntu swap (30 GB)
/dev/sdc3 - HD - Ubuntu Home (/home) (1.3 TB) ~300 GB used

```

My plan is to ONLY 'move' the root partition to the SSD. 
After I successfully do that, I will resize /dev/sdc to just be /home and /swap.

I've seen a few guides that look to copy the root partitions and then manually install grab / edit fstab
[https://www.pcsuggest.com/hdd-to-ssd-cloning-linux/](https://www.pcsuggest.com/hdd-to-ssd-cloning-linux/)

I've seen a few advocated cloning the drive... /dev/sdc1 clone to /dev/sda1

Any advice for those who went through it? Pitfalls?

Thanks,

---

### Post by oldrocker99 on 2020-02-26
It just might be easier and quicker just to reinstall. You do have to reinstall the apps, so you should make a list of the apps you installed, for easy-peasy installation. You'll probably want to install 20.04, anyway.

I have a M.2 SSD, which holds /, and the rest for a few large games which are slow-loading, and 1 1TB 2.5" SSD for more, and the two drives which hold the rest of my Steam games.

---

### Post by TheFu on 2020-02-26
Test your backup and restore procedures. You'll never have a better chance.  Lot of different techniques.  These forums are full of advice about that.

Comments about the current allocations:```

/dev/sdc1 - HD - Ubuntu root (500 GB) ~40 GB used
/dev/sdc2 - HD - Ubuntu swap (30 GB)
/dev/sdc3 - HD - Ubuntu Home (/home) (1.3 TB) ~300 GB used
```
```

/ - 25G  Anything larger is a waste.
swap - 4.1G the old rules of 2-3x RAM haven't applied since 4G of RAM became common.
/home - whatever, but perhaps keeping media files outside home would be smart?  
/media - whatever size needed.
```

IMHO.

Whatever is using so much on the / (FS root) needs to be cleaned up.  Seriously, 15G should be enough for /, so 25G is 10G more.

Why split /home from /media?  Backup techniques for never changinging media files don't need to be the same, complex, like what we require from /home/ backups.

If this system uses UEFI to boot, then /boot/ needs to be created. 
If the current system uses LVM, moving to different storage is easy.  You could create a mirror of / on the new storage, then break the mirror off the HDD leaving just the SSD with the files.  With LVM, we specify the path to the LV in the fstab.

[https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) has an LVM layout and a few sample commands.  Command output is better than word-descriptions. They show facts.

---

### Post by oldfred on 2020-02-26
If UEFI with gpt partitioning, you cannot easily copy a partition.
With gpt you have unique GUIDs in primary partition table, backup partition table at end of drive and in each partition that must match. If you copy a partition then they do not match and can cause major issues.  The partition tool gdisk may be able to repair, but much better to just to a new install and mount /home during install, but be sure NOT to format it.

---

### Post by yaminb on 2020-02-27
Thanks for the advice all.

Yes, I have UEFI and GPT partition tables.
I'll wait for 20.04 to come out to do the new install on the SSD.

In the mean time, Ill try and play with it to see if I can get it to work more for my own knowledge.
I was following this guide, but when I get to the installing Grub part.
[https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/](https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/)

>  
sudo grub-install --root-directory=/mnt /dev/sda
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.


I take it this means the EFI directory is not on the SSD.
I guess I partitioned it wrong or something. Any ideas on that?
I just created a new GPT partition table on the SSD and then an ext4 as /.
I didn't see any 'BOOT' flags on the HD, so I didn't enable the 'BOOT' flags on the SSD if that nees anything.

---

### Post by CelticWarrior on 2020-02-27
Yes, if you want to install and boot from that drive, you need to have an ESP (EFI System Partition). And that guide isn't applicable for UEFI installations.

If later you will be installing Ubuntu, it will create all the necessary partitions provided you boot the installer in UEFI mode and select the option to "Erase... Install" into a drive that is GPT already (it also allows UEFI installations in MBR with an ESP as well as a requirement, but perhaps it shouldn't?).

---

### Post by yaminb on 2020-02-27
@CelticWarrior

Can you help clarify my understanding.
Does each bootable drive need a EFI system partition?

I'm confused as to how I am booting right now with just the 2 HDs (not even worrying about the SSD).


> 
/dev/sdb1 - HD - NTFS system reserved (512 MB)
/dev/sdb2 - HD - NTFS recovery (530 MB)
/dev/sdb3 - HD - EFI SYSTEM PARTITION - FAT32 (100 MB)
/dev/sdb4 - HD - Microsoft reserved partition (16 MB)
/dev/sdb5 - HB - NTFS - data partition - 1.8 TB

/dev/sdc1 - HD - Ubuntu root (500 GB) ~40 GB used
/dev/sdc2 - HD - Ubuntu swap (30 GB)
/dev/sdc3 - HD - Ubuntu Home (/home) (1.3 TB) ~300 GB used


My Ubuntu HD (sdc) doesn't have any efi partition. So how am I booting from it? 
From my BIOS, if I choose to boot from the Ubuntu drive, is it actually first going to the sdb (windows drive) and using that partition? This sounds weird.

If not, then why can't my SSD boot with just a /root ext4 partition?

---

### Post by CelticWarrior on 2020-02-27
Only one ESP per system is required. Where the main system partition(s) is(are) doesn't matter. When the OSes are installed their installers write the bootloaders in the ESP pointing to the boot partition.

You can have ESPs in other drives (one per drive) but actually using it implies changing the drives' priority in UEFI settings. Dpoing this is useful for "portable" OSes - installed in an external drive - but in a machine with only multiple internal drives I usually have only one ESP for all OSes and that's it. You can do the same but then you have to keep the drive identified as 'sdb' and make sure this one also has the first priority in the UEFI boot settings. Likely you won't need to do anything to that effect. Likely everything is already set as it should with the original Windows. Ubuntu was installed later in a different drive and that's the same thing you should do now with the SSD replacing the current 'sdc'. Like before, the installer should pick up the existing ESP and install itself in the designated new drive. But if it doesn't then you can use "something else" and manually define the partitions to be used, including the ESP. In that installation step you will be choosing the current ESP (in sdb) -and- the partitions you will create there, which in your case you want to be only / (root), and then also select but don't tick format (obviously) your current /home.


In a nutshell, you'll be installing a whole new OS from scratch but using a previous /home partition (with your personal files and settings) instead of the problematic cloning of the root partition that is always a pain as commented above. So, the end result will be Ubuntu booting from the one and only ESP (sdb3) chainloading to the system partition (in the new SSD, likely sda1) and using 'sdc3' as /home, like before. Later you can delete the old root (sdc1) and reuse the space. And about that... Please do some preemptive cleanup for sanity, keeping in mind the following:

[LIST=1]
[*]The current root is absurdly big. With a separated /home, the root partition is only used to run the core OS and other software, so 20-25GB is more than enough to install and run lots and lots and lots of software. But make it bigger if it must be, it says *~40 GB used* in your current installation. Anything larger then say 50GB is a wast of space only.
[*]Speaking about wasted space... Your swap is also absurdly huge. In the current Ubuntu release a separated swap partition is no longer required, a swapfile is used instead. Therefore it's highly recommended to delete the old swap partition before installing the new Ubuntu in the new SSD, otherwise the installer will pick and use it as it is. Another reason to remove it is because it precedes 'sdc3' (/home), precisely the partition you want to move all the way to the left and resize to use the full drive after removing the old root and swap. You won't be able to do this with an (unmovable) swap partition in the middle of the drive (you could just reformat sdc1 for other purposes but it makes more sense using the 2TB drive for /home only or /home plus an additional data partition).
[*]As explained in #1 you don't need to use the whole SSD for the new root. So, you can also use the remaining space to another data partition.
[/LIST]

---

### Post by yaminb on 2020-02-27
@CelticWarrior

Really appreciate that explanation.
Yes, I do plan to do a fresh install on the SSD when 20.04 comes out. 
I am using this as a learning opportunity right now, especially with respect to the boot sequence.


If I did want to make the SSD bootable in the current system, how would i 'install grub' to it while using sdb3 as the EFI partition?
Or does this have nothing to do with installing grub why the SSD is not currently bootable?

---

### Post by CelticWarrior on 2020-02-27
> **yaminb said:**
> If I did want to make the SSD bootable in the current system, how would i 'install grub' to it while using sdb3 as the EFI partition?
Or does this have nothing to do with installing grub why the SSD is not currently bootable?

There's nothing wrong in keeping the current drive as it is, many OSes can be added and coexist in its EFI partition. You will keep this drive as it contains the /home you want to use ;). If you were to remove or replace it then re-configuring the boot order would be required. In your case I see no point in changing, just install Ubuntu in the SSD (again, not whole drive) and select the current ESP. But if you want to change things...

Start by changing the boot drive priority in UEFI settings making the SSD the first drive.
Boot Ubuntu installer and select "something else" to create partitions manually, pretty much how how commented in a previous post, but this time create a small FAT32 formatted partition then select EFI type (this will be your new ESP), then & (root) as large as you need and that is no more than 50GB being extremely generous. Next select the current /home in the other drive (do not select format). But before all that, assuming you'll be using Gparted in a live session, right-click the swap partition > swapoff (turns swap off) and delete that 30GB partition (the newly installed Ubuntu will be using a swapfile that needs no user configuration and is good for 99% of the users, for your convenience. Ignoring this will result in the installation using that swap partition instead of the default. Changing that after installation is not hard but takes time and attention.

In short, the only different is changing the boot drive priority to the drive you want to make bootable and then install to a new ESP. After having the new Ubuntu installed and running all the allocated space can be easily managed with GUI tools - Disks (default) or Gparted (runs in the live session but not installed by default).

---

### Post by oldfred on 2020-02-27
I prefer to have an ESP on every drive, but that is not required. It is more for emergency boot in case main boot drive with ESP fails or has issues. But I also have several emergency boot flash drives. And second or third ESP boots an install on that drive for testing or experimentation and only then grub may find my main working install and let me also boot it.

Ubuntu's Ubiquity installer is the only one that only wants to install grub to first drive's ESP, usually sda or first NVMe drive. And then that drive must have an ESP. 
I have installed several other distributions just to test how grub works and each let me install to sdb. Ubuntu will not without some effort on changing drive settings or mounts before or during install.

Since I just installed a new NVMe drive to my system, I did a full install of 20.04. But have 18.04 on old SSD as fully functioning system. 

Oldfred's partitions with new NVMe Feb 2020, I leave some space unallocated.
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)

---

### Post by yaminb on 2020-02-27
Just an update.

I installed a fresh Ubuntu 18.04 to the SSD. 
Everything seems to work.

I just did a custom install choosing my  /home on the old HD
I chose the same username as I did before and everything came up fine on my same account.

---

### Post by yaminb on 2020-02-27
Damn. that SSD made a difference to the start time. 
> 
systemd-analyze blame
          6.305s NetworkManager-wait-online.service
          4.984s plymouth-quit-wait.service
          2.119s e2scrub_reap.service
          1.758s snapd.service
          1.036s dev-sda2.device



I used to have entries like SNAP taking like 20 seconds.

---

### Post by CelticWarrior on 2020-02-28
> **yaminb said:**
> Damn. that SSD made a difference to the start time. 


I used to have entries like SNAP taking like 20 seconds.

That's why we use them ;)
But, as commented before, the difference is after UEFI, the difference is the OS running from a much faster drive now. The location of the EFI partition makes no difference.

---

### Post by yaminb on 2020-02-28
@CelticWarrior

Quick opinion question. Now I basically have 2 functional linux OS. One on the SSD and the old one on the HD.
Someone mentioned that this is kind of ideal as now I can say try out an OS in the HDD partition.

Obviously anything can go wrong, but from your experience, how much 'trouble' can you get yourself in by sharing the /home while trying out distros?

Just as a current example. I was on 19.10 in my HD. I installed 18.04 LTS on the SSD. They shared a /home.
When I booted in the SSD and tried to run firefox, it complained of running an older version. Assuming of course the firefox settings stored in home were for the 19.10 version. The 18.04 version detected this settings issue and warned about it.
In the firefox case, it wasn't an issue as I just updated the firefox to the latest and it was fine.

But assuming it's not a SNAP package, how much trouble do you typically get into if your programs are sharing the same /home settings. I'm more interested in 'core' programs like GNOME desktop or things that would impact basic functionality of Ubuntu.

---

### Post by CelticWarrior on 2020-02-28
> **yaminb said:**
> 

But assuming it's not a SNAP package, how much trouble do you typically get into if your programs are sharing the same /home settings. I'm more interested in 'core' programs like GNOME desktop or things that would impact basic functionality of Ubuntu.

I never tried a setup with "shared" /home but I imagine that different settings may well be a cause of concern. It may happen that the newer release installs a newer version of some program and that version implies a change in the user settings; then running the older release and the same but older version of said software may not work. But this situations are rare, I think.

---

### Post by oldfred on 2020-02-28
I always keep /home inside / with all my installs. And have a large data partition where all my Documents, Music, Pictures, etc are. I then can mount data into all installs, but can experiment with settings to make sure I do not also change settings in my main working install that I may not want.

While systems are designed to upgrade, so an application my change a file to support its new version, the old version may not then support that. I would not use /home partition in multiple installs unless also using different users so then separated.

---

### Post by dragonfly41 on 2020-02-28
> [COLOR=#000000]Quick opinion question. Now I basically have 2 functional linux OS. One on the SSD and the old one on the HD.[/COLOR]
[COLOR=#000000]Someone mentioned that this is kind of ideal as now I can say try out an OS in the HDD partition.[/COLOR][COLOR=#000000]

My pennyworth.  I have external SSD with Ubuntu 18.04 (this one I'm currently using) and internal drive with Windows 10 and older Ubuntu 16.04 (just for emergency boot). I also have another external USB drive with Ubuntu.

I find rEFInd to be useful and complementary to grub options.

[This is my reference blog]("https://forums.linuxmint.com/viewtopic.php?t=287353"). Note the tips about enabling/disabling boot flags. But the better option is to install rEFInd in /boot/efi/.[/COLOR]

---

