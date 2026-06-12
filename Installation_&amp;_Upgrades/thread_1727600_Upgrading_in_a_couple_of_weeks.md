---
title: "Upgrading in a couple of weeks"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by benargo on 2011-04-12
Hi guys,

I know this has probably been asked before, if not multiple times, but I wanted a new topic to make it easier for me to follow.

I've currently got an old desktop of mine running as a NAS and a Minecraft server. Currently running Ubuntu 10.04, as it has done for almost a year (since 10.04 came out in fact). I'm very excited to see the release of Ubuntu 11.04 in a couple of weeks time, and I'm very tempted to upgrade but I do not want to lose any of the important data on the NAS, namely:

- My and my family's documents in the /home/[username] directory
- Our family's shared documents in /home/shared
- Our Minecraft server in /var/minecraft

All directories excluding /home are mounted to a single partition on a 500 GB hard disk, whilst the /home directory is mounted to a 2 TB hard disk.

Assuming the minecraft documents will be moved from /var/minecraft to /home/minecraft for the update process, how would I go about performing the update whilst ensuring that the /home partition is not touched at all.

Your assistance on this matter would be much appreciated.
Kind Regards,
Ben Argo

[http://twitter.com/ben_argo](http://twitter.com/ben_argo)

---

### Post by rewyllys on 2011-04-12
> **benargo said:**
> . . . . All directories excluding /home are mounted to a single partition on a 500 GB hard disk, whilst the /home directory is mounted to a 2 TB hard disk.

Assuming the minecraft documents will be moved from /var/minecraft to /home/minecraft for the update process, how would I go about performing the update whilst ensuring that the /home partition is not touched at all.

Your assistance on this matter would be much appreciated.
Kind Regards,
Ben Argo

[http://twitter.com/ben_argo](http://twitter.com/ben_argo)
Since your root, "/", and home, "/home", directories are mounted on separate partitions, all you need to do is to be CAREFUL, during the installation process, that 
(1) you choose manual selection of mount points, 
(2) you choose your present "/home" partition as the partition on which to mount the "/home" partition in the new installation, and 
(3) you DO NOT format your "/home" partition.

---

### Post by benargo on 2011-04-12
I Assumed as much, thanks for the confirmation rewyllys! Have a brownie! [http://cl.ly/5wuY](http://cl.ly/5wuY)

---

### Post by oldfred on 2011-04-12
If you have lots of room you can just create a new 20GB / (root) partition and have your old install to fall back to if need be.

If you have installed a lot of programs, you may want to make a list to reinstall them automatically. You may want to edit list to remove old kernels and OpenOffice as LibreOffice will be in the new version & you may not want both.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

---

### Post by rewyllys on 2011-05-08
> **benargo said:**
> I Assumed as much, thanks for the confirmation rewyllys! Have a brownie! [http://cl.ly/5wuY](http://cl.ly/5wuY)
Great photograph!  Makes me hungry just to look at it.:D

---

