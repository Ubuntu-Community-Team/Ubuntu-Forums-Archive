---
title: "Removing Old OS's from a multi-boot computer."
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by 12quality on 2005-08-02
I currrently have four partitions on two seperate drives:
[list=1]
[*]an NTFS and containing my WinXP installation
[*] a Warty installation (not sure the fs)
[*]a fat32 that houses all of my data
[*]and an ext3 with Hoary, which is what I use
[/list]

I haven't touched Warty since I got Hoary, and I have gone months without booting into Windows, and would like to remove them (especially Windows!).

I was thinking about just removing their entries in menu.list.  This doesn't really do anything other than remove those options from grub.  I'd like to be able to use some of that space and move stuff around.

So, how do I?

[list=1]
[*]Delete the old partitions
[*]not screw up my MBR
[*]not mess up my swap
[*]convert the fat32 (needed so I could read/write from windows and Ubuntu) to a more linux-native format
[*]move partitions around from one drive to another
[/list]

---

### Post by kosmic on 2005-08-02
If you want to do that in GUI mode then install Parted, and erase the partition where Warty and Windows is, and format them to ReiserFs or ext2, ext3 and then give mount point to the new partition made, and there you go, only Hoary running in your box :)

---

### Post by Juergen on 2005-08-02
1) for creating and deleting partitions start 'sudo cfdisk', it's a little more userfriendly than the 'old' fdisk.

2) don't choose the option 'screw up MBR' ;-)

3) look into /etc/fstab which partition your swap is on currently. You can delete the others, if there are more.

4) I don't know a way to change the fs without destroying the data.
So do a backup, and copy your files back after creating the new fs.
Look at the permissions, since fat doesn't support them.

You create a new fs with mkfs (for all but reiser) or mkreiserfs - look at the man-pages.

5) You want to move your system to another partition?
You can use a simple 'cp -a' for this.
Since there are some demons running that might block access to some files, I'd at least boot into single-user ('recovery mode' in the grub menu).
Even better: boot the live-CD and mount source and target partitions.

After copying you have to adjust the devices in /etc/fstab of your new system-partition.
And create a new entry in your /boot/grub/menu.lst (best before copying so the changes are in the copy).

Then try to boot your new system.
If that succeeds, I think you have to run 'sudo grub-install /dev/yournewdevice' before you can delete the old partition.
For future reconfigs you might want to move /boot into it's own small partition, then there wouldn't be the need for grub-install...

---

### Post by 12quality on 2005-08-02
Thanks for the advice.  I understood it all except:

[QUOTE=kosmic]give mount point to the new partition made[/QUOTE]

What does this mean?

---

### Post by kosmic on 2005-08-02
[QUOTE=12quality]Thanks for the advice.  I understood it all except:



What does this mean?[/QUOTE]


ok
after you format the partitions, you want to acess that partitions right ?

then you need to mount them so ubuntu can see and use them, for example do :

sudo mkdir /media/WindosDisc
sudo mkdir /media/WartyDisc

them edit fstab, (sudo /etc/fstab)
and add them to that file, some like this

/dev/hda11 (you have to do -> sudo fdisk -l ) to see the partition number of your old windows and warty instalations )

/dev/hda11  /media/WindowsDisc  reiserfs defaults     0  2
/dev/hda12 /media/WartyDisc        reiserfs defaults     0  2

In this example I assume that the partitions are hda11 and hda12 and you had formated them with Reiserfs

---

