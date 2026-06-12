---
title: "install of 10.04 loses old /home directories"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2010-05-25
All,

I did a clean install of 10.04 after backing up /home. I reformatted sda1 and sda2 (swap). everything went without any error messages. I reinitialized all my users in the same order as the old system to keep the user numbers the same. I installed all the updates and downloaded and installed the System 76 Driver from the plant76.com repositories as instructed on the Knowledge76 data base. When I went to my home folder everything was empty!! I then noticed that in the file browser there was an entry for a 731GB file system. When I looked in there my old home files were there with everything intact. This volume is not mounted with the regular file system and when I am through with it I must unmount it. It is mounted as media 731GB File system. It does not show up when unmounted even when I use sudo and look at / as root.I did try to copy my picture files to the new home and it worked. It actually moved them because the move took some time.

How do I get these file moved to the new /home and how do I recover this portion of the disk into the regular file system?

---

### Post by darkod on 2010-05-25
If you had a separate /home partition you need to use the Manual Partitioning option during the install and tell it to mount it at /home. Just make sure the format box is not selected.

Otherwise, how does it know you have existing /home partition you want to use?

If you want to mount it automatically at boot, you can do it in /etc/fstab but I don't know the exact commands. However, it will mount it as ordinary partition, not as your Home folder.

I think there is a way to add existing /home partition after the install. You'll have to google around though.

---

### Post by oldfred on 2010-05-25
Since you already have the newhome you can skip many of the steps.

I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

