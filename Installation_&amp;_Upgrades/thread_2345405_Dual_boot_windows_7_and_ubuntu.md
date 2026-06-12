---
title: "Dual boot: windows 7 and ubuntu"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by lin-newbie on 2016-12-03
Hello all,

I'm considering dual boot for windows 7 and ubuntu (the last version LTS). However, some people warned me that this could damage the windows, and I don't wish for that to happen. Is there a scpecific way to do the dual boot safely? I watched some YouTube videos, but still I'm not sure if that will work 100%.

Thanks

---

### Post by oldfred on 2016-12-03
Who says it may damage Windows?

Users can damage Windows just using Windows. And it is often better to have a separate NTFS data partition, even if just using Windows.
The Linux NTFS driver mounts the NTFS partition with no hidden files & full access. I used to immediately change my XP to be that and often broke it on my own, long before dual booting.

With a separate NTFS data partition you can mount that read write and then have the NTFS Windows partition either hidden or mount read only.

Also most Windows 7 systems are MBR(msdos) partitioned with a 4 primary partition limit.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Dennis N on 2016-12-03
Probably thousands of users have safely done this. There are many guides. One is in the Community Help Wiki:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

