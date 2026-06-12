---
title: "How to uninstall ubuntu (alongside windows version)"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by robolist2 on 2014-05-26
I am very new to Ubuntu and I have just install it alongside my windows 7 using the iso file mounted onto a USB drive. I followed the setup and nothing went wrong. While I do not necessarily wish to uninstall Ubuntu now, I may wish to do so for some reason in the future and I would at least like to learn how it is done now so that I am prepared. 

Any help and advice would be much appreciated. thanks   

Rob

---

### Post by Mark Phelps on 2014-05-26
Telling us "alongside" isn't telling us anything useful as that term has lots of different interpretations.

So, presuming what you meant is that you installed Ubuntu to its own partition, then removing it later involves the following:
1) Deleting the Ubuntu partition (have to do this from OUTSIDE Ubuntu)
2) Restoring the original Windows MBR.  To do this, you should NOW use the Win7 Backup feature to create and burn a win7 Repair CD.  You will need that later to restore the Windows MBR.

---

### Post by oldfred on 2014-05-27
Also most Windows 7 systems used all 4 primary partitions. 

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

### Post by robolist2 on 2014-05-27
Great, thanks for the info. Cheers

---

### Post by coffeecat on 2014-05-27
@robolist2, another one for your bookmarks. This is only for a situation where you might want to remove the Ubuntu partition(s) and restore the Windows bootloader:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

