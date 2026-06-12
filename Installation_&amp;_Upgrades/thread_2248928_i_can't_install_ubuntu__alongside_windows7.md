---
title: "i can't install ubuntu  alongside windows7"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by slowmed on 2014-10-18
actually the problem is that  when i choose the option "install alongside windows 7" i don't get the option continue instead i get the option restart , when i choose it the  pc restarts and i keep looping(i choose the same options and i get the same results) , please help

---

### Post by prshah on 2014-10-18
> **slowmed said:**
> actually the problem is that  when i choose the option "install alongside windows 7" i don't get the option continue instead i get the option restart , when i choose it the  pc restarts and i keep looping(i choose the same options and i get the same results) , please help

Please change your boot order in the BIOS to boot off the CD, instead of your hard disk.

The exact method to change this depends on your hardware, but typically, you need to press DEL or F1 or F12 BEFORE the Windows startup (splash) screen appears.

Once the BIOS screen has loaded, you need to look for the "boot" section, and change order to boot your optical drive (CD/DVD) first.

You cannot install ALONGSIDE windows from WITHIN Windows. You need to be able to boot off the CD/DVD.

Regards,

---

### Post by oldfred on 2014-10-19
Most Windows 7 systems use all 4 primary partitions allowed with MBR(msdso) partitioned drives. So even if you have unallocated space for Ubuntu, you have no partitions available.

Post this from terminal in live installer:
sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

