---
title: "Can't install ubuntu on SSD Samsung NP530UC-05"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by dibo on 2013-04-19
Hi,

I have ultrabook Samsung NP530UC-05 which has 24GB SSD (used as cache by Windows 8) and 500GB HDD. I'm trying to install Xubuntu 12.10 64bit on SSD from pendrive following by this article: [http://www.childsplay.mobi/blog/?p=83](http://www.childsplay.mobi/blog/?p=83) . Installation went ok. But after reboot I see only samsung boot window with HDD ID. It can't find grub. Googling about this issue I see that some people have no problem with installations and others have. I don't know what it depends on.

When installing, gparted showing me this list:

sda: HDD 500 GB
sdb: Pendrive 2GB
sdc: SSD 24 GB

I deleted all partitions and created:

sda
 |- sda1 6 GB swap
 |- sda2 20 GB /var
 |- sda3 200 GB /home
 |- rest free for truecrypt partition
sdc
 |- 100 MB /boot
 |- 23.9 GB /

And as boot loader device I point to SSD because if I leave default HDD then I get grub error on the end of installation. "/boot" partition is as "solution" which I googled, but it doesn't work without it too. So I stuck. I found similar problem for windows users. Solution which worked for them was install from external DVD instead of pendrive. Is it possible that it can be solution for linux? I don't know how it work, but from my list above, pendrive (sdb) is second, SSD (sdc) is last. When I unpluged pendrive after installation, is it possible that SSD move to sdb from sdc and grub remember that SSD was on sdc? I want buy external DVD anyway, but maybe you know solution which I can try now?

Regards

---

### Post by Frogs Hair on 2013-04-19
You may have seen theese.  

[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

[http://labnotes.decampo.org/2012/12/installing-ubuntu-1210-on-ssd-part-1.html](http://labnotes.decampo.org/2012/12/installing-ubuntu-1210-on-ssd-part-1.html)

[http://labnotes.decampo.org/2012/12/installing-ubuntu-1210-on-ssd-part-2.html](http://labnotes.decampo.org/2012/12/installing-ubuntu-1210-on-ssd-part-2.html)

---

### Post by oldfred on 2013-04-19
Was this SSD part of an UltraBook. That uses RAID and would leave RAID meta-data on drive that interferes with grub installing. Grub would want to install to the RAID.

ARe you booting in UEFI or BIOS mode?

May be best to post link:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by dibo on 2013-04-20
Ok. Here is new info. I prepared screenshots. First installation and then bios repair

Here are my partitions before installation:
[http://ubuntuone.com/5AciyI3qchUu5ksufodqpk](http://ubuntuone.com/5AciyI3qchUu5ksufodqpk)
[http://ubuntuone.com/6cwc62RG9iQfYENPRS22qB](http://ubuntuone.com/6cwc62RG9iQfYENPRS22qB)

Boot menu after installation:
[http://ubuntuone.com/4GQj94Rcz5tqYjd6YjwtET](http://ubuntuone.com/4GQj94Rcz5tqYjd6YjwtET)

And my bios configuration (note that there is no info about SSD, it is hidden? GParted see it). I have only one AHCI option which I manually enabled
[http://ubuntuone.com/2o2qJxgEKuYH5WXCv6ik8B](http://ubuntuone.com/2o2qJxgEKuYH5WXCv6ik8B)
[http://ubuntuone.com/0enKQbWAFg1yPv9LmOw9Yk](http://ubuntuone.com/0enKQbWAFg1yPv9LmOw9Yk)
[http://ubuntuone.com/0weYEKNir4rxmU8qJkvCD3](http://ubuntuone.com/0weYEKNir4rxmU8qJkvCD3)
[http://ubuntuone.com/66TEb8FSQHHrkqBcoPcCnD](http://ubuntuone.com/66TEb8FSQHHrkqBcoPcCnD)
[http://ubuntuone.com/5RLI9SUu6oD2r0npuXrrPC](http://ubuntuone.com/5RLI9SUu6oD2r0npuXrrPC)
[http://ubuntuone.com/2Jxxxi955bYWWdKKLX36Cd](http://ubuntuone.com/2Jxxxi955bYWWdKKLX36Cd)

Now Bios-repair. This is report before repairing:
[http://paste.ubuntu.com/5724021/](http://paste.ubuntu.com/5724021/)

First repair try give me this error (sorry for not English):
[http://ubuntuone.com/5qXgBr3sfGBakiDtwL0z3r](http://ubuntuone.com/5qXgBr3sfGBakiDtwL0z3r)

So I run GParted which at startup give me this error:
[http://ubuntuone.com/4fFUfoXV9q6AINEdCfwMre](http://ubuntuone.com/4fFUfoXV9q6AINEdCfwMre)
On SDC is my mounted pendrive, so I ignored it.

I created bios_grub partition on SSD (where /boot and root / are) and run boot-repair again. Now it repaired something. Here is log after repair:
[http://paste.ubuntu.com/5724055/](http://paste.ubuntu.com/5724055/)

But after reboot I still see samsung boot menu with my HDD only :( .

**Edit: **I give up. If I can't install ubuntu on SSD I will try on HDD. But for what I can use SSD as mount point to speed up little linux? For /var?

---

### Post by dabl on 2013-04-20
> **dibo said:**
> 
And my bios configuration (note that there is no info about SSD, it is hidden? 

This is the problem -- I have the same problem with my OCZ RevoDrive PCI-e SSD.  Your BIOS does not recognize your SSD as a bootable device, so (unless there is a BIOS upgrade to fix this) you cannot boot from the SSD.  However, you can run Linux from the SSD.

On a bootable device (i.e. a hard drive that your BIOS recognizes) make a 500MB partition, format it ext2, and set the "boot" flag on it.  Also make a partition on the same hard drive that is slightly larger than your installed memory, and format it "linux swap".  Format your SSD as a single partition to ext4.  With only 24GB of space on the SSD, you will certainly want an ext4 data partition elsewhere on an hdd.  You can decide how big that needs to be.

With your Ubuntu installer, choose "manual" partitioning (it's been awhile since I installed Ubuntu -- maybe the nomenclature is different but you DON'T want "automatic").  You want to mount the 500MB partition on the hdd as /boot, and the SSD as / (including /home).  The installer should find the swap partition automatically.  Once your partitions are set, complete the installation and let grub be installed to the mbr of the hdd that has /boot on it.

That should get you a bootable system, running Ubuntu on the SSD.  To extend the life of the SSD, edit /etc/fstab and add the mount option "commit=nnn", which will slow down the default journal commit interval from every 5 seconds to something slower.  I personally use commit=120 (every 2 minutes).  There is a consequential increase in the risk of data loss from a power loss -- be aware of that.

There are other tweaks you can do to extend the life of your SSD, such as mounting selected filesystems as tmpfs, and setting the browser cache(s) in /run/shm.  Google should help you find those.

You'll also need to edit /etc/fstab to add your DATA partition, and then symlink your data folders in to your /home folder, so you can keep your videos, music, images, etc. off the SSD.

I hope this is helpful.

---

### Post by oldfred on 2013-04-20
Because you have gpt partitions, you will need a bios_grub partition on sda. Then Boot-Repair will install grub to sda from your current install in sdb. It shows it gave an error when it tried since you did not have the bios_grub partition.

      >  Reinstall the GRUB of sdb2 into the MBR of sda
/usr/sbin/grub-bios-setup: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
/usr/sbin/grub-bios-setup: error: embedding is not possible, but this is required for cross-disk install.
grub-install /dev/sda: exit code of grub-install /dev/sda:1
grub-install (GRUB) 2.00-7ubuntu11,grub-install (GRUB) 2.



           In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB's core.img is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

Some others that did seem to be able to boot from sdb, but may have kept UEFI?
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by dibo on 2013-04-20
> **dabl said:**
> This is the problem -- I have the same problem with my OCZ RevoDrive PCI-e SSD.  Your BIOS does not recognize your SSD as a bootable device, so (unless there is a BIOS upgrade to fix this) you cannot boot from the SSD.  However, you can run Linux from the SSD.

On a bootable device (i.e. a hard drive that your BIOS recognizes) make a 500MB partition, format it ext2, and set the "boot" flag on it.  Also make a partition on the same hard drive that is slightly larger than your installed memory, and format it "linux swap".  Format your SSD as a single partition to ext4.  With only 24GB of space on the SSD, you will certainly want an ext4 data partition elsewhere on an hdd.  You can decide how big that needs to be.

OMG you are my hero! Finally work! Linux booting 5 seconds! :D . And just like that? Everything should work now? I didn't find your solution anywhere. Some poeple just normally installed on SSD and everything worked without extra /boot mounting point. But nevermind. Thanks again

---

### Post by dabl on 2013-04-20
Great -- yes, it all should work that way!  Here's my coolest tip for SSD tweaking:

Eliminate many SSD writes by setting your browser cache in /run/shm (i.e. in memory). (Not a bad security enhancement, either, to have the cache go "poof" after each reboot!). For example, in the Firefox/Iceweasel address bar we enter "about:config" and confirm the warning. Now right-click in the white space and choose "New ==> String" and we create a new entry called:

"browser.cache.disk.parent_directory"

After double-clicking the new string, we assign it the value:

"/run/shm/firefox-cache"

Now as user in the terminal create a directory:

```
mkdir /run/shm/firefox-cache
```

After a Firefox restart, browser caching happens in memory, not on the SSD.

For chromium-browser, the cache location is set with the &#8220;--disk-cache-dir=&#8221;DIRNAME&#8221; launch command option. So to outsource the chromium-browser cache:

```
mkdir /run/shm/chromium-cache
```

Open the chromium-browser launch icon for editing, change to the &#8220;Application&#8221; tab, and edit the start command to read as follows:

/usr/bin/chromium --disk-cache-dir=/run/shm/chromium-cache %U

The new browser cache directory in /run/shm will not survive a reboot. To automate this process, put the following &#8220;auto_browser_cache.sh&#8221; script in your ~/.kde/Autostart folder (for KDE users, or the autostart folder in Gnome/Unity), and then &#8220;chmod +x&#8221; to make it executable:

```
#!/bin/bash
NEWDIR=/run/shm/chromium-cache
mkdir "$NEWDIR" &
sleep 1
NEWDIR1=/run/shm/firefox-cache
mkdir "$NEWDIR1" &
sleep 1
NEWDIR2=/run/shm/opera-cache
mkdir "$NEWDIR2" &
#end
```



Analogous cache outsourcing configuration can be made for other browsers, if they allow the user to specify the cache location, and the startup script can be adapted to add directories for each browser that the user wants to run.

NOTE: For a desktop system that remains booted for long periods, and depending on the memory capacity and browsing activities, the outsourced browsing cache could grow to a problematic size and need to be manually cleared to avoid sending the system into swapping.

---

### Post by dibo on 2013-04-20
Two questions:
1. I mounted my /home partition on HDD, not on SSD like you suggested. Is it bad? I want more space on home than 24GB SSD
2. Why worrying about browser cache? I mean, I never had SSD disk, they are less durable? Browser cache on SSD can slow down it?

---

### Post by dabl on 2013-04-20
> **dibo said:**
> Two questions:
1. I mounted my /home partition on HDD, not on SSD like you suggested. Is it bad? I want more space on home than 24GB SSD
2. Why worrying about browser cache? I mean, I never had SSD disk, they are less durable? Browser cache on SSD can slow down it?


1.  It is not "bad", it is OK.  I personally like the speed of the SSD for commonly used files in /home (the .config files and little things like that).  But of course you only have 24GB total for the system.  If you include /home under "/" on the SSD, then you can symlink it the big data directories from another partition on the hdd.  That way your big data (MUSIC, VIDEOS, IMAGES, etc.) shows available in /home, but it is not really on the SSD, it is on the hdd.

2.  Browser writes many, many small files in the cache all the time you are browsing.  SSD life is limited by write/erase cycles.  So if you put the browser cache in memory, it results in much less writing on the SSD.

Those are just suggestions.  I have 4 or 5 SSDs, they are all 3+ years old and none of them have any problems.

---

