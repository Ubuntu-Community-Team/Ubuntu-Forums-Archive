---
title: "FAT &amp; NTFS Question"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by reb68 on 2007-03-08
Got a good ISO file and booted to install. When I got to Partitions I had
/media/hda1 39G   ect3 -------Partition 1
/media/hdb1 10G          --------Hard drive with windows
swap             1G   ect3--------- Partition 2
/                 38G------------------ Partition 3   of 80G Drive
__------------------
I changed /media/hda1 to /home
I plan on formatting swap and / (partition 2 and 3)

hdb1 is a 10G drive with windows on it.
I get the error
"FAT and NTFS cannot be on a drive with(/./boot,/root,/home,/usr,/var etc) should be with /media/"
Not verbatum
I need to preserve the hda1 as /home as that is what it is called in Dapper and all my Data is on it.How can I set these partitions?

---

### Post by Kateikyoushi on 2007-03-08
Sounds to me your / was set to fat or ntfs, try as ext3 and tick reformat as well.

---

### Post by huygens on 2007-03-08
Seems all a bit confuse to me what you are trying to say. So perhaps, you could try to describe in a different manner so I could better help.

Tu resume what I understood from you:
You have a swap and / partition that you want to format and install a new release of Ubuntu on it.
You have another partition (/dev/hda1) which is your home directory under Dapper and you want it to be as is for the new installation. You have another one on a different disk (/dev/hdb1) where Windows is installed (either FAT or NTFS).

So you should tell that /dev/hdb1 is mounted as /media/hdb1 (or /media/windows as you wish) and you should be careful not to choose to format it.
For /dev/hda1, you should set /home as the mount point and you should be careful not to choose to format it.
All should then be fine, assuming of course that the premise I have written are correct.

Perhaps a good way to make us understand better the problem would be a few screenshots of the various partitions and of the error (of course this apply only if you are using the graphical interface of the installer)

---

