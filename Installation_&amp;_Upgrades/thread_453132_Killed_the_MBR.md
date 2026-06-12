---
title: "Killed the MBR"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by SimonT on 2007-05-24
I am having a few problems and I guess I did not read enough of the RTFM but I have run in to a problem. After the guide I followed from another website this is what I have done

In windows I created a new partition with partition magic and set that at the start of my disk (14gig) I was able to reboot back in to windows with out any issues.

I then used the live CD and booted in to the installer in the install partion menu I told Ubuntu to install in to the the first partion (it saw that as being around 12ish gig) after the install it rebooted but now comes back with a can not MBR errror 1 press any key to boot from the floppy.

Any help :-) for a linux noob

---

### Post by Psicolonia on 2007-05-24
grab xp disk. boot it, press R for recover console and type:

fixboot
fixmbr

reboot. you've got your mbr back. then worry about installing grub.
boot ubuntu live and type grub-install /dev/hd

---

### Post by SimonT on 2007-05-24
Psicolonia thank you very much for your help I will give this a shot now :-)

---

### Post by SimonT on 2007-05-24
Not much luck with that windows still does not boot from the live cd please see the results

```
ubuntu@ubuntu:~$ grub-install /dev/hd 
mkdir: cannot create directory `/boot/grub': Permission denied
ubuntu@ubuntu:~$ sudo grub-install /dev/hd 
Probing devices to guess BIOS drives. This may take a long time.
/dev/hd: Not found or not a block device.
ubuntu@ubuntu:~$ 

```

In the file browser I see 10.3GB volumedisk , 2.0 GB Volume disk-1 and 2.0 gb volume (2) disk-2 and then 41.1GB Volume disk-3 (thats windows xp) and then filesystem

So it looks like my windows OS is still there but for the life of me I dont know what all these 2 gig volumes are or how to fix the bootloader.

---

### Post by confused57 on 2007-05-24
To see how Ubuntu recognizes your partitions, boot the live cd, from a terminal:
```
sudo fdisk -l
```
the -l is a small "L"

Once you determine how your hard drive is identified, I think you have to use sudo to install grub:
```
sudo grub-install /dev/hda
```
which installs grub to the mbr

The live cd can also be used to install grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The Window's install cd has to be used to restore your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)

---

### Post by SimonT on 2007-05-24
Thanks for the reply confused57


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1927        7296    43134493+   7  HPFS/NTFS
/dev/sda2               2        1660    13325917+   f  W95 Ext'd (LBA)
/dev/sda3            1661        1926     2136645   83  Linux
/dev/sda5               2        1352    10851876   83  Linux
/dev/sda6            1640        1660      168651   82  Linux swap / Solaris
/dev/sda7   *        1353        1618     2136613+  83  Linux
/dev/sda8            1619        1639      168651   82  Linux swap / Solaris

Partition table entries are not in disk order
```

 as you can seem to have so many partition  is that right I was just trying to have a windows partition  and then a linux partition. I through linux would have just 2 partitions
one for the core files and then a swop file. Or are the 2 extra partitions just coming from the live boot cd.

sudo grub-install /dev/hda

gives

```
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.

```

should I be running ti as sudo grub-install /dev/sda1 ??

Thanks for your help or all that can help me :-)

---

### Post by psusi on 2007-05-24
Did you try to install ubuntu twice or something?  I'd say get rid of all but the windows partition and reinstall ubuntu.

---

### Post by confused57 on 2007-05-24
> **SimonT said:**
> Thanks for the reply confused57


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1927        7296    43134493+   7  HPFS/NTFS
/dev/sda2               2        1660    13325917+   f  W95 Ext'd (LBA)
/dev/sda3            1661        1926     2136645   83  Linux
/dev/sda5               2        1352    10851876   83  Linux
/dev/sda6            1640        1660      168651   82  Linux swap / Solaris
/dev/sda7   *        1353        1618     2136613+  83  Linux
/dev/sda8            1619        1639      168651   82  Linux swap / Solaris

Partition table entries are not in disk order
```

 as you can seem to have so many partition  is that right I was just trying to have a windows partition  and then a linux partition. I through linux would have just 2 partitions
one for the core files and then a swop file. Or are the 2 extra partitions just coming from the live boot cd.

sudo grub-install /dev/hda

gives

```
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.

```

should I be running ti as sudo grub-install /dev/sda1 ??

Thanks for your help or all that can help me :-)

Since your hard drive is recognized as /dev/sda, you'd need to do:
```
sudo grub-install /dev/sda
```

I'm not sure what the 2 small 2 Gb ext3 partitions are, but you have 2 swap partitions, which you don't need.  You can try reinstalling grub or restoring your Window's IPL code to the mbr...your best bet might be to use Partition Magic to delete all your Linux partitions, then reinstall maybe using "manual partitioning" & just setup a root(/) and swap partition.  Be sure to use the Ubuntu live cd's gparted to format your linux partitions for ext3 & swap.

It's usually always recommended to have Ubuntu physically  located on a partition after your Window's partition...I'm not sure about having your Window's partition designated sda1, but physically located after Ubuntu on your hard drive.  It would have been better to have freed up space at the end of your Window's partition to install Ubuntu on...your current setup might work, I'm not sure.

---

### Post by merlinus on 2007-05-24
If you have not configured any of the Ubuntu programs, you might consider starting over again.

It seems that you have four linux partitions rather than two.  If you do re-install, though, I recommend you create a third one for /home.

Then grub will be installed correctly.

If reinstalling is not an option, there are other alternatives, just not as easy.

Good luck!

-merlin

---

### Post by SimonT on 2007-05-24
I am happy to flatten the laptop as long as I can still keep the windows in the 45gig space as I will have to use that for work but every thing else can go :-)

if I fire up the installer again will that allow me to format every thing ?

if you could give me some pointers on how to setup the home on the 3rd partition that would be great. All the Linux partitions  are from me failing to install linux on the disk. I am just in the live CD now so happy to blow them away.

---

### Post by merlinus on 2007-05-24
Choose manual partitioning, or the use free space option.  This will leave your windows partition intact.

Again, be sure to defrag and run chkdsk on your windows partition.  If you do not, it could cause the linux partitioning to fail.

Then you can allocate how much space to give for /root, /home, and /swap.

I believe after you set up each partition, you can click on it and select edit.  This will give you a dropdown menu for the mount point.

swap only needs to be a half gig.  The rest of the free space can be shared between /root and /home.

Also, unless you have a dell or some other computer that reserves space for a system restore, you can lose the extended partition (sda2 in your print-out).  It seems as though it is not doing anything.

You can have up to four primary partitions, so you do not need an extended one, which is then divided into logical partitions.

As an example, here is the output of sudo fdisk -l on my machine:

```

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2666    21414613+   7  HPFS/NTFS
/dev/sda2            2667        7297    37198507+   f  W95 Ext'd (LBA)
/dev/sda5            2667        2774      867478+   7  HPFS/NTFS
/dev/sda6            2775        3627     6851691   83  Linux
/dev/sda7            3628        4909    10297633+  83  Linux
/dev/sda8            4910        7106    17647371   83  Linux
/dev/sda9            7107        7297     1534176   82  Linux swap / Solaris

```

-merlin

---

### Post by SimonT on 2007-05-25
Thanks for the help so far every one :-)

I have Choose manual partitioning and am about to click next I just wanted to check and confirm I have set it up correctly as I was not sure on the mount points and "type" setting EXT2 or EXT3  and I hope I wont loose my little windows XP :-) 


[[IMG]http://img69.imageshack.us/img69/1319/screenshotinstallgm2.th.png[/IMG]](http://img69.imageshack.us/my.php?image=screenshotinstallgm2.png)

---

### Post by confused57 on 2007-05-25
Everything looks good, but I believe you need to check the swap partition to be formatted...which it should be formatted as swap...your root & home should be formatted ext3.   Definitely don't choose to format your Window's NTFS partition...I see you've already selected not to format.

---

### Post by psusi on 2007-05-25
You want that to be / not /root.

---

### Post by confused57 on 2007-05-25
> **psusi said:**
> You want that to be / not /root.

Thanks psusi, I missed that...

Sorry SimonT, hope it didn't cause you too much problem, the installation probably wouldn't complete without a root partition assigned.

---

### Post by SimonT on 2007-05-26
Thanks guys it did tell me about the /root/ error and I fixed that but then failed to format 1 of the drives. I tried it again and all worked ok. on reboot I get the grub menu and was able to boot in to both windows XP and linux

Thank you to every one that helped me with this install I will keep reading and keep learning and one day hope to be able to help some one in my spot.

PS one question what's the difference between EXT2 and EXT3

---

### Post by psusi on 2007-05-26
Ext3 uses a journal to keep the filesystem in a consistent state in the event of a crash or power loss, so you don't have to run a lengthy disk check on the next boot.

---

