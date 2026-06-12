---
title: "Shared Partition"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by Hogosha on 2010-04-07
Will this work?

I have a new laptop that should be here this afternoon and i would like to share the home partition with a windows install. Here is my plan.

[LIST=1]
[*]Leave the default install of windows on there but shrink the partition it is on.
[*]Install ubuntu on the new partition along with a home partition
[*]copy the folders of the home partition and then format the partition into ntfs
[*]edit the FSTAB and put the folders back into that partition
[*]Boot back into windows and change the "My Documents" folders the those in the home partition
[/LIST]

What do you think?

---

### Post by Slim Odds on 2010-04-07
> **Hogosha said:**
> Will this work?

I have a new laptop that should be here this afternoon and i would like to share the home partition with a windows install. Here is my plan.

[LIST=1]
[*]Leave the default install of windows on there but shrink the partition it is on.
[*]Install ubuntu on the new partition along with a home partition
[*]copy the folders of the home partition and then format the partition into ntfs
[*]edit the FSTAB and put the folders back into that partition
[*]Boot back into windows and change the "My Documents" folders the those in the home partition
[/LIST]

What do you think?

I think that you're asking for trouble.

Windows and Ubuntu can easily share an NTFS partition, but /home is not a good one for that.

You could create a separate partition for "My Documents", etc. that is not part of /home.

---

### Post by ottosykora on 2010-04-07
could work, but I would take some fat32 or so for the shared partition and in addition, not call it partition /home but rather just alocate some folder in it where home will be in. So by that windows will not try to write into home and vice versa.

But anyway, seems asking for troubles.

---

### Post by ajgreeny on 2010-04-07
Sorry, but it will definitely _not_ work with everything from ubuntu's home on an ntfs partition, I'm afraid.  However, as others have suggested, you can easily keep /home within the root partition of ubuntu, but make sure all your docs, music, videos, photos, etc etc are saved into the shared ntfs partition by the programs you use in ubuntu.

A lot of the hidden files and folders that are produced and automatically placed into /home by ubuntu programs when first run, will simply refuse to work when/if saved to a fat32 or ntfs partition, as they need their specific linux permissions, which those file systems do not support.

If you need to share configurations for firefox and thunderbird between the two file systems, that is possible, and you can find details of how to do that on mozilla's website, or by searching this forum, I think.

---

### Post by oldfred on 2010-04-07
As ajgreeny says you can share data but not the settings in /home so /home has to be a linux file system. Data only needs read & write so no special permissions or ownership is required. You set those settings when you mount the NTFS shared partition.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

I directly mount my shared partition into /home but you can also link in folders. I also have shared firefox and thunderbird profiles in the shared partition for three years, but have not tried to convert to the new thunderbird yet.

---

### Post by duke.tim on 2010-04-08
Like many have said before leave the home partition on a Linux filesystem. Moving the /home directory to NTFS would be like moving Program Files (from windows) to an ext3/4 partition. instead It would be better to change the location of the directories within /home and windows to be on another partition. To change the location of your Desktop, or Documents folder and such navigate to```
cd /home/duke/.config/user-dirs.dirs
sudo gedit ./user-dirs.dirs
```
you should see something like this XDG_"directory"_DIR=
where I placed "directory" there will be the names of folders that are normally linked to home. place after the equals sign the location where you want that directory to point to. example: (if you wanted to change Documents to a partition called NTFS```
XDG_DOCUMENTS_DIR="/media/NTFS/Documents"
```

---

