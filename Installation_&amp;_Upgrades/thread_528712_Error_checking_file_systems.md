---
title: "Error checking file systems"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Vadi on 2007-08-18
Hello,

I've installed Ubuntu and Edubuntu on two different partitions recently (ubuntu first, then edubuntu). Edubuntu loads fine for me, but ubuntu gives me an error when loading, the "checking file systems" step fails. Then it goes into a recovery console (I don't remember the name exactly, and unfortunately I don't know how to save the log of the booting process), and says that I should press Ctrl+D to resume booting.

So then I press Ctrl+D, and ubuntu loads fine. But I want to know if this is fixable?

I think there might be a small issue with my swap drives - when I patritioned the disk, I created 2 ext3 patritions for the two linuxes and two swap ones. But when installing, I wasn't exactly given a clear option as to which linux will use what swap file.

Is there anything I can do to make my ubuntu bootup normal?

---

### Post by super carrot on 2007-08-18
Maybe someone else has a smarter answer, but I would go for a reinstall personally. It still seems to me that your root file system is corrupt, you could run a fsck -Ca on it ( I think those are the best options) but with what you said about swap ( usually linux just recognises swap and doesn't have any problems ) I think that the quickest way may be to just to a re install, when the partitioner comes up, you will be able to see what partitions are what.

---

### Post by trak87 on 2007-08-18
I don't know if this will help, but...

In the past I believe one could share swap files among different distros, but I've recently read that the suspend/hibernate options store vital info in the swap that can't be shared. If you reinstall, be sure to assign swap partitions uniquely to each distro.

---

### Post by dabl on 2007-08-18
> **trak87 said:**
> 

I've recently read that the suspend/hibernate options store vital info in the swap that can't be shared. If you reinstall, be sure to assign swap partitions uniquely to each distro.

I think that's true for laptops, and not true for desktops.  I'm running a desktop with multiple hard drives, and a single swap partition on one of them.  Whichever Linux OS I boot is happy to use that swap partition while retaining all of its unique settings.

---

### Post by Vadi on 2007-08-18
The problem is that I -wasn't- given a clear option as to which swap the installed system would use.

I don't feel like reinstalling again, because I did the two patritioned install as a result of already messing up my computer bad... but hibernate is something that I'll definitely need. Or at least sleep.

Are there any other options? Because I don't know how to reinstall and assign a unique swap to the os'.

---

### Post by Herman on 2007-08-18
Hello Everyone,
Vadi, I think your first problem would be in your /etc/fstab file which tells your operating system which partitions are which as the system boots up.

You can edit that if you want and assign one swap area for each operating system if you like, but I don't imagine that will be your main problem.

I am guessing that cause of your main problem will be that you already made two ext3 partitions prior to installing one operating system and then the other.
The first operating system might have the UUID number that the then empty second ext3 partition had at the time the first OS was installed.
Then when you installed an OS in the spare ext3 partition you would have had to format the partition again, right?
So you have a new UUID number in there now compared with when the first OS was installed.
That's my guess.

It will be easy to fix. Just open your /etc/fstab file in the OS with the problem with sudo gedit /etc/fstab

[COLOR=Red]EDIT: Oh-oh, I almost forgot to tell you to make a backup of your /etc/fstab file first, sudo cp /etc/fstab /etc/fstab_backup```
sudo cp /etc/fstab /etc/fstab_backup
```[/COLOR]

*** Now ***you can open your /etc/fstab file in the OS with the problem with sudo gedit /etc/fstab ```
sudo gedit /etc/fstab
```Now, switch to another desktop (the little squares in the right-hand bottom corner, click on  an empty one), then open a new terminal, and run blkid for a list of your partitions and UUID numbers.
```
blkid
```Make sure the UUID numbers in your /etc/fstab file agree with the output from blkid, and if they don't, then copy the ones from blkid and paste them over the ones in your /etc/fstab carefully, (make sure you read where you are putting them first), until your /etc/fstab is corrected.

You can also see which swap area is allocated to the operating system and take note of that. If more than one swap is allocated you can 'hash out' one by placing a # mark at the beginning of the line to make the OS ignore that line.

If you have trouble figuring it out just post your two /etc/fstab files here and your output from blkid and I or someone here will help you with it.

Regards, Herman :)

---

### Post by Herman on 2007-08-18
I always just have one big swap area and let all my OS's share the same one, they all just grab whatever swap area they detect on installation. I don't use hibernate mode at all, maybe it's something I should try, maybe I'd like it if I get used to it.  I have read someone who does use hibernate mode say that you shouldn't share the same swap area in that case, so you will be correct to allocate a different swap area to each OS for that reason.

That is probably a secondary problem though.

Regards, Herman :)

---

### Post by Vadi on 2007-08-18
Hello,

Yes, I think you were exactly right - it saved a log, and here's what the log says:

```
Log of fsck -C -R -A -a 
Sat Aug 18 16:38:18 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=047d9c51-11dd-46b4-833a-318c0e4b5b35'

fsck died with exit status 8

Sat Aug 18 16:38:18 2007
----------------
```

So from what I understand, yes it is unhappy that the UUID is changed.

Here is what my fstab and blkid say initially:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=7bcf3b2d-c32a-4115-9d92-441224b64b68 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=047d9c51-11dd-46b4-833a-318c0e4b5b35 /media/sda1     ext3    defaults        0       2
# /dev/sda2
UUID=ed644684-bdfa-4942-bf98-e143145cd403 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

```
/dev/sda1: UUID="2edbba3d-b81b-4677-8452-766be6907472" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="ed644684-bdfa-4942-bf98-e143145cd403" 
/dev/sda3: TYPE="swap" UUID="53981891-40cb-4c91-a436-65dcedd2a218" 
/dev/sda4: UUID="7bcf3b2d-c32a-4115-9d92-441224b64b68" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb: UUID="10DB-E6EF" TYPE="vfat" 
```

The last one should be ignored though, as that's my USB drive I'm thinking.

So, hm... it looks like the file isn't saying anything about my *other* swap, the one that I untended for edubuntu. Or ubuntu. I have no idea who's is it using.

What would you recommend that I change my fstab to?

Thank you for the very detailed help by the way, it's great.

---

### Post by Herman on 2007-08-18
Here is what your fstab for whichever Linux you have in /dev/sda4 should say now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda4
UUID=7bcf3b2d-c32a-4115-9d92-441224b64b68 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=[COLOR=Red]2edbba3d-b81b-4677-8452-766be6907472[/COLOR] /media/sda1     ext3    defaults        0       2
# /dev/sda2
UUID=ed644684-bdfa-4942-bf98-e143145cd403 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```and your /dev/sda4 Linux will be using your /dev/sda2 partition as a swap area.

```
/dev/sda1: UUID="2edbba3d-b81b-4677-8452-766be6907472" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="ed644684-bdfa-4942-bf98-e143145cd403" 
/dev/sda3: TYPE="swap" UUID="53981891-40cb-4c91-a436-65dcedd2a218" 
/dev/sda4: UUID="7bcf3b2d-c32a-4115-9d92-441224b64b68" SEC_TYPE="ext2" TYPE="ext3"
```
Regards, Herman  :)

---

### Post by Herman on 2007-08-18
> it looks like the file isn't saying anything about my *other* swap, the one that I untended for edubuntu. Or ubuntu. I have no idea who's is it using.Allright, which one is in /dev/sda4 then? Ubuntu or Edubuntu?

Your sda4 Linux install is using your sda2 swap, so now all you need to do is boot into your other Linux, in /dev/sda1, and check the /etc/fstab file in that one to see if it's using only your /dev/sda3 swap.

If it's using both swap areas, just delete one out of the /etc/ftab file for that OS, or else just # hash it out.

It your sda4 Linux install also is using the wrong swap area, (sda2, which your other install is usning too, then copy and paste the UUID number corresponding with the swap area you want it to use, (sda3), over the wrong entry in sda4's /etc/fstab file. Save and close the file. That should fix it.

Regards,Herman  :)

---

### Post by Vadi on 2007-08-23
Thanks, I've fixed the issue with loading on Ubuntu (sda4) with your help.

However edubuntu now needs to be removed to make space for ubuntu... what would be the best way to go about modifying the patritions & grub?

---

### Post by Herman on 2007-08-23
Your Master Boot Record will have code in it to make it point to whichever operating system you installed last, Edubuntu or Ubuntu.

If you installed Ubuntu last and you want to delete Edubuntu, you  won't need to do anything to GRUB except maybe delete the entry for Edubuntu in your Ubuntu's /boot/grub/menu.lst, because you won't be using it anymore.

If you installed Edubuntu last and you want to delete Edubuntu, you would need to 'reinstall GRUB' from Ubuntu. 'Reinstall GRUB' here means to have Ubuntu's GRUB's stage1 file written to MBR, to make the MBR point to GRUB in  Ubuntu instead of the GRUB in Edubuntu. (Which will be gone).

There are lots of ways to re-install GRUB. 
Here's how to re-install GRUB from a GRUB shell, in any operating system that has GRUB in it, including a Live CD, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

The easiest way is to use a [Super Grub Disk]("http://geocities.com/supergrubdisk/") CD, floppy disk or USB, With one of those you can do any work with boot loaders even if your operating system won't boot up at all, and even if it has no GRUB in it at all, or if there is a problem with the boot loader part of the MBR. It's always a good idea to have a [Super Grub Disk]("http://geocities.com/supergrubdisk/") somewhere around your computer for emergency booting in case you should ever need it.

You should always make a backup of your files before using any hard disk partitioning software.

You can use any hard disk partition editing software for deleting a partition or two.
It is best to avoid using any commercial or proprietary partitioning programs as those tend to be made for Windows mainly and are not always very good. Just because you have to pay for some software does not mean it is good.
 It is best to use a good libparted based partitioning software like 'Parted, GParted, Gnome Partition Editor (in the Ubuntu Live CD), QTParted or similar.

You can use any hard disk partition editing software for resizing a partition 'to the right' of towards the center of a hard disk.
The best in my opinion is [GParted -- LiveCD]("http://gparted.sourceforge.net/"). If you use a GParted LiveCD, you will even be able to resize your Linux partition to the left if you need to. 
GParted LiveCD includes [Partimage]("http://ubuntuforums.org/Main%20Page%20-%20Partimage"), for making a backup of entire partitions before you edit your partitions or any time you like.
Special versions of GParted LiveCD also include [Clonezilla]("http://clonezilla.sourceforge.net/"), which can also back up a partition or even back up an entire hard disk if you want to.
Usually it's enough just to make sure your files are all backed up on some other media.

Regards, Herman :)




.

---

### Post by Vadi on 2007-08-23
Unfortunately I don't remember which I installed first...

When I'm presented with GRUB at bootup, Edubuntu kernels are listed first, then it says "other operating systems", and then ubuntu ones are listed.

I'm guessing that I installed Edubuntu last then, but do you think you can confirm that?

And thank you very much for your excellent help.

---

### Post by Herman on 2007-08-23
Yes, I agree with you, if the Edubuntu boot entries are listed in the automagic kernels list above the Ubuntu entries in your GRUB menu, it would indicate that you installed Ubuntu first and then Edubuntu.
That means you will find it easiest to install Ubuntu's GRUB to MBR just before you delete Edubuntu.
If you have a [Super Grub Disk]("http://geocities.com/supergrubdisk/") or a Ubuntu Live CD it won't matter, you can do it first or later, but your Ubuntu will be temporarly unbootable until you restore your Ubuntu's GRUB stage1 file to MBR.

And no problem about helping, there are lots of us here in Ubuntu Web Forums who enjoy helping new Ubuntu users, you are more than welcome to ask about anything you want help with. 

Regards, Herman :)

---

