---
title: "how can I split a dual boot system into two physical systems?"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2011-02-25
I have a HDD with a fairly old XP - Ubuntu (10.10) dual boot with Grub (legacy) as boot manager.  I would like to split the two OS to run XP virtually in Win 7, and have Ubuntu on a separate HDD to boot into.  Is there a way to create bootable partitions on a different HDD and move my existing system there?

---

### Post by oldfred on 2011-02-26
I do not know about win7, but I thought it had an XP compatible mode. Install win7 on one drive and Ubuntu on the other. With Ubuntu/grub just be sure to install grub to the Ubuntu drive. The current version only gives that option if you use manual install. I prefer partitioning with gparted in advance. Then use manual install to select previously created partitions and choose to install grub to that drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by merlin666 on 2011-02-26
Thanks. What I meant to do was to move an existing configured Ubuntu from a dual boot to a single boot drive. I was wondering if this was as easy as creating the partitions and copying the directories from one drive to the other, and somehow create a way to boot into the copied system.

---

### Post by oldfred on 2011-02-26
Many post here discuss copying their system from one drive to another. I am more of a clean install as it is quick & easy & works. When going from old drive you can just copy /home over to your new /home partition. Make a list of installed apps and reinstall. I now  have it down to about an hour total, but have done it many times as I reinstall each new release as beta,RC & final or several time just to experiment. 

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)

aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

### Post by Hedgehog1 on 2011-02-26
+1 on a clean install of Ubuntu on the new drive and copy your data from the /home directory.

The your current drive can be used by your new Win 7, with XP as the guest OS in either Win7 OR Ubuntu using Virtual Box or VMware player.

---

### Post by merlin666 on 2011-05-05
I don't really want to consider a "clean" ubutu install as the current installation has been very customized over 6 years or so of use. If I copied the various partitions to a non-bootable drive, what would I have to do to make this bootable?

---

### Post by oldfred on 2011-05-05
All you user customizations are in /home. If you manually configured something system wide, that will be in /etc. 

You can copy your system over. Depending on how you do it the UUIDs may be identical & you just have to reinstall grub/grub2. Or if new partitions and UUIDs are different you have to reinstall grub and edit fstab.

The full system clonezilla or remastersys may be the best way.

---

