---
title: "Wubi, partitions"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by rebecca5 on 2014-11-02
Hi there, 

I've got what I assume is a pretty basic problem when trying to install Ubuntu with Wubi, on a Windows 7 machine... Ubuntu can't complete installation because of the following errors:

'Failed to partition the selected disk (probably because there are too many partitions in the partition table)' and
'No root file system' 

I have no great understanding of partitions, so I would really appreciate advice on what to do. I can see that at the moment my one disk is spilt beween C:, Recovery and an untitled 557MB partition (any tips on what this is??)

Thanks a million! 

R

---

### Post by sudodus on 2014-11-02
Welcome to the Ubuntu Forums :-)

Wubi was developed to make it easy to test Ubuntu. Unfortunately it does not work with Windows 8, so there is no future, and the developement and maintenance has stopped. It also means that there are few people here at the Ubuntu Forums, who are able to help. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

We recommend that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by oldfred on 2014-11-02
Also if a Windows 7 system, you probably have all 4 primary partitions used. Even if you have unallocated space left on drive, you cannot create another primary partition.
You have to convert one primary to an extended partition, and then can have an unlimited number of logical partitions inside the one extended.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by hakuna_matata on 2014-11-03
> **rebecca5 said:**
> (any tips on what this is??)
A known bug: [https://bugs.launchpad.net/wubi/+bug/1385930](https://bugs.launchpad.net/wubi/+bug/1385930)

---

