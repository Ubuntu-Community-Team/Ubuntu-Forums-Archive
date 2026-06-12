---
title: "Creating separate /home partition after the fact? Need help."
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by StevieCretin on 2013-03-11
I've read that it's a good idea to put one's /home directory (folder) in a separate partition because if you re-install the OS from scratch (or switch to a different but compatible distro, say Ubuntu to Mint) you will not have to reinstall all your user files from backup.
I know how to create partitions, and could just copy the files over from the existing /home, but how does one then get the OS to use the /home folder in the new partition? Is there some kind of pointer that needs to be changed?
I'm currently using Ubuntu 10.04 (Lucid)
THANKS!
--Steve

PS-Could multi-boot systems share that same /home partition folder?

---

### Post by schragge on 2013-03-11
Basically, what is said at [uhelp]community/MountingWindowsPartitions[/uhelp] about manual configuration through */etc/fstab* also applies here with the obvious change that your mount point should be */home* in this case.

> **StevieCretin said:**
> PS-Could multi-boot systems share that same /home partition folder?While it certainly possible I wouldn't recommend it, especially, if you're multi-booting different Linux distributions like Fedora and Ubuntu because some settings could conflict with each other. Better create an extra partition where you could share data for several distributions. You can symlink the whole, or only certain subfolders of it from respective /home directories if you want. E.g. on my system (Dual-boot Debian/CentOS) [XDG user directories]("https://wiki.archlinux.org/index.php/Xdg_user_directories") in respective Debian and CentOS home folders are actually symlinks into separate partition mounted under */.share*:
```

[COLOR=green]$[/COLOR] ls -l|grep -e '->'
[COLOR=green]lrwxrwxrwx. 1 sero sero       16 Aug 30  2012 bin -> /.share/sero/bin
lrwxrwxrwx. 1 sero sero       16 Sep 19 15:49 cfg -> /.share/sero/cfg
lrwxrwxrwx. 1 sero sero       22 Aug 31  2012 Documents -> /.share/sero/Documents
lrwxrwxrwx. 1 sero sero       22 Aug 31  2012 Downloads -> /.share/sero/Downloads
lrwxrwxrwx. 1 sero sero       17 Sep 19 15:41 mail -> /.share/sero/mail
lrwxrwxrwx. 1 sero sero       17 Sep 19 15:42 misc -> /.share/sero/misc
lrwxrwxrwx. 1 sero sero       18 Aug 30  2012 Music -> /.share/sero/Music
lrwxrwxrwx. 1 sero sero       21 Aug 30  2012 Pictures -> /.share/sero/Pictures
lrwxrwxrwx. 1 sero sero       19 Aug 30  2012 Public -> /.share/sero/Public
lrwxrwxrwx. 1 sero sero       16 Sep 20  2011 src -> /.share/sero/src
lrwxrwxrwx. 1 sero sero       22 Aug 30  2012 Templates -> /.share/sero/Templates
lrwxrwxrwx. 1 sero sero       19 Aug 30  2012 Videos -> /.share/sero/Videos[/COLOR]

```
Obviously, I also took care of my user in both system having the same UID/GID.

Instead of symlinking them, you can specify the actual location of XDG user directories in *~/.config/user-dirs.dirs*

---

### Post by oldfred on 2013-03-11
I also use the data partition with symlinking as I have multiple Ubuntus installed.

If you want to move /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

More info on separate data partition(s) - a bit more advanced than a separate /home but better if multiBooting.
      
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by StevieCretin on 2013-03-11
Wow, thanks for the quick replies!
 To clarify a bit, I'm not *that* worried about different distros sharing /home. I know there can be compatibility issues, but if both were Ubuntu-based (say Ubuntu and Mint- I love both and like to experiment) rather than just Debian based (wherein relation can be distant) I assume it would be less of an issue.  That all can come later if desired. 
  I'd really just like to make the /home partition independent for now, even if I stick with Ubuntu 100%, and just need to know the process for partition-izing /home without blowing anything up. Of course, I'd experiment on my netbook before trying it on my work computer.
THANKS UBUNTU COMMUNITY!
--Steve
PS- I have no need to mount NTFS partitions as I gave up Windows like a bad habit 8 years ago when my older hardware (P4) was taking 20 min to boot XP SP3 and [ironically] crashed  while downloading my first Linux (Ubuntu) and in the process marked the HDD as "in use" making it inaccessible until I did a bit of hacking.
  This led me to save the following quote from the web:
"Rumour has it that if you play Microsoft CDs backwards you will hear Satanic messages.
Worse yet, is that if you play them forwards they will install Windows."

---

