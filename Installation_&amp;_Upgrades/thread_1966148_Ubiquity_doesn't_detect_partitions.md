---
title: "Ubiquity doesn't detect partitions"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by blah... on 2012-04-26
Hey everyone, I'm trying to do a fresh install of 12.04 over my existing 11.10 root partition, however when i get to the third part of the installer, it says "This computer has no detected operating systems" and gives me only the option to install Ubuntu on the whole disk or make my own partition. However a quick check of disk utility and fdisk reveals that all my partitions are there, but has a curious message of 'omitting empty partiton' ```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (8)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb030

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sda2         3074048   523397699   260161826    7  HPFS/NTFS/exFAT
/dev/sda3       523399166   955676671   216138753    f  W95 Ext'd (LBA)
/dev/sda4       955676672   976773119    10548224    7  HPFS/NTFS/exFAT
/dev/sda5       752175104   760018927     3921912   82  Linux swap / Solaris
/dev/sda6       760020992   786669567    13324288   83  Linux
/dev/sda7       786675712   955676671    84500480   83  Linux
ubuntu@ubuntu:~$ 


```
Any ideas guys? The .iso is good, i checked it.

---

### Post by blah... on 2012-04-27
Anyone?

---

### Post by Drone4four on 2012-04-27
hey man, I ran into a similar problem aeons ago back in 2008.  **[Here is my thread]("http://ubuntuforums.org/showthread.php?t=766355&highlight=partition")**.  fdisk showed 7 partitions on /dev/sda but gparted in ubiquity didn't recognize any existing partitions.  At the time there was a bug report.  See **[here]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/209974")** for that.  I never really did resolve this issue.  I ended up frying my CPU that summer and so I got a new PC and with it a new Hard Disk.  What I am saying is I never really solved the problem. Sorry, blah...I wish I could have been more helpful.

---

### Post by darkod on 2012-04-27
It seems confused because you have some sort of empty partition inside the extended. So maybe it's confused about its start/end points.

You can try running fixparts to fix any errors in the partition table:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You can also try what parted sees with:
sudo parted /dev/sda print

Compare how it will print the partition list with fdisk.

---

### Post by oldfred on 2012-04-27
Usually it is a partition table error, but I cannot see one. Another is old RAID data on drive, but you should not have been able to install before if that was the issue. I have had gparted not show entire drive when my NTFS partition needed chkdsk, so that is a possibility.

Often the issue of mounting some partition will be shown by the boot info script as it seems to mount in the same way system does. Run script and we can see if it reports anything.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by blah... on 2012-04-27
> **darkod said:**
> It seems confused because you have some sort of empty partition inside the extended. So maybe it's confused about its start/end points.

You can try running fixparts to fix any errors in the partition table:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You can also try what parted sees with:
sudo parted /dev/sda print

Compare how it will print the partition list with fdisk.What I got: ```
Error: Invalid partition table on /dev/sda -- wrong signature 0.          
Ignore/Cancel?                    
``` And oldfred I'll check that out now.

---

### Post by blah... on 2012-04-27
Here is the log, I tried using the auto repair, to no avail. [http://paste.ubuntu.com/951028/](http://paste.ubuntu.com/951028/)

---

### Post by darkod on 2012-04-27
There is definitely something invalid in the partition table. But I'm not sure how to fix that.

Have you maybe tried manipulating linux partition from windows? I'm not sure if that could leave something invalid that linux can't understand.

---

### Post by oldfred on 2012-04-27
I am not sure I have seen fixparts not work. Lets hope this shows it.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Then post the contents of PTsda.txt

Some have had fdisk  fix some errors just by having it rewrite partition table. Some have also done similar by exporting & reimporting the sfdisk export as it does not export the error or does not read it back in. But lets see what the table looks like.

Not exactly your problem, but similar ways to fix it may work.
Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

---

### Post by blah... on 2012-04-27
> **oldfred said:**
> I am not sure I have seen fixparts not work. Lets hope this shows it.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Then post the contents of PTsda.txt

Some have had fdisk  fix some errors just by having it rewrite partition table. Some have also done similar by exporting & reimporting the sfdisk export as it does not export the error or does not read it back in. But lets see what the table looks like.

Not exactly your problem, but similar ways to fix it may work.
Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)What I got when I did the command:```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 563447745 does not have an msdos signature

```PTsda.txt: ```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id= 7, bootable
/dev/sda2 : start=  3074048, size=520323652, Id= 7
/dev/sda3 : start=523399166, size=432277506, Id= f
/dev/sda4 : start=955676672, size= 21096448, Id= 7
/dev/sda5 : start=752175104, size=  7843824, Id=82
/dev/sda6 : start=760020992, size= 26648576, Id=83
/dev/sda7 : start=786675712, size=169000960, Id=83
```I'll check out what you posted.

---

### Post by darkod on 2012-04-27
That error in your post #6 seems from parted. Did you also try fixparts?

That sector reported without msdos signature is within the extended partition but outside sda5.

What you could try is copying the content of sda5, sda6 and sda7, then delete them and the extended sda3 partition. Then create them again and copy the data back.

You will probably need to make changes in fstab after recreating the partitions because the UUIDs will be different.

---

### Post by blah... on 2012-04-27
> **darkod said:**
> That error in your post #6 seems from parted. Did you also try fixparts?

That sector reported without msdos signature is within the extended partition but outside sda5.

What you could try is copying the content of sda5, sda6 and sda7, then delete them and the extended sda3 partition. Then create them again and copy the data back.

You will probably need to make changes in fstab after recreating the partitions because the UUIDs will be different.
I haven't tried fixparts. And I don't have anything to copy the data to so I can't do that... Any other possible solutions?

---

### Post by oldfred on 2012-04-27
Did you have another partition before sda5 on the drive in the space between the start of the extended partition and the start of sda4? It might have even been sda8?

  If you did have another partition with data you might try testdisk. If not, use fixparts or from sfdisk say ignore and see if it corrects itself.

If partition table does get messed up you can use the exported list from sfdisk to restore the way it is now. You do have it outside of the sda drive?

---

### Post by blah... on 2012-04-27
> **oldfred said:**
> Did you have another partition before sda5 on the drive in the space between the start of the extended partition and the start of sda4? It might have even been sda8?

  If you did have another partition with data you might try testdisk. If not, use fixparts or from sfdisk say ignore and see if it corrects itself.

If partition table does get messed up you can use the exported list from sfdisk to restore the way it is now. You do have it outside of the sda drive?
I think I even had up to sda9. I had an Arch Linux install awhile ago but in that time I would constantly be experimenting with many different Linux distros and after installing one I realized that my Arch install had disappeared, which is now that huge 117 GB chunk of free space. The install for that particular distro had gotten messed up as well during installation, and so I deleted it. I have no idea how nothing else (my Ubuntu and Windows installs) were untouched. I don't know if testdisk would work, as it was awhile ago and the data has probably been written over already. And I don't know how to use fixparts.

---

### Post by oldfred on 2012-04-27
See the link in post #6 for fixparts. Explains how to use it.

---

### Post by darkod on 2012-04-28
If I'm not mistaken, the website of fixparts has a .deb for ubuntu. Boot into live mode with ubuntu cd, download the .deb, right-click and install it.

Then in terminal you can use it with:
sudo fixparts /dev/sda

In most cases if it finds an error it can repair, it will tell you immediately and offer to do it.

Note that all this is in live mode. After you reboot fixparts is not installed anywhere and you have to do the same again next time.

---

### Post by blah... on 2012-04-28
> **darkod said:**
> If I'm not mistaken, the website of fixparts has a .deb for ubuntu. Boot into live mode with ubuntu cd, download the .deb, right-click and install it.

Then in terminal you can use it with:
sudo fixparts /dev/sda

In most cases if it finds an error it can repair, it will tell you immediately and offer to do it.

Note that all this is in live mode. After you reboot fixparts is not installed anywhere and you have to do the same again next time.
It didn't work, what I got:```
subuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda
EBR signature for logical partition invalid; read 0x0000, but should be 0xAA55
Error reading logical partitions! List may be truncated!

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): 

```

---

### Post by darkod on 2012-04-28
If you use 'p' to print the table, how will it print it?

---

### Post by blah... on 2012-04-28
> **darkod said:**
> If you use 'p' to print the table, how will it print it?
```
MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x000EB030
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048      3074047   primary              Y      0x07
   2               3074048    523397699   primary              Y      0x07
   4             955676672    976773119   primary              Y      0x07
   5             752175104    760018927   logical     Y               0x82
   6             760020992    786669567   logical     Y               0x83
   7             786675712    955676671   logical     Y               0x83

MBR command (? for help): 

```

---

### Post by darkod on 2012-04-28
How about if you try writing the table as it is with 'w'. That might recreate new extended partition without the sector that has the error. Sometimes just writing the same table removes errors.

Otherwise I don't see much that you can do to remove that error. Only copying the data, deleting all logical partitions and creating new ones.

---

### Post by blah... on 2012-04-28
> **darkod said:**
> How about if you try writing the table as it is with 'w'. That might recreate new extended partition without the sector that has the error. Sometimes just writing the same table removes errors.

Otherwise I don't see much that you can do to remove that error. Only copying the data, deleting all logical partitions and creating new ones.
So I just type 'w' and it won't do anything but rewrite the table? And well I didn't want it to come to that point but it does look like the entire MBR is pretty messed up.

---

### Post by darkod on 2012-04-28
Yes, with 'w' it will write it as it is shown at the moment, and what it shows with 'p' looks OK.

Three primary ntfs partitions and three logical linux/swap partitions. In between there is empty space which contains the sector with the error. If by recreating the extended partition it includes only the three logical, it will leave the sector with the error outside of it. Giving you more options to format that space in future, or grow the sda2 to include it, etc.

In any case, I would start thinking about regular backups, especially for the most important data, because these kind of errors could turn messy, if it doesn't go away. Be prepared, you never know when it might fail.

---

### Post by blah... on 2012-04-28
> **darkod said:**
> Yes, with 'w' it will write it as it is shown at the moment, and what it shows with 'p' looks OK.

Three primary ntfs partitions and three logical linux/swap partitions. In between there is empty space which contains the sector with the error. If by recreating the extended partition it includes only the three logical, it will leave the sector with the error outside of it. Giving you more options to format that space in future, or grow the sda2 to include it, etc.

In any case, I would start thinking about regular backups, especially for the most important data, because these kind of errors could turn messy, if it doesn't go away. Be prepared, you never know when it might fail.Success! This worked, that empty partition disappeared and all my partitions are able to be read now. Thank you.

---

