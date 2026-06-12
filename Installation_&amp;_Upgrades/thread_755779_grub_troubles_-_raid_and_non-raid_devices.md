---
title: "grub troubles - raid and non-raid devices"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by bertram_wooster on 2008-04-15
Hi,

I have had a good look around for a solution to this, but cannot find/reach a solution. It is quite a complex, but not intentionally so. I want to simplify things by moving my bootable partitions to a non-raid device, but have had some trouble doing so.

Hardware:

MSI P965 Platinum Mobo
Intel Core2Duo Processor + 2 x 1Gb RAM
Device1 - 2 x SATA 360Gb (in Raid0)
Device2 - 1 x SATA 750 Gb (as single disk).



Partitions (apologies for the complexity):

Device1 (RAID0 - 4 Primary Partitions)
 1 - (20Gb) NTFS with a mature WindowsXP install
 2 - (2Gb) Swap
 3 - (10Gb) ext3 / of ubuntu 7.10 install (with issues)
 4 - (560Gb ish) ext3 my files (mounted when needed)

Device2 (Various partitions single disk)
  1 - (100Mb) primary ext3 partition intended for /boot
  2 - (15Gb) primary ext3 partition intended for testing OSs
  3 - (30Gb) primary partition intended for migrated WindowsXP install
  4 - (650ish) Extended Partition
    5 - (500Gb) logical ext3 partition for temporary migration of files.
    6 - (Unallocated)
    7 - (15Gb) logical ext3 partition intended for new root ubuntu
    8 - (4Gb) logical partition swap.

I have had WindowsXP running for a while on the RAID device and had things set up as fake raid. I always intended to have a linux install too, but had difficulty at first setting things up. Eventually I followed advice from all the fakeRAID howtos available and managed a flaky install of ubuntu. Of most help was:

[https://help.ubuntu.com/community/FakeRaidHowto#head-7ff4f621394cd019a48906c6d332a1215852d331](https://help.ubuntu.com/community/FakeRaidHowto#head-7ff4f621394cd019a48906c6d332a1215852d331)

but this didn't work exactly, The liveCDs I used kept freezing after 3/4 of the process. In the end I realised I could ignore certain steps that I had already setup in a previous try, and I had the thing running (just). In particular the grub instructions never seemed to work fully, In the end I had to manually copy the grub setup files into the right directory, and things worked.

The problem with the ubuntu system was that there were lots of minor issues. System >admin options weren't avaialble (e.g. synaptic package manager). The terminal didn't load bash as standard. The gstreamer didn't work.

I bit the bullet and bought another disk. I want to migrate to this disk, and use the raid0 setup primarily as a file dump. However, a little knowledge is a dangerous thing. And I thought I would have separate boot, root and home partitions. I used the gutsy liveCD to set up my partitions, then rebooted into the ubuntustudio 7.10 alternate install disk. The install seemed to run fine, but the grub boot loader didn't install properly giving me:

Stage 1.5
Error 21...

I think one problem may be that I didn't include dmraid at the alternate install stage.
I had a bit of a play with things by reloading the liveCD and trying to fiddle with the grub settings, but without success. Neither device.map files (old one on raid or new) show the /dev/mapper/... details. My setup is now so complex that I may be making errors in device naming without being aware of it.

As far as I can tell, other problems might be that the bios is wrong, the bootable flags are wrong, grub might be pointing to the wrong partition, the new root install is in a logical partition, grub is still trying to access the raid disks individually, or some problem.

I have a great deal of further troubleshooting information if you want it, but I don't know what is the most relevant. So as not to dump unnecessary info I have omitted it for the time being. Please request any info you might need.

Can anyone help me troubleshoot this. I just want a simple(ish) system honest.

Cheers,
Bertie

---

### Post by dstew on 2008-04-15
> The problem with the ubuntu system was that there were lots of minor issues. System >admin options weren't avaialble (e.g. synaptic package manager). The terminal didn't load bash as standard. The gstreamer didn't work.This, I think, is part of the problem with using the debootstrap method and hand-assembling an Ubuntu system, as laid out in the FakeRaidHowTo. You could continue to work on it, and might get these to work.> I think one problem may be that I didn't include dmraid at the alternate install stage.Yes, if you just let grub install as default, it will install as if the RAID were separate disks. But, when you boot, the BIOS will report to grub that there are only two disks present, and since grub is looking for disk 3, it fails. The key is to install grub using the grub shell on your installed Ubuntu system *after* you have made it aware of the RAID by using dmraid.

I would proceed this way. Make a grub boot floppy, or use a [Supergrub disk]("http://www.supergrubdisk.org/"), and try to boot your hard disk Ubuntu installation. Install dmraid, and use it to recognize the RAID as it is. Try to mount the RAID, and if you can, fix the fstab file so it will mount the RAID at boot time. Then, use the grub shell (sudo grub on the command line) to reinstall grub as described in the FakeRaidHow to, using the grub device command to create a link between (hd0) and the RAID. Your grub root device can be the /boot partition on disk two, so in grub-speak in the RAID-aware system, ```
root (hd1,0)
```Then, when you setup grub, it will go into the MBR of the RAID, but it will be set up with block addresses coming out of a RAID-aware shell. Then, you will have to fix the menu.lst file, if one was already created, to use the correct grub roots and kernel roots, as in the HowTo. Hopefully it will boot correctly after that.

---

### Post by jbulcher on 2008-04-15
Hi,

Here's a couple of posts you might find useful. The gist of the error you are seeing is that grub can't find a disk - could be a motherboard issue, maybe a configuration problem...

[http://www.mepis.org/node/7330]("http://www.mepis.org/node/7330")
[http://ubuntuforums.org/showthread.php?t=62717]("http://ubuntuforums.org/showthread.php?t=62717")

Hope these help!

---

### Post by bertram_wooster on 2008-04-15
dstew: 

Thank you. You have cleared up some things in my understanding. I have a few further questions before I try anything, if that's ok. Apologies for being dense.

You suggest that I install grub on the MBR of the raid volume with the device command, i.e.

```

device (hd0) /dev/mapper/isw...

```

On the FakeRaidHowTo they annotate this step with the words:
"tell GRUB which device is the boot device:"

Does this simply force grub to recognise the raid array as device hd0, or does it do something further.

The boot partition on disk 2 (which should be hd1 in grub) is referred to by grub as root. Should I also run the device command to recognise the second disk, i.e.

```

device (hd1) /dev/sdc1

```

Or is there some way of checking this is done automatically at the grub command line.

If I now understand correctly, this installs the grub binary in the very first few segments of the RAID device. The bootstrap then proceeds in this order
 - The bios recognises disk1 as a RAID array (from bios fakeRaid) allowing these segments to be read to launch grub.
 - Grub now has a topology mapping defined in the MBR allowing it to recognise the Raid (now true raid).
 - Grub is pointed towards the boot partition where it reads the menu.lst, and device.map files.
 - Depending on the menu.lst file, this then launches the kernel file and mounts the file system, giving me the ubuntu os we all know and love.


If this is true then I don't understand what the device.map file is for. I thought it was the topology mapping that allowed grub to read the raid array.

Thanks again for your help dstew.

---

### Post by dstew on 2008-04-15
> Does this simply force grub to recognise the raid array as device hd0, or does it do something further.I think that is all it does. The BIOS at boot time will report the RAID to the grub loader as a single disk, and (hd0) will be the MBR of that disk. I don't know exactly how the BIOS interacts with the disks in the RAID to do this, but it seems to work. I guess it worked for you originally. This is different than how a pure software RAID works, though. In that case, the BIOS does not have the ability to see the software RAID disks as a single device. The RAID is only "there" after the operating system is booted.> Should I also run the device command to recognise the second disk, i.e.I don't think that would hurt. Just for fun, you might see if it works without doing that. If it doesn't work, try it.> If this is true then I don't understand what the device.map file is for.Overall, your description seems right to me. I am not entirely sure what the device.map file is for, I think the device.map file gets read after the stage2 file has already been loaded, but I am not sure it is used during OS loading. It might only be used by the grub shell for guiding installations and updates. A device.map file was not used in the FakeRaidHowTo during the grub install process, only the device command. Probably a device.map file could have been created and used, but the writer took a different, more direct approach. But however it is done, either with device.map or with the device command, the grub shell was informed of two things: first, where to install the stage 1 (where the MBR is), and second, how to make the correct block address in the MBR and stage1.5 portions, so that grub could find and load its stage2.

---

### Post by bertram_wooster on 2008-04-15
dstew:

Thanks again for your reply.

I haven't got easy access to a cd writer, so instead of your supergrub approach I used the live CD install for ubuntu, but followed your/FakeRaidHowTo instructions from there.

In particular I ran the following commands in grub after installing dmraid:

```

> device (hd1) /dev/sdc
> device (hd0) /dev/mapper/isw_...
> root (hd1,0)
> setup (hd0)

```

I had forgotten about the setup command in my previous post. I guess this schedules the uploading of grub to the MBR. I ran the update-grub commands and all that gubbins without errors. However, when I looked in menu.lst the root seemed to be hd2 (not hd1), this is I guess because it still 'sees' the raid disks separately as sda and sdb.

I edited the fstab file nonetheless and rebooted with the root device set to hd2, this failed with grub error,

```

error 21 device not found

```

(I think). I rebooted with the live CD and changed hd2 to hd1 in the menu.lst, this gives:

```

error 17 device cannot be mounted.

```

Interestingly, the Raid XP boot option now gives

```

error 13 Invalid or unsupported executable format

```

and the Raid Ubuntu boot option gives

```

error 15 File not found.

```

Which is a change on before where they all gave error 21. I think this means that grub is at least recognising the raid volume now. But not the single disk. I think tomorrow, I may have another crack with the supergrub disk, if I have time.

Thanks again for your help.

---

### Post by bertram_wooster on 2008-04-15
jbulcher:

I had looked through the available online references to error 21 that you sent. This is where I got the info to make bios changes, but this didn't seem to make a difference.

Thanks for your post though. It may well be a motherboard issue. I will investigate if the grub stuff comes up blank.

---

### Post by dstew on 2008-04-15
What is significant about these new errors is that they have a verbal explanation along with them. That means they are stage 2 errors. Congratulations! You are loading stage 2 from somewhere!

Anyway, the errors have to do with the menu.lst file at this point. Grub is installed correctly, I think. Is it possible that grub is getting the old menu.lst from your RAID installed system? Are you sure it is finding the new menu.lst? Anyway, we need to work on the menu.lst file to finish up the installation. > I ran the update-grub commands and all that gubbins without errors. However, when I looked in menu.lst the root seemed to be hd2 (not hd1), this is I guess because it still 'sees' the raid disks separately as sda and sdb.At this point you had to change the (hd2)'s to (hd1)'s, because when the RAID is operational, /dev/sdc will be (hd1). In order to make it so that update-grub does not mess up menu.lst you have to make the changes in the menu.lst file Automagic parameters as mentioned in the HowTo. You might also make a device.map file with the correct mappings. And, you have to make sure the kernel root statements are correct.> I edited the fstab file nonetheless and rebooted with the root device set to hd2, this failed with grub error,No! It should be (hd1).> I rebooted with the live CD and changed hd2 to hd1 in the menu.lst, this gives:Yes, this is better. The error you got is now "error 17 device cannot be mounted."  But, we need to make sure that grub is pointing to and using the new menu.lst file. Boot the Live CD again, and re-install dmraid (it will disappear each time the Live CD system is stopped). Once dmraid has recognized the RAID, post the output of fdisk -l. Also, see if you can mount the RAID and the un-RAIDed disk onto your liveCD system. You should be able to. If you can mount them, look at the /boot/grub/menu.lst file in each to make sure that you are working on the correct menu.lst. Please post the contents of the whole menu.lst file so we can have a look at it.

---

### Post by bertram_wooster on 2008-04-16
dstew:

> 
What is significant about these new errors is that they have a verbal explanation along with them. That means they are stage 2 errors. Congratulations! You are loading stage 2 from somewhere!


You are right, it is getting to stage 2, but I am pretty sure that the new menu.lst file is accessed. I have posted both files and I have edited the first boot option title in each menu.lst so that I know for certain which one is being read.

On reboot, the grub menu's first option reads (Non-Raid Menu.lst)... so I am sure that the first partition on /dev/sdc1 is being accessed.

There are 4 potential os's btw: a generic and real-time kernel on the single disk, and a generic and XP on the raid. Either kernel on the single disk is ok, I can scrap the other. I added one manually as part of yesterday's test.

> 
Once dmraid has recognized the RAID, post the output of fdisk -l. 


```

luke@aristotle:/tmp$ cat /tmp/fdisk.output.txt 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f6d4f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2800     2008125   82  Linux swap / Solaris
/dev/sda3   *        2801        4000     9639000   83  Linux
/dev/sda4            4001       77826   593007345   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x582daa16

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4273

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   83  Linux
/dev/sdc2              14        1971    15727635   83  Linux
/dev/sdc3            1972        5887    31455270    b  W95 FAT32
/dev/sdc4            5888       91201   685284705    5  Extended
/dev/sdc5           90680       91201     4192965   82  Linux swap / Solaris
/dev/sdc6           88722       90679    15727603+  83  Linux
/dev/sdc7            5888       71158   524289244+  83  Linux

Partition table entries are not in disk order

```

A couple of questions:

Do I need to install grub on the MBR of the raid volume, for grub to be able to read and boot installations from the raid? I was thinking that things would be less flaky if I used the single disk as the repository of all the grub stuff. Just a thought.

In the device.map file can I use the UUID representation of the single disk? What about when using the device command to grub, i.e.

```

device (hd1) UUID=81e2c7a2-05a7-4908-9fb3-a35092693fcc

```

for the time being my device.map file is as follows

```

(hd0)   /dev/mapper/isw_ccddgdghai_the_ant_colony
(hd1)   /dev/sdc

```


I have just seen that in the menu.lst for the single disk, some lines of the boot option for the raid linux os have been truncated, my first job will be to change this. Also, the kernels in the non-raid options are given as /boot/vmlinuz... this needs changing too. I will experiment after this post.

---

### Post by dstew on 2008-04-16
> Do I need to install grub on the MBR of the raid volume, for grub to be able to read and boot installations from the raid?No, you can install grub in the MBR of any disk, or even in a partition of a disk. It depends on whether or not your BIOS can be instructed to boot that partition or disk. If you install grub on the MBR of /dev/sdc, you have to tell your BIOS to boot that disk before the RAID.> Also, the kernels in the non-raid options are given as /boot/vmlinuz... this needs changing too. I agree that the truncated root statements need changing, but I am not sure you need to change those /boot/vmlinuz... paths. It depends on what is specified as the root for grub. If the kernels are in the /boot directory of /dev/sdc, and if you install grub so that its root is /dev/sdc, then those lines are correct. Grub stage1.5 has enough brains that it can find the /boot/grub directory to get its stage2 and menu.lst file, once it knows which partition to look in. That partition is specified by the root statement that was given to the grub shell at the time the boot loader was installed. Grub stage1.5 is able to understand the file system of the root partition. It might be more difficult to figure out how to direct grub to the RAID file system, to boot the kernels there, but for that I would refer to the HowTo.

One more thought: is the RAID still intact? It is possible that it needs to be repaired, since fdisk can see a normal partition table in /dev/sda. I really don't know much about that, though. What is the output of sudo dmraid -ay? Is dmraid happy with the current setup?> In the device.map file can I use the UUID representation of the single disk?I could not find anywhere that the grub device command or device.map file can take a UUID as an argument. It needs to be a device file name, such as /dev/sdc, or as a devicemapper file name. See [the grub manual]("http://www.gnu.org/software/grub/manual/grub.html#device").

---

### Post by bertram_wooster on 2008-04-17
dstew:

Apologies this is quite a long one.

> 
is the RAID still intact?
...
What is the output of sudo dmraid -ay? Is dmraid happy with the current setup?


Firstly I installed dmraid and collected the first output from each of the commands below:

```

$ dmraid -ay 
RAID set "isw_ccddgdghai_the_ant_colony" already active
RAID set "isw_ccddgdghai_the_ant_colony1" already active
RAID set "isw_ccddgdghai_the_ant_colony2" already active
RAID set "isw_ccddgdghai_the_ant_colony3" already active
RAID set "isw_ccddgdghai_the_ant_colony4" already active
$ dmraid -r 
/dev/sda: isw, "isw_ccddgdghai", GROUP, ok, 625142446 sectors, data@ 0
/dev/sdb: isw, "isw_ccddgdghai", GROUP, ok, 625142446 sectors, data@ 0
$ dmraid -s 
*** Group superset isw_ccddgdghai
--> Active Subset
name   : isw_ccddgdghai_the_ant_colony
size   : 1250275840
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

```

This corresponds to what I got when I first installed the linux os on the RAID volume, and that booted ok.Also, I can mount the ext3 raid partitions once I have installed dmraid via the live CD, and I can access the files on those filesystems

Of possible relevance, when I open up gparted and look at the raid volume as a whole there is a triangular caution symbol next to the two ext3 and the NTSC partitions. When I access the  information on the ext3 partitions (from the right click menu) I get the following error message:

```

e2label: Bad magic number in super-block while trying to open /dev/mapper/isw_ccddgdghai_the_ant_colony

Couldn't find valid filesystem superblock.

dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: Bad magic number in super-block while trying to open /dev/mapper/isw_ccddgdghai_the_ant_colony
Couldn't find valid filesystem superblock.

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.

```


Running e2label and dumpe2fs at the command line on the RAID volume itself, I get the same message, i.e.

```

e2label /dev/mapper/isw_ccddgdghai_the_ant_colony

```

However, running this command on the ext3 partitions gives no error message, i.e.

```

e2label /dev/mapper/isw_ccddgdghai_the_ant_colony3

```


Finally, you say

> 
If the kernels are in the /boot directory of /dev/sdc, and if you install grub so that its root is /dev/sdc, then those lines are correct.


As far as I know the kernels are in the / directory of /dev/sdc1 this being mounted on the /boot directory of /dev/sdc2. When I ran update-grub again I got the location without the /boot part.

Apologies again for this being such a long post. I have looked around the man pages and the web for clues, but I cannot seem to find relevant help. I have posted the menu.lst and fstab files to view. On reboot the grub errors are the same as in my last post.

Thanks again.

---

### Post by dstew on 2008-04-17
It looks like the RAID is intact. I don't know if gparted can recognize the RAID, I think only fdisk can do that.> As far as I know the kernels are in the / directory of /dev/sdc1 this being mounted on the /boot directory of /dev/sdc2.I see you have a separate /boot partition, my apologies. In that case, you need to remove the /boot from your kernel and initrd lines in the menu.lst file. When you installed grub, you gave it the root of (hd1,0), correct? That is what it should be if the RAID is operational. One way to check that is to look at the device.map file. It should list (hd0) as the device-mapped RAID, and (hd1) as the /dev/sdc disk. Then (hd1,0) should point to the /dev/sdc1 partition, which contains the grub menu.lst and the kernel images. Once the kernel is loaded and running, the /dev/sdc1 partition will be mounted to the /boot mount point in your root file system.

EDIT: I see your device.map file on the previous page, it is as it should be. If you edit the kernel and initrd lines, you should be better off.
EDIT again: I see you edited the lines. It still doesn't work? You get the menu, correct? What is the grub error you get when you choose the generic kernel?

---

### Post by bertram_wooster on 2008-04-17
dstew:

Yes. The new menu.lst file from the last post has the /boot part omitted.

And the RAID seems to be intact, but I still can't boot.

The frustrating thing is that I have removed all mention of the RAID disk from fstab (commented out rather). So the only complication in booting from the single disk is that grub resides on the RAID volumes MBR, but since we get stage2 errors that would imply that grub at least loads.

I noticed after I posted the last, that the menu.lst file gives the same UUID for both the rt and the generic roots. This corresponds to /dev/sdc6 . I cannot seem to chroot into a /dev/sdc6 based system though, and have been configuring grub on a system setup with 

/ as /dev/sdc2
/boot as /dev/sdc1

I just tried this again. And again the menu.lst file picks up the wrong root uuid. I tried manually changing the root uuid to the one that corresponds to /dev/sdc2 and rebooting but that doesn't work either.

---

### Post by dstew on 2008-04-17
At this stage in your setup the fstab file is not coming in to play. It is read by the kernel, and so far I don't think you are getting the kernels to load. We are still in the grub menu configuration stage.

Since you get the menu, grub is installed correctly. The problem has to lie in the menu.lst file. You can try some experiments from the grub menu, by pressing 'e' to edit lines in the menu item. Highlight the menu item you want to work on, press 'e', then highlight the specific line in the menu item you want to change, then press 'e' again. Make the changes, press 'enter', then 'b' to boot. The edits you make this way are not saved, they only affect that one boot. You can try different things, like changing the root designation (which I think is correct), or changing the kernel line. Watch the errors you get after the changes, that can also be a clue. You can also get a grub command line at the menu by pressing 'c', which might be useful.

Again, what is the exact error you get when you try to boot the generic kernel? I agree that if the kernel root UUID points to /dev/sdc6, that is wrong. One thing, make the changes to menu.lst (or better, edit menu items from the menu) directly, but do not use install-grub or update-grub at this point, in case you were doing that. But, if the only problem is the UUID, you should get a kernel error, I think, and not a grub error.

---

### Post by bertram_wooster on 2008-04-17
dstew:

Oooo, I've made some progress. Thank you.

Right, I have deleted the /dev/sdc6 partition, but the update-grub still tries to write this UUID to the menu.lst file. Instead I edited menu.lst (with nano) and changed root to /dev/sdc2, I also went into the bios and changed the boot order of the raid and single disk volumes.

Boot order was:
DVD
Single DIsk
RAID

Boot order is now:
DVD
RAID
Single DIsk.

Something somewhere made a difference. However, when I try to boot the non-recovery kernel on the single disk. I get a message about /var/log/dmesg and incorrect user:group ownership of some file .../daemon/(something).

I am however, happier. I will play and get back to you (maybe in a couple of days).

---

### Post by dstew on 2008-04-17
> update-grub still tries to write this UUID to the menu.lst fileUpdate-grub uses the configuration options in the upper part of menu.lst to re-create the menu.lst file. Look at the upper part of the file, and you will see the #kopt (kernel options) value. This is added to the kernel line every time you run update-grub, so you see how you get the bad UUID back again and again. Better not to run update-grub unless all the configuration options are correct.

As far as what you changed that made it work, it could be the boot disk order. Some BIOSes will change their drive enumeration when you change boot order, so maybe in the first case, the single disk was (hd0), and in the second case (hd1). Since you set up grub to expect the single disk to be (hd1), probably that is what happened.

---

