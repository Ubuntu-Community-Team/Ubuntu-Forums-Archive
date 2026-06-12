---
title: "Install /dev/disk/by-uuid... does not exist"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by ben aveling on 2012-05-27
I have this problem, perhaps. Perhaps not.

While trying to install from wubi on a  Sony Vaio SA36 it fails with the same 
/dev/disk/by-uuid/xxx... does not exist error, and then drops to the limited shell.

When I cd to /dev/disk I can see that the directory by-uuid does not exist.  

Typing exit just repeats the error. Typing reboot takes me back to Windows with no drama.

Booting from a USB Stick didn't work - went straight into windows - perhaps PC is set not to boot from USB? Not sure, and not sure how to check either.

Booting from a livedisk (CD) has triggered an install. 

During the initial load, it produced a page or two of error messages, mostly SQUASHFS error: Unable to read fragment cache entry [4a4f12]/Unable to read page, block 4a4f12. 

It offered the choices to try Ubuntu without installing, or to install.  I selected install.

The install failed with a message something like: "ubi-partman failed with exit code 2. There may be more info in /var/log/syslog"

I quit the install, and it dropped me into a ubuntu desktop

There are about 2000 lines in syslog. The relevant error may or may not be OSError: [Ernno 2] No such file or directory: /var/lib/partman/devices

There is a directory /var/lib/partconf but no directory /var/lib/partman

partconf conains only fstab.d/ which contains only one file called common, which contains 3 lines, one for /dev/fd0, one for /dev/cdrom, one for proc.

I am now working through the suggestions in [http://ubuntuforums.org/showthread.php?t=1639198&highlight=%2Fdev%2Fdisk%2Fby-uuid%2F+exist](http://ubuntuforums.org/showthread.php?t=1639198&highlight=%2Fdev%2Fdisk%2Fby-uuid%2F+exist)

(This is my 2nd ubuntu install - the first was on a cheap netbook, and it just worked.  That was an earlier version of ubuntu, but I suspect the problem is that the higher range hardware on this Vaio requires special treatment.  To be continued...)

---

### Post by oldfred on 2012-05-27
Moved to your own thread.
Was here, but may not be very related:
[http://ubuntuforums.org/showthread.php?t=1935495](http://ubuntuforums.org/showthread.php?t=1935495)

Are you now trying wubi install or a full partitioned install? 
Not familiar with wubi installs.

With partitioned install I would suggest partitioning in advance with gparted from liveCD. But use Windows to shrink the Windows partition. 

With the errors you are getting, is your download correct? I would check md5sum and verify CD before using. 

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ben aveling on 2012-06-23
Used windows to shrink the existing partition by 100GB, as per [http://windows.microsoft.com/en-us/windows-vista/Can-I-repartition-my-hard-disk](http://windows.microsoft.com/en-us/windows-vista/Can-I-repartition-my-hard-disk)

i.e.

controlpanel->administrative tools->compuater management->storage->disk management
then
r.click->Shrink volume

Downloaded 12.04, downloaded fourmilab md5, checked the cksums:

C:\Users\ben\Downloads>\bin\md5.exe ubuntu-12.04-desktop-i386.iso
D791352694374F1C478779F7F4447A3F  ubuntu-12.04-desktop-i386.iso

Check against [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso

So far so good.

Burnt the CD (right click on iso and selected burn iso to disk - with verify, no dramas)

Fourmiliab "mc5.exe -c" didn't t behave as expected.  So I created a .bat file from a copy of the md5sum.txt file , eg 
c:\bin\md5.exe -l  ./pics/red-upperleft.png
c:\bin\md5.exe -l  ./pics/red-lowerleft.png
c:\bin\md5.exe -l  ./pics/blue-lowerleft.png
c:\bin\md5.exe -l  ./pics/logo-50.jpg
c:\bin\md5.exe -l  ./pics/blue-upperright.png
c:\bin\md5.exe -l  ./pics/blue-lowerright.png
...

Ran it, piped output to a file, edit the result by hand to remove extra lines (memo to self - next time, use echo off)

c:\tmp>\bin\md5.exe md5sum.???
3C78F095A4BCA5508636BFC2970B2240  md5sum.out
3C78F095A4BCA5508636BFC2970B2240  md5sum.txt

All good.

Rebooted, and installed.  All seemed to go OK until: "Executing 'grub-install /dev/mapper' failed - this is a fatal error - not possible to install the boot loader at the specified location /dev/mapper

It offered a list of alternate locations:
/dev/mapper/isw_dafajjibid_Volume0   Linux device mapper (striped) (256.1 GB)
/dev/mapper/isw_dafajjibid_Volume0p1 Windows Recovery Environment (loader)
/dev/mapper/isw_dafajjibid_Volume0p2 Windows 7 (loader)
/dev/mapper/isw_dafajjibid_Volume0p3 
/dev/mapper/isw_dafajjibid_Volume0p5
/dev/mapper/isw_dafajjibid_Volume0p1 Linux device-mapper (linear) (13.6 GB)
/dev/mapper/isw_dafajjibid_Volume0p1 Windows Recovery Environment (loader) 
/dev/mapper/isw_dafajjibid_Volume0p2 Linux device-mapper (linear) (104.9 MB)
/dev/mapper/isw_dafajjibid_Volume0p2 Windows 7 (loader)
/dev/mapper/isw_dafajjibid_Volume0p3 Linux device-mapper (linear) (137.5 GB)
/dev/mapper/isw_dafajjibid_Volume0p3 

I opted to continue without installing a boot loader.

when I restarted the computer, Windows Boot offered either Windows 7 or Linux.  Selecting Linux died with a message that "ALERT! /dev/disk/by-uuid/80F0E... does not exist.

Using cd /dev/disk and ls shows that there is no directory by-uuid

There is a directory by-id and a directory by-path.

by-id contains lots of files with names like ata-MATSHITADVD-RAM_... and ata-SAMSUNG)... and scsi-SATA_SAMSUNC...-part2 and ...-part3 and so on.

I assume these are the partitions?

by-path contains 4 files with names like pci-0000:00:1f.2-scsi-0:0:0 and pci-0000:00:1f.2-scsi-0:0:0-part1 and so on.

Rerunning controlpanel->administrative tools->computer management->storage->disk management, I think p1 is the original recovery partition, not sure what p2 except that it is something windows related - it's NTFS, and p3 is the original C: drive (now shrunk). The space I originally freed up has been used for two partitions: one 89.74GB and one of 7.92GB - presumably these are where Ubuntu has installed itself.

One thing I'd have like to have done differently is that when asked about partitions, I said "install alongside" existing OS, instead of being explicit about what partitions to create.  I'll give that a go now, but not confident it will make a difference. If it fails, I'll try to get into linux from the boot CD (which worked last time) and then try running grub-install, as per [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

wish me luck.

---

### Post by westie457 on 2012-06-23
Hi.

Before going any further could post here either a screenshot of your partitions as seen from Windows Disk Management or the rerminal output of ```
sudo fdisk -l
``` please (the l is a lowercase L).

---

### Post by ben aveling on 2012-06-23
I'm currently booted from the CD.

sudo fdisk -l doesn't give anything.

sudo parted -l gives, in part:

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  13.6GB  13.6GB  primary   ntfs            diag
 2      13.6GB  13.7GB  105MB   primary   ntfs            boot
 3      13.7GB  151GB   138GB   primary   ntfs
 4      151GB   256GB   105GB   extended
 5      151GB   248GB   96.4GB  logical   ext4
 6      248GB   256GB   8501MB  logical   linux-swap(v1)

5 is 'clearly' the partition I've installed ubuntu in.

It looks like:

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_dafajjibid_Volume0p4: 105GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1024B   96.4GB  96.4GB  primary   ext4
 2      96.4GB  105GB   8501MB  extended
 5      96.4GB  105GB   8501MB  logical   linux-swap(v1)

I can cut and paste the rest, but I think this is the information you are asking for?

---

### Post by ben aveling on 2012-06-23
For what it's worth, the whole output is:


[FONT=Courier New]ubuntu@ubuntu:~$ sudo parted -l[/FONT]
 [FONT=Courier New]Error: Can't have a partition outside the disk!                            [/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Error: /dev/sdb: unrecognised disk label                                   [/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Error: /dev/sdc: unrecognised disk label                                   [/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Error: /dev/sdd: unrecognised disk label                                   [/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (linear) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0p2: 105MB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: loop[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start  End    Size   File system  Flags[/FONT]
 [FONT=Courier New] 1      0.00B  105MB  105MB  ntfs[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (linear) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0p4: 105GB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: msdos[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start   End     Size    Type      File system     Flags[/FONT]
 [FONT=Courier New] 1      1024B   96.4GB  96.4GB  primary   ext4[/FONT]
 [FONT=Courier New] 2      96.4GB  105GB   8501MB  extended[/FONT]
 [FONT=Courier New] 5      96.4GB  105GB   8501MB  logical   linux-swap(v1)[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (linear) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0p5: 96.4GB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: loop[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start  End     Size    File system  Flags[/FONT]
 [FONT=Courier New] 1      0.00B  96.4GB  96.4GB  ext4[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (linear) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0p3: 138GB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: loop[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start  End    Size   File system  Flags[/FONT]
 [FONT=Courier New] 1      0.00B  138GB  138GB  ntfs[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (linear) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0p6: 8501MB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: loop[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start  End     Size    File system     Flags[/FONT]
 [FONT=Courier New] 1      0.00B  8501MB  8501MB  linux-swap(v1)[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (linear) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0p1: 13.6GB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: loop[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start  End     Size    File system  Flags[/FONT]
 [FONT=Courier New] 1      0.00B  13.6GB  13.6GB  ntfs[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Model: Linux device-mapper (striped) (dm)[/FONT]
 [FONT=Courier New]Disk /dev/mapper/isw_dafajjibid_Volume0: 256GB[/FONT]
 [FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT]
 [FONT=Courier New]Partition Table: msdos[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Number  Start   End     Size    Type      File system     Flags[/FONT]
 [FONT=Courier New] 1      1049kB  13.6GB  13.6GB  primary   ntfs            diag[/FONT]
 [FONT=Courier New] 2      13.6GB  13.7GB  105MB   primary   ntfs            boot[/FONT]
 [FONT=Courier New] 3      13.7GB  151GB   138GB   primary   ntfs[/FONT]
 [FONT=Courier New] 4      151GB   256GB   105GB   extended[/FONT]
 [FONT=Courier New] 5      151GB   248GB   96.4GB  logical   ext4[/FONT]
 [FONT=Courier New] 6      248GB   256GB   8501MB  logical   linux-swap(v1)[/FONT]
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT] 
 [FONT=Courier New]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/FONT]
 [FONT=Courier New]has been opened read-only.[/FONT]
 [FONT=Courier New]Error: Can't have a partition outside the disk!        [/FONT]

---

### Post by darkod on 2012-06-23
Why did you decide not to install the grub2 bootloader?

On top of that, you seem to be installing on raid. For better results on raid, the alternate cd should be used.

If you want to, you can add the bootloader now.

---

### Post by darkod on 2012-06-23
Since it seems the raid array is recognized from live mode, it should be easy to install the grub2 to the MBR of the array. I hope the package was fully installed inside ubuntu and that only the installation to the MBR was interrupted.

If that assumption is correct, from live mode in terminal you would only need to mount the root partition (ending in Volume0p5) and install grub2 onto the MBR of the array (ending in Volume0 without the p5).

Note that you will need to type the whole device name including the isw_blahblah...

```
sudo mount /dev/mapper/isw_blahblah_Volume0p5 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_blahblah_Volume0
```

Restart and see if it helped.

---

### Post by ben aveling on 2012-06-23
> **darkod said:**
> Why did you decide not to install the grub2 bootloader?

Because, once it failed, I wasn't sure which partition to install it into..

> **darkod said:**
>  On top of that, you seem to be installing on raid. For better results on raid, the alternate cd should be used.

If grub-install fails, I'll try that.

Thanks.

---

### Post by ben aveling on 2012-06-23
[FONT=Courier New]ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dafajjibid_Volume0p5 /mnt
ubuntu@ubuntu:~$ df 
Filesystem                           1K-blocks    Used Available Use% Mounted on
/cow                                   4087328   85840   4001488   3% /
udev                                   4079696      12   4079684   1% /dev
tmpfs                                  1634932     924   1634008   1% /run
/dev/sr0                                718124  718124         0 100% /cdrom
/dev/loop0                              688256  688256         0 100% /rofs
tmpfs                                  4087328      16   4087312   1% /tmp
none                                      5120       4      5116   1% /run/lock
none                                   4087328      76   4087252   1% /run/shm
/dev/mapper/isw_dafajjibid_Volume0p5  93954840 4149712  85100184   5% /mnt
ubuntu@ubuntu:~$ df -h
Filesystem                            Size  Used Avail Use% Mounted on
/cow                                  3.9G   84M  3.9G   3% /
udev                                  3.9G   12K  3.9G   1% /dev
tmpfs                                 1.6G  924K  1.6G   1% /run
/dev/sr0                              702M  702M     0 100% /cdrom
/dev/loop0                            673M  673M     0 100% /rofs
tmpfs                                 3.9G   16K  3.9G   1% /tmp
none                                  5.0M  4.0K  5.0M   1% /run/lock
none                                  3.9G   76K  3.9G   1% /run/shm
/dev/mapper/isw_dafajjibid_Volume0p5   90G  4.0G   82G   5% /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mapper/isw_dafajjibid_Volume0
Installation finished. No error reported.[/FONT]

So far so good - will reboot now. Tx again.

---

### Post by ben aveling on 2012-06-23
Progress, but less than success.  It now brings up grub, and tries to boot linux, but gets stuck at Starting CUPS printing spooler/server. 

Windows still boots OK for whatever that's worth.

---

### Post by darkod on 2012-06-23
Well, this is not grub2 related any more, doesn't look like it.

Unfortunately, I don't know what could be the issue. This is a new clean install right?

Does it always stop loading at the same line?

You can remove the 'quiet splash' from the boot lines so that it shows (text scrolling) what it does while loading and any errors it might show. To edit the boot lines while in the grub2 boot menu, highlight the ubuntu entry and press 'e' for edit.
Move the cursor with the arrows keys and delete the 'quiet splash' in the line starting with linux.
Then press Ctrl + X to boot.

See if that helps you troubleshoot.

---

### Post by ben aveling on 2012-06-23
Agreed, seems to have gotten past the original problem.  Perhaps we should start a new thread?

The line it always fails on is Starting CUPS printing spooler/server [YES]

But the YES makes me unsure that CUPS is the problem.

When I boot from the CD (which works), the next lines are something like:
[ 115.508523] Bad LUN (0:2)
[ 115.508660] Bad target number (1:0)
[ 115.508786] Bad target number (2:0)
...
[ 115.509244] Bad target number (7:0)
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
* Stopping System V initialisation compatibility
* Starting System V runlevel compatibility
...

I'll try the alternate CD.

---

### Post by ben aveling on 2012-06-24
Fun and games continues.  

Reinstalled from alternate CD - opted to delete and recreate Partition 5, which is now partition 6.

Again, grub failed: "grub-pc failed to install into /target/"

It offered a choice of device for boot loader installation, but no guidance.  I hit "go back", and it offered to install to master boot record.

I said "yes", and again it failed, something about "/sda failed". 

It then told me I should have installed to "/dev/mapper/isw_dafajjibid_Volume_0p6" but didn't give me a chance to do so.

Rebooted, "grub rescue>"

Oh dear.

I booted off the standard CD, and reinstalled grub as before.

Reboot. This time it goes to the prompt "grub>" 

Better, but still not good.

A bit of web searching, and I try

set root=(hd0,2)
chainloader +1
boot

And that worked, at least, well enough to get me back into Windows. (And bringing to mind: [http://xkcd.com/349](http://xkcd.com/349))

set root=(hd0,5)
chainloader +1

and 

set root=(hd0,6)
chainloader +1

do not work, something about invalid signature.

The I remembered that set root=(hd0,2) ... also gave an option to boot linux - except it failed with a complaint about /dev/disk/by-uuid, which is pretty much where this thread started.

One more datapoint:
blkid gives /dev/sdb, /dev/sdc and /dev/sdd

But ls shows that there is /dev/sda, and also /dev/sda1, /dev/sda2 and /dev/sda3 as well.

blkid /dev/sda -p retuns /dev/sda: VERSION="1.2.01" TYPE=isw_raid_member" USAGE="raid", same as for /dev/sd[bcd].  

Nothing about UUIDs.

blkid /dev/sda? doesn't return anything at all. 

There is no directory /dev/disk/by-uuid

There is a directory /dev/disk/by-path which contains (ls -l)
pci-0000:00:1f.2-scsi-1:0:0:0 ->../../sdb
pci-0000:00:1f.2-scsi-4:0:0:0 ->../../sr0
pci-0000:00:1f.2-scsi-0:0:0:0 ->../../sda
pci-0000:00:1f.2-scsi-3:0:0:0 ->../../sdd
pci-0000:00:1f.2-scsi-2:0:0:0 ->../../sdc
pci-0000:00:1f.2-scsi-0:0:0:0-part1 ->../../sda1
pci-0000:00:1f.2-scsi-0:0:0:0-part3 ->../../sda3
pci-0000:00:1f.2-scsi-0:0:0:0-part2 ->../../sda2

I believe sr0 is the cdrom. (I've seen ubuntu complain loud and often that it is readonly)

The rest seem to match nicely enough to my partitions - but which is which?

cat /proc/cmdline returns BOOT_IMAGE=/vmlinuz root=UUID=80F0E65FF0E65B44 loop-/ubuntu/disks/root.disk preseed/file/ubuntu/install/presseed.cfg wubi-diskimage ro quite splash

I guess that means that this is a left-over from the original attempt to use wubi?

And that where it is trying to use /dev/sda it should be using /dev/sda3?  Or /dev/sda1 or /dev/sda2?

Am passingly tempted to add and delete some partitions to see what happens to these devices - possibly nothing - if these were created by wubi, then can they be influenced by any subsequent changes to partitions?

(If nothing else, this is ... educational.)

ls -l /dev/sd* gives
brw------ 1 8, 48 /dev/sdd
brw------ 1 8, 32 /dev/sdc
brw------ 1 8, 16 /dev/sdb
brw------ 1 8, 3 /dev/sda3
brw------ 1 8, 2 /dev/sda2
brw------ 1 8, 1 /dev/sda1
brw------ 1 8, 0 /dev/sda

Booting from std cd again.  Perhaps interestingly, the first thing it does is report that it is:
unable to open /dev/dm-0
unable to open /dev/dm-4
unable to open /dev/sda
unable to open /dev/sdb
unable to open /dev/sdd

---

### Post by darkod on 2012-06-24
We never touched one important question: Do you have raid or not?

You might have only one disk that has been used in raid before and still has meta data remains. Windows ignores this and works like normal from one disk, but ubuntu gets confused whether you are running raid or not (not to mention grub2 installing gets confused).

This is important since if running only a single hdd you need to get rid of the meta data first, and then try to install ubuntu.

Also, you never posted a full result from either fdisk or parted, I see in one of your earlier posts a message about a partition outside of the disk. This might be messing it up for you too.

I suggest you boot into live mode and post the full results of both:
```
sudo fdisk -l
sudo parted /dev/sda unit s print all
```Also, clarify, once and for all, are you running raid or not? That is important.
With regards to your last post and the alternate install attempt, the grub2 should have been installed on the MBR of the array, which is /dev/mapper/......_Volume0 like we discussed previously. Not to Volume0p6. But all of that is besides the point if you are not running a raid.

---

### Post by ben aveling on 2012-06-24
Yes, it's raid: SSD in RAID 0: (256 GB (64 GB x 4; Serial ATA)) ([http://www.sony.com.au/product/vpcsa36gg](http://www.sony.com.au/product/vpcsa36gg))

ubuntu@ubuntu:/dev/disk/by-uuid$ sudo fdisk -l /dev/sd*

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

ubuntu@ubuntu:/dev/disk/by-uuid$ sudo parted /dev/sda unit s print all
Error: Can't have a partition outside the disk!   

ubuntu@ubuntu:/dev$ sudo fdisk -l /dev/dm*

Disk /dev/dm-0: 256.1 GB, 256083755008 bytes
255 heads, 63 sectors/track, 31133 cylinders, total 500163584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x99a1a653

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1            2048    26554367    13276160   27  Hidden NTFS WinRE
/dev/dm-0p2   *    26554368    26759167      102400    7  HPFS/NTFS/exFAT
/dev/dm-0p3        26759168   295360511   134300672    7  HPFS/NTFS/exFAT
/dev/dm-0p4       295361534   500163583   102401025    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/dm-0p5       483560448   500163583     8301568   82  Linux swap / Solaris
/dev/dm-0p6       295361536   483560447    94099456   83  Linux

Partition table entries are not in disk order

Disk /dev/dm-1: 13.6 GB, 13594787840 bytes
255 heads, 63 sectors/track, 1652 cylinders, total 26552320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/dm-1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/dm-1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/dm-1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 137.5 GB, 137523888128 bytes
255 heads, 63 sectors/track, 16719 cylinders, total 268601344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x6e697373


This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/dm-2p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/dm-2p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/dm-2p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/dm-3p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/dm-3p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/dm-3p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-4: 104.9 GB, 104858649600 bytes
255 heads, 63 sectors/track, 12748 cylinders, total 204802050 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Alignment offset: 1024 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-4p1       188198914   204802049     8301568   82  Linux swap / Solaris
/dev/dm-4p2               1   188198913    94099456+   5  Extended
Partition 2 does not start on physical sector boundary.
/dev/dm-4p5               2   188198913    94099456   83  Linux

Partition table entries are not in disk order

Disk /dev/dm-5: 8500 MB, 8500805632 bytes
255 heads, 63 sectors/track, 1033 cylinders, total 16603136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x00000000

Disk /dev/dm-5 doesn't contain a valid partition table

Disk /dev/dm-6: 96.4 GB, 96357842944 bytes
255 heads, 63 sectors/track, 11714 cylinders, total 188198912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x00000000

Disk /dev/dm-6 doesn't contain a valid partition table

So my take: /dev/sd* is the raw 64G drivers.  Not sure what has happened to /dev/sda, if anything - it may that it is fine but linux is getting confused, I don't know. 

The /dev/dm-? devices seem to be the (virtual) partitions, the reason 5 comes before 6 is that I deleted the original partition 5, so it moved partition 6 up by one.

And, I take it, the /dev/dm-?p? are the pieces of each of the dm-? partitions.
[I]
PS

[/I]ubuntu@ubuntu:/dev/mapper$ ll
total 0
drwxr-xr-x  2 root root     200 Jun 24  2012 ./
drwxr-xr-x 16 root root    4600 Jun 24 10:09 ../
crw-------  1 root root 10, 236 Jun 24  2012 control
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0 -> ../dm-0
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0p1 -> ../dm-1
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0p2 -> ../dm-3
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0p3 -> ../dm-2
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0p4 -> ../dm-4
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0p5 -> ../dm-5
lrwxrwxrwx  1 root root       7 Jun 24  2012 isw_dafajjibid_Volume0p6 -> ../dm-6
ubuntu@ubuntu:/dev/mapper$ sudo mount  /dev/dm-6 /mnt
ubuntu@ubuntu:/dev/mapper$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
bin  boot  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  selinux  srv  sys  tmp  usr  var  vmlinuz
ubuntu@ubuntu:/mnt$ sudo grub-install --root-directory=/mnt /dev/dm-0
Installation finished. No error reported.
ubuntu@ubuntu:/mnt/dev$ sudo !!
sudo blkid 
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660" 
/dev/sdd: TYPE="isw_raid_member" 
/dev/mapper/isw_dafajjibid_Volume0p1: LABEL="Recovery" UUID="4C92D84A92D839E2" TYPE="ntfs" 
/dev/mapper/isw_dafajjibid_Volume0p2: LABEL="System Reserved" UUID="B48CE5368CE4F3B0" TYPE="ntfs" 
/dev/mapper/isw_dafajjibid_Volume0p3: UUID="80F0E65FF0E65B44" TYPE="ntfs" 
/dev/mapper/isw_dafajjibid_Volume0p6: UUID="6ce9e2b0-4b74-4828-a532-cd2018dae041" TYPE="ext4" 

So... 0p1=Recovery; 0p2=boot partition?;0p3=Windows;0p6=Ubuntu.

---

### Post by darkod on 2012-06-24
I am worried parted said:
Error: Can't have a partition outside the disk!   

and it didn't print anything.
Also, fdisk omitted /dev/sda.

I think you might have a corruption in the partition table on /dev/sda. You might wanna look into it, especially since you are running raid0. If one disk goes, you lose everything.
I wouldn't depend on my machine if one disk has a problem with the partition table.

I was hoping parted would show if any partition is outside the disk, but it didn't even print out anything.

---

### Post by ben aveling on 2012-06-24
Indeed, is a bit of a worry. Don't know what to make of it. You'd think that a missing partition table would bring everything to a screaming halt, but Windows still seems as happy as ever. Maybe linux is failing to communicate with the raid somehow - so there is no problem with the raid, only with linux's attempts to read it - but not clear to me why that should be.

Currently nothing irreplaceable on that machine...

---

### Post by ben aveling on 2012-06-24
PS Using grub 2 I can boot windows, and I can get linux to begin booting, but it either panics, or goes into initramfs, depending on what settings I give it.  I'm pretty sure the initramfs is only the abortive wubi install that I started with.

See also [http://paste.ubuntu.com/1057481/](http://paste.ubuntu.com/1057481/)

---

### Post by darkod on 2012-06-24
I don't think the partition table is missing, maybe it only has some error in it or corruption. Very often windows ignores some errors in the table and can work as normal, but linux wouldn't allow you that.

Not sure which is the best tool to try to read the disk in this situation since both parted and fdisk seem to ignore it.

Windows will not even see it as separate disk when it's in the raid array, so you can't use Disk Management I guess.

Very often fixparts can help with corrupted partition tables but if it makes some changes that the raid won't like on one of the disks included in the raid?
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

