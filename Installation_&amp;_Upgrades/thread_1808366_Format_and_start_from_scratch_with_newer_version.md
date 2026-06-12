---
title: "Format and start from scratch with newer version"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by kabeza on 2011-07-20
I have Ubuntu 10.10 installed
I have installed lots of programs, some hacks so this thing works behind proxy, lots of ppas, etc.

Which partition should I format so I can install Ubuntu 11.04 (or next Ubuntu 11.10) from scratch? I want to get rid of garbage, nvidia drivers, etc. but would not like to loose some programs

This is my gparted screen:

[IMG]http://i.imgur.com/pKW4D.jpg[/IMG]

---

### Post by ajgreeny on 2011-07-20
Why do you have the large ntfs partition when you obviously don't have windows on the disk; is it on another disk in your machine?  And why are there two silly little unallocated areas in front of and behind the ntfs partition?  They are too small to be of any use for anything.

Alsdo it is not necessary to have separate partitions for /usr, /var or /tmp, and if I were doing an installation, I would leave those partitions simply as folders in root, and then use the freed space for another distro.

However, without knowing exactly what your reasons are for having separate /usr etc partitions, it is difficult to know what to suggest.  If you use one of the partitions sda5, 6 or 7, you will loose use of ubuntu 10.10 unless you can somehow undo the separate partitions currently set up when you installed the distro, and I have no idea how to do that on a current installation.

Simplest would be to shrink the ntfs partition from the left hand edge by about 10 -15 GB and then stretch the extended partition to cover the free space, make a new partition in the free space, now in the extended partition, and install 11.04 into that.  By doing that you keep a degree more flexibility than you would creating a new primary partition.

Your choice!

---

### Post by kabeza on 2011-07-20
I used the large ntfs partition to store a backup, but forgot to delete it once moved backup to another pc.
The 2 unallocated areas finished as they are, I didn't notice that, I guess the partition program left those there...?

I read some blog posts (can't remember now exactly where) that it was better to have /usr /var /tmp and /home in separate partitions

And finally, if I reduce the ntfs partition, create a new 20gb one and install 11.04 there, I'll still keep the 10.10 install in the PC, right? Will 11.04 detect this and adjust grub to have multiboot ubuntus? what will happen with /var /tmp /home in the 11.04? Could be all of them in the new 20gb partition?

Thanks and sorry 4 my ignorance

---

### Post by oldfred on 2011-07-20
The extra system partitions are for servers or users with very special requirements.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I regularly install each new version of Ubuntu to a new 20-25GB / (root) partition with /home included in the same partition. But I keep all data on other partitions and link the folders from my /mnt/data back into /home.

Grub2's os-prober finds all your other installs. I have several older ones that I now rarely boot so I have turned off os-prober and just add the one's I want to 40_custom

You will want to export a list of installed programs and reinstall the current versions of the same programs. Some system settings may be in /etc, but do not restore the /etc as the new version may have different defaults. You may need to reedit but having old copy makes that easier. All your user settings are in /home, but are less than 1GB if you exclude all your data that is normally in /home.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I have a home system with very little critical data. So my backup plan is just a new install and restore data from backups. I have some data backed up to DVDs and some rsynced to another partition. You should not use NTFS for backups as you lose permissions & ownership.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

I modified the above script to include this:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by kabeza on 2011-07-21
wow @oldfred
that was a very informative post

thanks to all for the info and lessons!!

---

### Post by dino99 on 2011-07-21
standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

