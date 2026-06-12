---
title: "Ubuntu 17.10: different behaviour of binds in fstab"
date: 2017-11-16
forum: Installation &amp; Upgrades
---

### Post by emilio-parente on 2017-11-16
Since the beginning with Ubuntu (Hoary Hedgehog) I tried to find a solution for make easy to me installations of new releases, even with fresh installs. Finally the architecture of my installations is:
[LIST]
[*]System "/" partition and /home partition are on an SSD (sda). 
[*]The home partition is quite small and contains empty folders with the names of the default ones (Documents, Images; Music...). 
[*]Actual data are on a second disk (sdb1 partition) that contains the same folders names. 
[*]Only the Desktop folder stays in the /home/user directory with all its data. 
[*]As soon as the new installation is made, I create in the /media folder the mount point of the second disk ("Data") 
[/LIST]
Then I update the /etc/fstab with the following:

```

[FONT=verdana][SIZE=2]...
...
#
# /media/Data was on /dev/sdb1 during installation
UUID=xxxxa901-xxxx-46b2  /media/Data                  ext4    defaults   0   2
#
/media/Data/Dowloads         /home/user/Downloads   none    bind
/media/Data/Templates        /home/user/Templates    none    bind
/media/Data/Public              /home/user/Public          none    bind
/media/Data/Documents       /home/user/Documents   none    bind
/media/Data/Music              /home/user/Music           none    bind
/media/Data/Pictures           /home/user/Pictures       none    bind
/media/Data/Videos             /home/user/Videos         none    bind
...
...[/SIZE][/FONT]

```

Until ubuntu version **17.04** everything worked as a charm. Partitions mounted with UUID in fstab were seen as devices (disks) and shown on the desktop. Opening Home I could see the normal default icons and access my actual data through the binded folders. Everything transparent to the user.

With **17.10** I can see a different behaviour: each binded folder in fstab is seen on the desktop as if it was a **mounted device**. At first each of them is displayed with its own name (I mean Documents, Music, under the device icon), but after few minutes, **all** the binded folders are renamed with the partition name on wich they stay: e.g. "Data". In addition, opening Home, all the default icons have a disc symbol on the lower right corner. 
This happens with a fresh install, using both ubuntu and Xorg sessions.  

Has somebody experienced something like this? What could be the source of this different behaviour between 17.04 and 17.10? Nautilus? Bind? Mount? ... Is there a solution to fix or bypass this problem?

---

### Post by mook765 on 2017-11-17
First off all, is this
```

[FONT=verdana][SIZE=2]/media/Data/Dowloads [/SIZE][/FONT]
```
a typo in your fstab-file?

Anyway, I have a similar setup for my home-folder which means the standard folders like Documents, Videos, Templates and so on are stored on an extra partition which is mounted on /media/Data. But I never used bind-mounts, I deleted the original folders in /home/user and replaced them with links to the folders in the Data-partition.
Example:
```
ln -s /media/Data/Documents ~
```
This way the link has the same name as the original folder, this is important.
For you that would mean to remove (or comment out) the bind-mounts from your fstab, reboot, then delete the mentioned folders from /home/user (after checking if they are really empty,of coarse) and then create the links to the folders in your Data-partition.

Another way around instead of using links is to edit a single configuration file.
Take a look at the file /home/user/.config/user-dirs.dirs
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```
For example, replacing "$HOME/Desktop" with "/media/Data/Desktop" in this file will use the folder /media/Data/Desktop instead of /home/user/Desktop after the next login. But before you log out and back in just right now,  remove (or comment out) the bind-mounts in fstab , then reboot.

I'd recommend to edit the configuration file /home/user/.config/user-dirs.dirs at least for the use of the standard xdg-folders, this is the clean, official way. For additional folders you may use links.

---

### Post by ChM on 2017-12-21
Using logical links is not nice because we have this link arrow displayed on the bottom right of the folder.
Changing the .config/user-dirs.dirs adds directories with that name in the file browser. The directories with icons disappear from the home directory. 

There is also the risk that we create dirs in the home directory which is on the SSD*(for instance) and we forget to move them on the persistent partition. So when we erase the SSD partition for a fresh system install we erase those directories. 

It seam that the other way round is safer. Put the /home directory on the persistent partition and disk and move .config and .cache on the SSD and redirect to them with a logical links (ln -s). Access to their content will be fast and may be erased with a fresh install of a new OS*install.  The redirect of home cane be done by changing the home dir path in the password file.

---

### Post by quonsar on 2018-01-19
This has been frying my brain, and nobody seems to answer the question "why did the behavior change?" and "how do I get it back?"
I do not wish to use symbolic links. I have good reasons. I use tried and true backup practices to ensure all of my root filesystem and personal data stored on other file systems are preserved and when restoring everything goes back where it was, including any symbolic links which are treated as just another file and are not followed during the backup process. This has worked very well for me ever since 2005. All down the tubes I guess. While monkeying around with this I have somehow managed to bork bind mounts completely. Like you, (except I have been using /mnt instead of /media) I mount these non-root volumes in fstab:  
```
UUID="9bb6e978-1da2-4093-9c17-8696169ddfd8" /mnt/Media ext4 noatime,errors=remount-ro 0 3
/mnt/Media/Movies  /home/quonsar/Movies none bind
```
The behavior now is during the boot process, ***new directories are created*** at /mnt/home/quonsar/Movies and mounts there!!!! Caja crashes repeatedly after this boot. 
Things only return to "normal" when I unmount this new folder which I did not create and did not call out in fstab, delete it, then comment out the bind mounts and reboot.

So, something is seriously borked at a low level and I can't imagine why this happens. Somewhere in all the various reboots, fstab edits, etc I've gotten something royally screwed :lolflag: I hope it's not the volume itself... Starting from scratch again.

Just venting, thanks for reading. :rolleyes::rolleyes::rolleyes:

---

### Post by Ascurion on 2018-01-24
Hello together, I have a very similar setup for similar reasons to the one described in the first post. I just noticed the same different (annoying) behavior of bind mounts in 17.10. I would also be interested in an explanation on what has changed and why :)...

---

### Post by jim4652000 on 2018-02-01
I have joined the forum to ask about this too - I have similar setup as above; the usual documents/pictures/downloads etc but also a few additional folders like my ebook library all on a separate drive.  I just upgraded today but am tempted to go back!

---

### Post by emilio-parente on 2018-02-06
No answers so far to my initial question: The cause of this behaviour. I'm now convinced (but no data to support this) that the proble could reside in GNOME3 or NAUTILUS that, to me, are getting worst in usability at each "improvement" release.
For the moment I was forced to adopt the "soft-link" solution. Not the maximum of elegance, but at least it works. Will keep tracking if something will change in the future.

p.s.  with the past version of Nautilus a right click on any folder allowed to create a soft link to it. Now this option has disappeared, forcing to use the terminal session. No problem to me, but this is very unconfortable.

---

### Post by Morbius1 on 2018-02-06
Looks like a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=782814](https://bugzilla.gnome.org/show_bug.cgi?id=782814)

---

### Post by emilio-parente on 2018-10-24
Problem finally fixwd in Ubuntu 18.10 cosmic, by putting for **binds in fstab** the following:

[B][COLOR=#000000]....        ....        none      bind,x-gvfs-hide          0      0[/COLOR]
[/B]
Thank you all.

---

### Post by quonsar on 2018-10-31
Will this fix be backported to 18.04? I have no intention of moving off this LTS for another nightmare in UbuntuLand!

---

