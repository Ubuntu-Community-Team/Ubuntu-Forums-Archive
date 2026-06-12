---
title: "Windows XP partition stopped loading in grub, help!"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by suicidal6 on 2006-12-02
Hi guys, i'm having the strangest problem.
First here's a description of my system hard drives:
1 IDE drive (on which ubuntu resides)
2 SATA drives

fdisk -l outputs:

```

Disk /dev/hda: 18.4 GB, 18480365568 bytes
255 heads, 63 sectors/track, 2246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         721     5791401    7  HPFS/NTFS
/dev/hda2             771        2181    11333857+  83  Linux
/dev/hda3            2182        2246      522112+   5  Extended
/dev/hda4   *         722         770      393592+   b  W95 FAT32
/dev/hda5            2182        2246      522081   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7748    62235778+   7  HPFS/NTFS
/dev/sda2            7749       24321   133122622+   f  W95 Ext'd (LBA)
/dev/sda5            7749       24321   133122591    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

```

Now the fun story, windows XP resides on /dev/sda1, it was working fine using the following in menu.lst of my grub:

```

title                   Windows XP
root                    (hd1,0)
savedefault
makeactive
chainloader             +1

```

since i have a fat32 partition on the IDE hard drive, windows boots into D: drive and not C:, this is perfectly fine since it was installed like so.

The problem is, today, when i needed to use windows (which i don't need often), when i select "Windows XP" from grub's menu, it writes the:

"Starting up..."
and hangs on it! system becomes unresponsive and i need to press Reset...

the partition is not damaged in a way that i can see, i can mount it just fine and see the files on it, i even set it up as a physical drive in VMWARE and the NT bootloader poped up, but windows crashes when it's starting up (i'm guessing cause of hardware change).

The only thing i can think of that i've done on this partition is that i mounted it using:
mount /dev/sda1 -t ntfs-3g -o defaults /mnt/windows
(did not use the mount point to Write to the hard drive, only used it to Read some files from it) and i forgot to umount before restarting the machine, don't know if that might've cause the problem and if so, how to fix it.

i really don't want to reinstall windows and would like to find some other solution, any help would be greatly appreciated.

](*,)

---

### Post by Herman on 2006-12-02
Hello suicidal6,
It is strange that your Windows used to boot okay from Grub but has now changed without you doing anything that you are aware of. I don't think shutting down you computer without manually unmounting a partition first would cause any problems. Nowadays Linux, or at least Ubuntu, is smart enough to automatically unmount everything as it shuts down, as long as we shut down properly, and not pull the power cord or use the big on/off button.  So I don't think your Windows file system is likely harmed.

It is usual for Grub to consider any SCSI or Sata disk as a first hard disk, even though it might not be according to partitioning software and cabling. I think that it would be a good guess that your Windows will be bootable if you try replacing (hd1,0) in your menu.lst file with (hd0,0).
```
title                   Windows XP
root                    (hd0,0)
savedefault
makeactive
chainloader             +1
``` Try that and see if it helps or not.

Regards, Herman :D

---

### Post by Herman on 2006-12-02
[SIZE=3][SIZE=2]Just in case you or someone else reading this thread for an answer to a similar problem becomes impatient, here is a link I recommend for Windows XP users with boot problems.[/SIZE]

[/SIZE][SIZE=3][SIZE=2][How To Create a Boot Disk for an NTFS or FAT Partition in Windows XP]("http://support.microsoft.com/kb/305595/EN-US/")[/SIZE]
[/SIZE][B][SIZE=3]
[/SIZE][/B]There are other versions of this how to (page) available for other Windows editions too. This Windows boot floppy disk is great! It will boot Windows for you even if you have no IPL in the hard disk's  MBR, no bootsector, no boot.ini, no ntdetect and no NTLRD at all. 
You can also edit the boot.ini on the floppy disk from Linux, in case your problem is that your Windows partition number has been changed. So you can still boot Windows even if it has the NT File System, and then edit your boot.ini from within Windows.

I haven't found out yet how to format the floppy disk correctly to make one from Linux yet. If someone knows how, feel free to share the info!
The link gives instructions for formatting it from DOS, and other ways of formatting it I have tried have not  resulted in a bootable floppy.
We can copy the files to the floppy disk via Linux easily though. :D
The above floppy disks will boot Windows whether or not Windows bootloader has a problem.

[Super Grub Disk]("http://supergrub.forjamari.linex.org/") is currently the most popular boot disk, and it will boot Linux whether of not the Linux bootloader or the hard disk's MBR has a problem, and also Windows if Windows doesn't have any serious problems. It's a good idea to have a Super Grub Disk around if you need to set up a dual boot and work with bootloaders.

Regards, Herman

---

### Post by suicidal6 on 2006-12-02
thank you for your input, my problem isn't in the partition numbers though, i can go into grub command line at boot (c) and type root (hd1, <TAB> and it will list correctly the partitions for the hd1  (0=windows partition, 1=ntfs data partition). so grub isn't mixing up the partition numbers, that i'm sure  of...
i will try the disk thingy, if it works, at least it will let me get into my windows to do the work i need to do on it... will let you know what happens with that...

---

### Post by suicidal6 on 2006-12-02
Heh, i used that SuperGrub CD iso image and booted the partition nicely =D
i selected windows and then windows from 2nd harddrive and it booted perfectly...
so now i just need to know what's wrong with the grub that's on my hard drive? why isn't it able to boot that partition while the one on the CD can? :(

PS: Thanks alot for the SuperGrub, it rocks, i will use it until i can figure out how to fix the problem.

---

### Post by Herman on 2006-12-03
> The problem is, today, when i needed to use windows (which i don't need often), when i select "Windows XP" from grub's menu, it writes the:
"Starting up..." and hangs on it! system becomes unresponsive and i need to press Reset...
the partition is not damaged in a way that i can see, i can mount it just fine and see the files on it, i even set it up as a physical drive in VMWARE and the NT bootloader poped up, but windows crashes when it's starting up (i'm guessing cause of hardware change).
The only thing i can think of that i've done on this partition is that i mounted it using:
mount /dev/sda1 -t ntfs-3g -o defaults /mnt/windows
(did not use the mount point to Write to the hard drive, only used it to Read some files from it) and i forgot to umount before restarting the machine, don't know if that might've cause the problem and if so, how to fix it. I have been re-reading your original post, and I am now thinking that if Windows does in fact begin to boot but then freezes, perhaps just some general Windows maintenance utilities like scan disk and defrag will help. Now that you can boot Windows with Super Grub DIsk it wouldn't hurt to try those. 
Windows is a very weird operating system. A friend of mine had a Windows computer that would not boot up. It eventually did after an hour. We shift-deleted all his spam email which contained a lot of suspicious attachments. That improved the machine to the point we could access the internet and update his antivirus software and run that. We also ran all the maintenance utilities and after a few hours his machine was as good as new. (Actually, it was new, it had hardly been used). I have recovered several Windows computers in a similar fashion whose owners thought they were unrepairable.  
Here is a [great link]("http://www.geekgirls.com/windows_defrag.htm") to help you make Microsoft utilities work faster, (see especially down near the bottom of the page under 'Step-by-Step Efficient Defragging', about how to set a selective start-up). I use this method for both scandisk and defrag. (Not that I use Windows myself anymore, I help other people who have Windows though.)
  
If it was a Grub problem there would more likely be a grub error message. There isn't a Windows error message either. Maybe it just needs some housecleaning. :D

Regards, Herman :D

---

### Post by suicidal6 on 2006-12-03
Hi Herman,

thank you for all your support it's much appreciated :)
as for cleaning mail and the sorts, i don't really have any, i only use gmail and never download attachements, i'm very tidy when it comes to these things, i've ran 3 PCs with no anti-virus and no firewalls for over 3 years now and no problems at all, i have an isolated test machine that i install things on before putting them on the final destination.
the strange thing is that i haven't booted that windows partition for a long time since i'm now almost always using Ubuntu (which i adore).
i've already ran all sorts of possible tests on the hard drive by plugging it into another machine and scanning/running checks from it, i even booted it from the other machine using the ntloader already there (by adding to boot.ini)
i'm guessing something changed and my grub's menu.lst needs to be fixed, i just don't know how...
is there any way to see how Super Grub is booting it? what it's using as
root (hd?,?)
...
chainloader...
maybe it's doing some mapping?
if so maybe i can do the same on my grub config...?

Regards,
Georges

---

### Post by Herman on 2006-12-03
:-k  Hmmm, it seems to me that your problem is somewhere other than in your menu.lst file.
You could test out your booting commands to make sure using Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and in particular, this section, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI"). 

If you can boot from your installed Grub's command line interface then it looks like it is probably a matter of editing your menu.lst file. 

If it still doesn't work then I think there might be something else wrong with your hard disk installed Grub, but I'm not sure what it could be.
We could try completely re-installing your Ubuntu Grub files and see if that helps. (I'll give you the commands for that later, if you need them).

What disk has the MBR with the bootloader for Windows? Can you boot Windows up by pressing your F8 or F12 key while your computer is booting up for a menu for selecting a different hard disk? 
If your computer's BIOS has such a menu, you can install Windows bootloader to the hard disk with Windows on it with Super Grub Disk -->'English Super Grub Disk'-->'Windows (Advanced)'-->['Fix Boot of Windows']("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Fix_Boot_of_Windows")-->(select your version of Windows)'-->(and choose which hard disk you want Windows bootloader installed to). 

Then after that you will always be able to choose Windows hard disk and boot Windows from the MBR of that disk, bypassing Grub altogether.

Will that work?

Regards, Herman :D

---

### Post by suicidal6 on 2006-12-03
Hi Herman,

i tried booting using F8, works fine...
i will try using the command line as described in the link you pointed me and see what happens...

Cheers,
Georges

---

### Post by suicidal6 on 2006-12-03
teehee problem solved!

tried booting from command line and i used:

map (hd0) (hd1)
map (hd1) (hd0)

and it worked... crazy how it was working without it and now it needs :-k 
anyway i guess i'll update my menu.lst with this and it should work fine now...

again, thank you very much for your patience and support :)

best regards,
Georges

---

### Post by Herman on 2006-12-04
Congratulations and well done! :-D

Regards, Herman

---

