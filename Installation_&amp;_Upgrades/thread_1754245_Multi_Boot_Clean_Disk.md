---
title: "Multi Boot Clean Disk"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by Isidorito on 2011-05-09
I have a new Hard Disk and i need to make a multi boot

The idea is:

a single home directory and clean installations of:

Ubuntu 11.04
OpenSuse
Fedora
BackTrack
Debian

The problem is:

Can anyone tell me what order its better to install?

Can I install systems of 32 and 64 bits (for example Ubuntu 64 Bits and BackTrack 32 Bits)?

What other operative system recommends?

The mission is simple: Help my family to use different Linux distros.

Thanks =)

---

### Post by lmarmisa on 2011-05-09
I recommend to use a virtualization solution. Maybe VirtualBox could help you:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Isidorito on 2011-05-09
I have virtual box, i want to start the pc in differents distros some times so, te PC will be working with the same files but differents distros, its like an experiment :P and the rat lab are my parents :P

---

### Post by oldfred on 2011-05-10
I do not think you want to have one /home unless you have different user ids for each install. Any settings that overlap between different systems will cause major problems. /home without any data is tiny and I would just leave /home in each install.

I only install Debian based (so far) and use a common /data as UID is always 1000, and I have a /shared NTFS for some data that I used to share with XP. But with different distributions you will have issues with UID & GID.

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by Isidorito on 2011-05-10
> **oldfred said:**
> I do not think you want to have one /home unless you have different user ids for each install. Any settings that overlap between different systems will cause major problems. /home without any data is tiny and I would just leave /home in each install.

I only install Debian based (so far) and use a common /data as UID is always 1000, and I have a /shared NTFS for some data that I used to share with XP. But with different distributions you will have issues with UID & GID.

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)


thanks, i was looking the threads and im thinking in this options:

I think i will take the second one =)

> **Morbius1 said:**
> I'm fairly certain the uid and gid in fstab are only used for Windows filesystem not linux filesystems.

If you want an old school method the general procedure is something like this - it's been a very long time since I've done this but:
(1) Create a new group - sharedata with a group id that is the same for every OS you have making sure it doesn't conflict with an existing gid.
(2) Make the default umask for each user on each OS = 002
(3) Change the group of the shared directory to sharedata
(4) Change permissions of the shared directory to allow all members of the sharedata group to have access and so that all new files / directories will inherit the sharedata group:
```
sudo chmod 2775 /media/Data
```Or you can use bindfs: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

The implementation of bindfs may be different for each OS but it will make every user on every OS think he owns the partition and it's contents. Essentially making a Linux partition appear to be an NTFS partition.


> **Morbius1 said:**
> Since you have 12 OS's and apparently like to tinker I would suggest the following alternative that you might want to try out.

I have a common linux data partition /DATA and use the following two lines in the fstab of every linux OS installed on my system:
```
 LABEL=Data /DATA           ext3    defaults,noatime        0       2
 bindfs#/DATA /home/Shared fuse perms=0666:+X 0 0
```/home/Shared will "bind" to /DATA with all it's content except:

All existing and new files added in /home/Shared will have permissions set to 666 - universal read / write.
All existing and new directories in /home/Shared will have permissions set to 777 so they can be opened.

Conceptually it's exactly the same thing you're trying to achieve with the fstab mount, symbolic link, and chmod.

BINDFS HowTo: [http://ubuntuforums.org/showtion /DATA and use the following two lines in the fstab of everhread.php?t=1460472](http://ubuntuforums.org/showtion /DATA and use the following two lines in the fstab of everhread.php?t=1460472)

Just an idea.

Some questions about the second option:

1- The 777 perm... is not to dangerous?
2- The DATA partition must have operative sistem? or just the space whit ext3 format?
3- The I will need to re direct the links of "music", video"... to the data folders doesn't it?

So much thanks for the links and im sorry for my english, im argentinian :P

---

### Post by oldfred on 2011-05-11
If you are the only user having 777 permission should not be an issue for your data partitions. 

You do not need to have an operating system in the data partition, just format as ext3 or ext4. But I do like to have an operating system on every hard drive, just in case.

I just mount both my data (ext3) and shared (NTFS) partitions with fstab and use links to link folders from those partitions into my /home. My /home is tiny (and now back in / as I move all data ). I move even data like Firebird & Thunderbird profiles & some others that often are . files that are normally hidden.

More details on the way I do it with linking. see post #4
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

