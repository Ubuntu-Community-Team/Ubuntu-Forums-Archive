---
title: "mount NTFS (hda2) at boot"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by baza41 on 2005-03-09
I'm wanting to mount windows (had2) during boot. What worked on Warty does not seem to work on Hoary. Advice?

Baza

---

### Post by bored2k on 2005-03-09
[QUOTE=baza41]I'm wanting to mount windows (had2) during boot. What worked on Warty does not seem to work on Hoary. Advice?

Baza[/QUOTE]
 [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by KLineD on 2005-03-09
Just add the following to the /etc/fstab file
```
sudo vi /etc/fstab
``` 
substitute 'vi' for whatever editor you want, just remember you need to do sudo in order to edit the file
and add the line
```
/dev/hda2       /mnt/windows    ntfs    umask=0222      0       0

``` 

Just make sure that the folder (in this case /mnt/windows/) exists and where it says ntfs change it to vfat IF the partition is fat32 or leave it as it is for ntfs

---

