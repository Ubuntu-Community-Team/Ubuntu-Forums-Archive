---
title: "[boot-repair] Unable to boot Windows after moving partition to SSD"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by spontex on 2012-09-28
Hi,
I just moved my Linux and Windows partitions on my new SSD. Thanks to boot-repair (which was [updated]("http://ubuntuforums.org/showthread.php?p=12264895#post12264895") at the occasion) , I am now able to boot again under Linux.
But I still have a problem when booting my Windows partition: when booting, I get:
 ```
Status: 0xc000000e   Info: The boot selection failed because a required boot device is inaccessible
```When I moved my Windows partition, I did not move the 100 MB partition preceding it.
I believe that Windows looks for my old disk, which I would like to get rid of.
Is there any way to fix the Windows boot devices list so that it will run the adequate partition? I am a bit reluctant to use the Windows repair tool on the installation CDROM because I believe it may have crashed my partition tables the last time I used it.
What is the best way to proceed?
Here is the boot-repair log: [http://paste.debian.net/193748/](http://paste.debian.net/193748/)
Thanks

---

### Post by Mark Phelps on 2012-09-28
> **spontex said:**
> ...
Is there any way to fix the Windows boot devices list so that it will run the adequate partition? I am a bit reluctant to use the Windows repair tool on the installation CDROM because I believe it may have crashed my partition tables the last time I used it.
What is the best way to proceed?


The best way is to boot from the Windows Repair CD and run Startup Repair at least three times.  When you migrated to the SSD, you failed to migrate the partition containing the Win7 boot loader files.  The Repair CD will recreate those, but it might take up to three passes for them all to get written.

You could have saved some trouble if you had asked about this BEFORE you made the move.  I would have told to you install EasyBCD (for free) and use its feature to move the boot loader to the Win7 OS partition.  Then, when you migrated the partitions, the boot loader would already have been there.

---

### Post by spontex on 2012-09-28
> **Mark Phelps said:**
> You could have saved some trouble if you had asked about this BEFORE you made the move.  I would have told to you install EasyBCD (for free) and use its feature to move the boot loader to the Win7 OS partition.  Then, when you migrated the partitions, the boot loader would already have been there.

I will check if I still have this partition or if I can restore it using TestPart. Else I will run again the repair 3 times.
Thanks.

---

### Post by darkod on 2012-09-28
I think you will also need to set the boot flag on the windows partition first. The repair process looks for it so it can put the files there. I doubt any repair process will work without a boot flag.

Also, I don't know how you moved it, but usually partitions on hdd are not optimized for ssd. I would have made a clean install of windows in your place (I actually did it about a month ago).

---

### Post by spontex on 2012-09-28
Thank you. I have put the boot flag using GParted.

---

### Post by oldfred on 2012-09-28
Grub does not use boot flag, but Windows has to have it to boot directly or to know what partition to make repairs to. In Windows it is the active partition.

Windows also has information on the start & size of the Windows partition that has to match the partition table. Since  you move it, that does not match. Often chkdsk will repair it, but not always.

You also have another issue.
> /dev/sda4 ends after the last sector of /dev/sda

First backup partition table:
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by spontex on 2012-09-29
> **oldfred said:**
> You also have another issue.

First backup partition table:
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I just ran fixparts on my /dev/sda drive. The doc says that sometimes just starting it will fix the partitions table. This is what happened. However, now I have another problem: when I start GPArted, I get the following error message about my linux swap partition:
```

spontex@bureau ~ $ sudo gparted
[sudo] password for spontex: 
======================
libparted : 2.3 
====================== 
The kernel was unable to re-read the partition table on /dev/sda5 (Device or resource busy).  This means Linux won't know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/sda5.

```Of course, rebooting did not change anything. Is there a way to go forward and fix it? I would really like to have clean partitions before I start the Windows repair utility. If I cannot clean it then I will just backup the data on this partition, format it and restore the data, though it might be long.

By the way, I just saw that I kept my old 100 MB partition on my other hard drive. May it still be used?

The latest BootInfo report for my PC  is available here: [http://paste.debian.net/194271/](http://paste.debian.net/194271/)

---

### Post by darkod on 2012-09-29
What did you expect to change with sda5? It looks normal. It's on the other disk and was never touched by fixparts I guess.

That looks like only a warning because if you were running live mode it loads the swap partition. That's why it's reported as "busy, working". It just wants to let you know that any possible changes made to it will be active after the reboot since the partition was mounted when those possible changes were done.

If no changes are done, nothing will change after reboot and it doesn't need to because there were no changes to swap to start with.

If you boot ubuntu does it not mount swap correctly? Does it not work?

PS. And for future reference, I think next time it's better simply to copy the data, NOT the partition, especially if the target disk is smaller. Make the desired partition(s) on the new disk, and then use something like cp -ax or the fsarchiver program (which is very good for backup) to make a backup and then restore it on the partition on the new disk. That way you avoid problems with the partition table when copying big partition onto smaller disk. That is designed to copy the partition, not only the data. Personally I can't see it as useful especially when the target partition is smaller than the source.

---

### Post by spontex on 2012-09-29
Hi,
I am currently running Linux Mint from sdb1, not a Live OS.
The initial problem was on sda4 (see above:                               /dev/sda4 ends after the last sector of /dev/sda), so on the same disk as sda5.

Running fixparts fixed it but created this other problem which I did not have before with my swap partition. [Fixparts documentation]("http://www.rodsbooks.com/fixparts/") states: "FixParts checks the validity of the partitions it finds on your disk and will automatically (and silently) make adjustments for certain problems it finds. Thus, you may discover that your partition table is fine at this point. It's also possible that you'll see some changes in primary vs. logical status, or even omitted partitions.". This is what happened here, I think: I do not have my old problem with the partition exceeding the total disk space anymore. Instead, I have this new one :-)
Under GParted, my Linux swap is seen as "Unknown" file system.
My swap partition is not mounted anymore by Linux Mint:
```

spontex@bureau ~ $ sudo swapon --all --verbose
[sudo] password for spontex: 
swapon: impossible de trouver le périphérique UUID=d8f383a2-1c38-4e23-b768-1fc8b67c2ffd
```About the "cp -ax" method: Is it not only for data partitions? Does it work with system partition (e.g. Windows partition)? 
Would it be better than the GParted method I used? Because my new Windows partition (sdb3) is here, I can mount it and see it under Linux Mint but I cannot boot it anymore.
When I first searched for "move linux windows partition ssd" I found a lot of advices to use Copy/Paste under GParted. It worked well for Linux, not for Windows (probably this 100 MB partition I did not copy...).
Thanks!

---

### Post by darkod on 2012-09-29
And where is sda4 now?

As for moving windows to a SSD, I thought you were talking only about the linux partitions. I would never copy/move win7 from a HDD to a SSD. I would always do a clean install (I actually did that few weeks ago after buying my first SSD).

It detects the SSD during install and installs in a different way. I am not sure an installation copied from a HDD would ever use the SSD in the optimal way it's supposed to use it.

As for copying, actually using Nautilus (the file browser) should be enough for windows and other ntfs partitions since permissions are written in a different way.
For linux partitions, to keep the ownership and permissions you would use the cp -ax. I did that when moving my /home partition from the HDD to the SSD, everything worked fine, without a glitch. All files had correct ownership and permissions transferred.

---

### Post by darkod on 2012-09-29
As for swap, I now noticed in the results in the blkid section that the UUID for sda5 is not shows any more. It somehow got corrupted. So when fstab is looking for that UUID to mount it as swap, it doesn't find anything.

Open Gparted (if you prefer using it) and reformat sda5 as swap area again. Save changes and close Gparted.

Then open terminal and check the new sda5 UUID string with:
sudo blkid

Note it down.

Open /etc/fstab for editing with sudo permissions, and replace the old UUID with the new one. You can open it for editing for example with:
gksu gedit /etc/fstab

Save and close /etc/fstab. Reboot and it should be fine.

---

### Post by spontex on 2012-09-29
> **darkod said:**
> And where is sda4 now?
I think it is now sda2 (an extended partition containing sda5 and sda6).

> **darkod said:**
> As for moving windows to a SSD, I thought you were talking only about  the linux partitions. I would never copy/move win7 from a HDD to a SSD. I  would always do a clean install (I actually did that few weeks ago  after buying my first SSD).

Ok, I will do a clean install, perhaps with the Windows 8 Preview.

> **darkod said:**
> It detects the SSD during install and installs in a different way. I am  not sure an installation copied from a HDD would ever use the SSD in the  optimal way it's supposed to use it.

There is a trick to "align" the partition but you are right, I should reinstall Windows (and Linux?)

> **darkod said:**
> As for copying, actually using Nautilus (the file browser) should be  enough for windows and other ntfs partitions since permissions are  written in a different way.
I like rsync for big amount of data so I will use it.

> **darkod said:**
> For linux partitions, to keep the ownership and permissions you would  use the cp -ax. I did that when moving my /home partition from the HDD  to the SSD, everything worked fine, without a glitch. All files had  correct ownership and permissions transferred.
I did copy/paste in GParted for my Linux home and it was copied Ok.

> **darkod said:**
> As for swap, I now noticed in the results in the blkid section that the UUID for sda5 is not shows any more. It somehow got corrupted. So when fstab is looking for that UUID to mount it as swap, it doesn't find anything.

Open Gparted (if you prefer using it) and reformat sda5 as swap area again. Save changes and close Gparted.

Then open terminal and check the new sda5 UUID string with:
sudo blkid

Note it down.

Open /etc/fstab for editing with sudo permissions, and replace the old UUID with the new one. You can open it for editing for example with:
gksu gedit /etc/fstab

Save and close /etc/fstab. Reboot and it should be fine.
I believe I will now format sda and create a swap partition and a NTFS data partition.
Thanks!

---

