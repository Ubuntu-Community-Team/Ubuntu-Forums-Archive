---
title: "dual boot archbang and ubuntu?"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by F.G. on 2011-09-25
hi folkes,
I've got a asus netbook with archbang installed on it. I want to install ubuntu and have them dual booting.  the only thing is that the partitioner doesn't recognise archbang as being an OS.
I can manually specify the partitions, so as not to overwrite the archbox filesystem. if i do this, oddly, Archbang does show up in the grub menu, it will only boot to a console (and startx doesn't work)and will have lost the Home folder (to do with resizing the partition with the home folder in it).

anyhow, i havn't exhaustively google around for answers (which i will be doing), but if anyone has any good tips to get this set up, or wher to look i'd be very grateful.

thanks for all/any replies.

---

### Post by F.G. on 2011-09-26
bump.

---

### Post by F.G. on 2011-09-29
hi everyone,
having figured it i though i'd put down the way i got them running. it's all pretty simple really:

1) install Ubuntu, manually managing partitions, all you really need to do is make sure you leave enough contiguous space outside of your root or home partitions to install archbang (this would probably work with most other distros).
I used a primary swap partition, and an extended partition with '/' and '/home' partitions in it for Ubuntu, with another chunk of unused space (for the other os).

2) Install Archbang, choosing the empty partition to install it into, choose the same swap as the swap used by Ubuntu. And DO NOT install a bootloader.

3) boot into Ubuntu and run:
```
sudo update-grub
```
this should update your grub configuration to include Archbang. 

Now you should be able to boot into Arch or Debian as you like.

Now i'm just trying to figure out if I can use the same 'home' (ie shared) for an Ubuntu user and a Archbang user. feels a bit like the diamond problem.

---

### Post by oldfred on 2011-09-29
I would not suggest to share /home. Setting and software versions may not be the same and get confused.

But you can share data. Do not know what UID & GID Archbang uses. All Debian use 1000 for UID so you can easily share a data partiiton without user issues. NTFS may be a choice but you have to have a Windows repair CD to run chkdsk periodically.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

