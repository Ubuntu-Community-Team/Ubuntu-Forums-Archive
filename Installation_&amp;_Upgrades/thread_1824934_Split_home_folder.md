---
title: "Split /home folder"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by 8301 on 2011-08-14
Hello

I wonder if there is a way to split up the /home folder content to two partitions during the installation. I want the Home folder only contains my Music, movie and download content. The other partition shall only include the Ubuntu settings and program settings example /home/.xbmc.

Br Sebastian

---

### Post by Furball588 on 2011-08-14
You could just setup the mount point during the installation.

I'm not sure if there's any advantage to do this though.  Seems easier to me to just edit the fstab or create a symlink afer everything is done.

---

### Post by 8301 on 2011-08-14
> **Furball588 said:**
> You could just setup the mount point during the installation.

I'm not sure if there's any advantage to do this though.  Seems easier to me to just edit the fstab or create a symlink afer everything is done.

The only experiences that I have with installation mount point is:
Root /
Home /home
Swap swap

Which mounting points can I use for my desires?

Also how can I use fstab to direct all default shortcuts in ubuntu to "my" home folder? Create symlinks to the system seems to create to much work for my initially task. The thing is that sometimes I want to do a clean install without to have to move all my files (250 Gig) from /home to another drive.

Br sebastian

---

### Post by Furball588 on 2011-08-14
> **8301 said:**
> Which mounting points can I use for my desires?

You can use /home/8301/music for all the partitioning tool cares...

> **8301 said:**
> Also how can I use fstab to direct all default shortcuts in ubuntu to "my" home folder? Create symlinks to the system seems to create to much work for my initially task. The thing is that sometimes I want to do a clean install without to have to move all my files (250 Gig) from /home to another drive.

All you're doing here is automating mounting the partition to a folder in your home folder.

I guess to be clear...to directly answer your question, the answer is no.  However, there's nothing that prevents you from mounting a device somewhere in your home folder.

---

### Post by Hakunka-Matata on 2011-08-14
> **8301 said:**
> The only experiences that I have with installation mount point is:
Root /
Home /home
Swap swap

Which mounting points can I use for my desires?

Also how can I use fstab to direct all default shortcuts in ubuntu to "my" home folder? Create symlinks to the system seems to create to much work for my initially task. **The thing is that sometimes I want to do a clean install without to have to move all my files (250 Gig) from /home to another drive.**

Br sebastian
You can do a 'clean install' to your / (root) partition and it will not affect your /home partition.  The reason to make a separate /home partition **is** so that you can 'clean install', or reinstall a system and keep your /home partition untouched.

---

### Post by Morbius1 on 2011-08-14
There are pros and cons to creating a separate home partition.

The pro argument is that is saves time when you do a new install or have to reinstall because all your config files as well as all your data is already saved.

That is exactly the con arguemnt as well however as you really aren't doing a "fresh" install since you are bringing in all the old config files with it.

What I do is not have a separate /home partition but a separate /data partition which I have mount automatically in fstab every boot and then "bind" subdirectories from the /data partition to my /home [COLOR=Blue]directory[/COLOR]. For example I have a /data/Music directory that holds all my music. I can manually bind that to my Music folder in my home directory by issuing the following command:
```
 sudo mount --bind /mnt/data/Music /home/morbius/Music
```That bind does not survive a reboot however but there are multiple ways to have this done at every boot:

* add the bind command without the sudo to rc.local
* you could add to fstab with a slightly different syntax but it doesn't work very well there - at least not in ubuntu.
* or you can create your own Upstart job: [http://ubuntuforums.org/showpost.php?p=10899012&postcount=41](http://ubuntuforums.org/showpost.php?p=10899012&postcount=41)

To be clear what this will do is functionally separate your config files from your data. When you do an new install you will lose all your config / hidden files  and directories ( i.e. firefox / thunderbird - so make sure you do a backup ) but all your data remains. All you would have to do is recreate the upstart job. I tend to go from LTS to LTS releases anyway so setting up new configurations is not a big deal and would probably have to be done anyway ( Gnome3 vs Gnome2 for example ).

---

### Post by Hakunka-Matata on 2011-08-14
@Morbius1:  Thanks for the clarification - well explained and easy to see the advantages.

---

### Post by Whyzer on 2011-08-14
Editing fstab using a bind command is the way to go. I have 4 hard drives on my Ubuntu machine, one 40Gb which contains my Ubuntu OS, and then 3 other 1Tb drives that contain a bunch of other things. 
 I mount the drives in fstab using their UUID and then I created folders in my /media directory with various names like mp3s, movies and so on. The just add bind commands to put them into those respective folders.
One thing to remember, you must create the new folders used in the bind command, it doesn't create them automatically. If you don't it wont have anything to bind to. 
Write your bind commands and save, in a terminal window do a " mount -a " (no quotes), if no error messages come up your all set.

One huge advantage to this is if your Ubuntu ever goes down your data is on a separate drive than Ubuntu. I have had the 3 drives since Ubuntu 9.10 and now I am at Ubuntu 11.04. I do fresh installs every upgrade and the extra drives let me back up all my modified Ubuntu files for easy restoration.

---

### Post by Morbius1 on 2011-08-14
Having binds in fstab is the way I used to do it ( and btw is the classic method ) and still do for some distros but I have run into problems doing it in Ubuntu. There's a bug report somewhere that details that under certain conditions the system attempts to do the bind before the the main partition is mounted and the bind fails even though the bind line is after the main line in fstab. 

It could very well be that after having it happen to me and finding a workaround with Upstart that I haven't kept up with the bug and it's no longer an issue.

If your're interested the syntax in fstab corresponding to the upstart bind would look something like this:
```
/mnt/data/Music /home/morbius/Music auto bind 0 0
```

---

### Post by Furball588 on 2011-08-14
> **Morbius1 said:**
> :sudo mount --bind /mnt/data/Music /home/morbius/Music

That bind does not survive a reboot however but there are multiple ways to have this done at every boot:

Just to clarify my mind, what's the point of --bind flag here?  I guess the way  to read this, he's just mounting a regular device...

---

### Post by Morbius1 on 2011-08-14
Bind is used to mount part of an already mounted directory somewhere else.

Somewhere in fstab there is a line that is mounting the parent partition like:
```
UUID=whatever /mnt/data ext4 defaults 0 0
```

So the mount --bind is mounting a subdirectory of that partition to another location binding one to the other so that anything done to one ( chmod / chown for example) happens to the other.

---

### Post by oldfred on 2011-08-14
Morbius1 knows mounting & fstab and I often link to his posts as an alternative to my way which is to mount a partition once and link the folders into /home. He also points out the issues of differnt UID/GID if using differnet distributions. 

I also move all hidden folders that contain any amount of data into one of my data partitions. The only thing I have not moved is .wine as I understand that is not so straightforward.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

