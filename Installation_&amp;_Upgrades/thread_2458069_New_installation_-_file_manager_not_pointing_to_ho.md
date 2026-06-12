---
title: "New installation - file manager not pointing to /home"
date: 2021-02-15
forum: Installation &amp; Upgrades
---

### Post by jerrywo on 2021-02-15
So I installed 20.04.2 and used GPARTED to designate my solid state drive (with all my folders, files, etc) as /home and did not format it

Now it seems during the install, UBUNTU creates another /home folder with a bunch of empty folders (pictures, music, downloads, etc.)
In fact that empty home folder has a little "home" symbol on it

How do I make the UBUNTU file manager point to my actual folder?
A slight complication:  That original filename had a typo - had my name as jerrryw instead of jerryw 

Distro looks nice!

Jerry
Warrenton, VA

---

### Post by CelticWarrior on 2021-02-15
It's probably faster to reinstall it correctly.
Whenever you want to use a customized partitioning you must choose "something else" and select all the required partitions.
The installer can't guess that you want a separated /home. Bt default /home is under /, not a separated partition.

---

### Post by oldfred on 2021-02-15
Probably easier to reinstall, as Celtic Warrior suggests.
Just because you said in gparted which partition is /home, does not let installer know that.
And in the option in the installer to use /home (change button), DO NOT check the format box.

You can change the new default /home to your other /home partition.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)

---

### Post by Impavidus on 2021-02-15
It sounds to me &#8211; but I might misunderstand your post &#8211; that you installed Ubuntu 20.04 and wanted to keep your /home partition from your previous install. However, you made a typo in either your original or your new username, so the names are different. The result would be that the /home partition contains two directories, one with the old, one with the new username: /home/jerryw and /home/jerrryw. Both would have the same owner.

If this is indeed the case, it's simple to solve. Best to do this from a live disk or in recovery mode, so you're not logged in as you fix it. Rename the new directory to some temporary name, rename the old directory to the original name of the new directory, then log in. If it all works, delete the new directory (that now has the temporary name).

---

### Post by jerrywo on 2021-02-16
Thanks to all who replied - I've been wrestling with printers over the last two days (I won!).

So when I do a fresh install and wish to retain my /home from the previous OS - I designated that partition as /home - yet the 
Ubuntu install created another /home partition.  I'm having some headaches with hidden folders...but oldfred, do I, when using
Gparted mark that drive to be /home and then hit the "change button".  Do I have that right?

Does that keep the installer from creating another /home folder?

Jerry

---

### Post by CelticWarrior on 2021-02-16
> **jerrywo said:**
> Thanks to all who replied - I've been wrestling with printers over the last two days (I won!).

So when I do a fresh install and wish to retain my /home from the previous OS - I designated that partition as /home - yet the 
Ubuntu install created another /home partition.  I'm having some headaches with hidden folders...but oldfred, do I, when using
Gparted mark that drive to be /home and then hit the "change button".  Do I have that right?

Does that keep the installer from creating another /home folder?

Jerry

No, you're still not understanding that what you do in GParted is irrelevant for the installer. Please read again post #2. You can partition in advance but then you CAN'T use the automated install, you MUST choose "something else" and MANUALLY select all the required partitions including, if applicable, a preexisting EFI System Partition. That is: (If applicable) select the ESP as "EFI", then create and select the root partition using any unallocated space, as "root" (/) and with EXT4 file system (can be others but they aren't recommended at your level), tick format (or not, if new and blank it doesn't matter, then finally select your previously defined /home as /home (format or not is now up to you; DON'T format if /home is being "recycled" from a previous installation, obviously).

The installer does not and cannot know what you want to do. It won't touch or use other partitions unless you explicitly tell it to, with the exceptions of the special ESP for obvious reasons and any previous swap partition (not needed currently as Ubuntu has been using swapfiles for years) will be used as well.

---

### Post by oldfred on 2021-02-16
Found this older Something Else for Mate flavor.
It shows using Something Else to select / and then another screen shot showing selecting /home.
Different flavors & newer versions may look slightly different, but are the same otherwise.

You can partition during install, but if partitions exist, you have to use Something Else and then for each partition choose the change button.
Be sure you select correct partition. Once I created two new partitions one smaller for / and one larger for /home, but then reversed that when using Something Else.

[https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651](https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651)

---

### Post by jerrywo on 2021-02-16
Thanks Celtic Warrior, and others

I did use "something else" and had the following in Gparted:
sda
    sda1  ext4  /home   1000203 GB     no format

sdb
   sdb1        bios/grub  9999GB
   sdb2        efi             9999GB
   sdb3   ext4  /           299999    format
   sdb4    swap

I had installed a new 1TB solid state drive and wanted to dedicate that for my /home folder

Somewhere along the line, sdb became the home of my "boot" folder.

Times have changed - I got a low space alarm on / (root) because of software I down-loaded (kiCAD)
and took the opportunity to do a clean install

Am I, or  rather was I, on the right track?

Once the install was done, I found a new /home with a half dozen empty folders.

Jerry

---

### Post by yancek on 2021-02-17
>  Am I, or  rather was I, on the right track?


No.  As pointed out above (in 2 separate posts) what you set using GParted is irrelevant.  You need to use the manual option (Something Else) and select the partition you want for /home in the installer Installation Type window.  Select NOT to format there.  

> sdb1        bios/grub  9999GB
   sdb2        efi             9999GB 

You don't need BOTH a bios-grub partition and an EFI partition, you only want one.  The size of an EFI partition is generally around 200MB, sometimes as large as 500MB but no more than that should ever be necesasry.   You should have a / filesystem partition of 20-30GB.

---

### Post by ajgreeny on 2021-02-17
It is just possible that if your username is the same as the original /home partition user, (and I am not sure if that is now the case or not), and that partition still contains all the files and folders that it did before, that you may be able to reset the /home partition back where you wanted it, ie, as /home in your new system.

Show us the content of /etc/fstab and also the output of sudo blkid with command ```
cat /etc/fstab
sudo blkid
```
No promises, and make sure you backup fstab before doing anything but knowing the UUID of your old /home partition it may be possible to edit fstab and add appropriate lines like this but using your UUID of course for the old home ```
# /home from bionic mounted at installation.
UUID=0cd847e0-572c-459d-8429-154cac24f4fb /home	ext4	defaults	0	1
```  to ensure that it mounts as /home at boot.
You can check any edits you make to fstab by immediately running ```
sudo mount -a
``` after saving the new fstab version; if there are no errors the partition should now be mounted as you /home partition; if errors are shown restore the backup you just made.

---

### Post by jerrywo on 2021-02-17
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=bb725cef-8875-4a82-bcd9-c682f337ee9b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=E476-E134  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda1 during installation
UUID=31b39630-10d3-4910-a80e-6bfd8a999ff0 /home           ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=b46b216b-b048-4f57-a60a-c6fc5f7902fe none            swap    sw              0       0


and

sudo blkid
[sudo] password for jerryw: 
/dev/sdb3: UUID="bb725cef-8875-4a82-bcd9-c682f337ee9b" TYPE="ext4" PARTUUID="2560e513-5d20-4aa6-bddb-123517018775"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sdb1: UUID="a41b9953-c5ba-41ac-8685-15d6edf8c8c3" TYPE="ext4" PARTUUID="31c85444-333a-49b5-9cb1-5dbb1459f65d"
/dev/sdb2: UUID="E476-E134" TYPE="vfat" PARTUUID="18760245-32b1-45cb-bedd-779cc3766fe8"
/dev/sdb4: UUID="b46b216b-b048-4f57-a60a-c6fc5f7902fe" TYPE="swap" PARTUUID="91d27323-55bc-4e90-8d2f-5e8e148580ca"
/dev/sda1: UUID="31b39630-10d3-4910-a80e-6bfd8a999ff0" TYPE="ext4" PARTUUID="19dd95f9-dbd9-419f-bcf8-00847bd3969f"

I'll wait on the other stuff

Jerry

---

### Post by jerrywo on 2021-02-17
Actually I DID use the manual option.

On my initial try Gparted demanded that I set up a efi partition.  So, since I had all the space in the world - I complied

Thanks
Jerry

---

### Post by ajgreeny on 2021-02-17
So again, is the username the same on your old OS as the new OS?
The /home partition UUID is correct for /dev/sda1 to be mounted as /home so it may be interesting to see the output of ```
ls /home
``` to see if both versions of username, jerryw and jerrryw are present and have folders in /home.

---

### Post by jerrywo on 2021-02-17
The results of ls /home:

jerrryw  jerryw  lost+found  timeshift

The "jerrryw" folder is empty as I copied all the files over to "jerry".

This is all so messed up that I'm inclined to re-do the install.  

Jerry

---

### Post by jerrywo on 2021-02-17
So it looks like my home folder at sda1 was correctly identified during installation
See:
# /home was on /dev/sda1 during installation
UUID=31b39630-10d3-4910-a80e-6bfd8a999ff0 /home ext4 defaults 0 2

so, why does the install create a /home folder with empty folders, like pictures, videos, etc.

Does it have to do that because it creates some hidden folders related to the applications being installed?

Jerry

---

### Post by ajgreeny on 2021-02-17
> **jerrywo said:**
> So it looks like my home folder at sda1 was correctly identified during installation
See:
# /home was on /dev/sda1 during installation
UUID=31b39630-10d3-4910-a80e-6bfd8a999ff0 /home ext4 defaults 0 2

[COLOR="#FF0000"]so, why does the install create a /home folder with empty folders, like pictures, videos, etc.[/COLOR]

Does it have to do that because it creates some hidden folders related to the applications being installed?

Jerry
It created a new /user folder with the new name jerryw because that is what you told the installer to do; it is the consequence of your typo in the username, I'm afraid. The partition is correctly mounted but your different username means the old user home/jerrryw folder was not the one which the system used; it created a new home/jerryw home folder.
However. it should be easy enough for you to now move the files and folders from the old, incorrectly named home folder to the new correctly named home folder, then change ownership of all those files and folders to your correct username with (I hope I have this username now correct!) ```
sudo chown -R jerryw:jerryw /home/jerryw
``` and then delete the incorrect /home/jerrryw folder.
In fact it may be even simpler to rename the incorrectly named folder with the files in them to whatever the new name should be, then possibly running that chown command just to make sure everything does indeed belong to you with the new correct username.

Confused? 
Yes I think I may be but I hope you can see what I'm attempting to get you to do though just getting a bit unsure where all those home files sit at the mmoment.

---

### Post by jerrywo on 2021-02-17
Ahhh, I've met the enemy....tis me.

I am tempted to simply do a re-install minding my spelling, etc.  I have some issues with a few hidden files,
mainly CQRLOG, a ham radio logging program...I think, when I tried to move my files over onto /home, I was blithely
merging and replacing.

At this early stage, the only application that's really important/essential is my mail program (Evolution) and I 
can back that up.

Because the /home folder on the computer has issues, I'd like to just do an rsync:  source = backup and destination = new home folder.

I'll probably have to do that while using the live CD.  That sound right?

Jerry

---

### Post by ajgreeny on 2021-02-18
Yes, go for a new installation; on the assumption you get the username right this time it should be a smooth ride.
You may still find an empty folder for jerrryw in /home which you can delete but check before you do so that there really are no files or folders in it that you do need.

Definitely a case of double checking for typos when installing; I have almost done the same in the past (fat fingers!) but noticed just in time to go back a step in the process.

---

### Post by CelticWarrior on 2021-02-18
An installation takes some 15-20 minutes, reason why I suggested it some 48 hours ago.

---

### Post by ajgreeny on 2021-02-18
> **CelticWarrior said:**
> An installation takes some 15-20 minutes, reason why I suggested it some 48 hours ago.
Whilst I would normally agree wholeheartedly with you, I tyhink in this case it should have been easy to do whatever transfer of personal files and folders was needed to get everything back to where it should have been had that typo not messed up everything.

It all depends, I suppose, on how many additional applications were essential to the OP that might take a long time to install and configure as wanted.

---

