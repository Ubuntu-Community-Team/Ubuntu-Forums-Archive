---
title: "Partition Issue"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by huangyingw on 2013-08-29
Hi,
    I install my Ubuntu on sda1, and grub installed to sda. And it's the sole OS on my SSD disk.
    Only one SSD in my PC, the layout of my disk is as bellow
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    73402438    36700195+  83  Linux
/dev/sda2        73402439   488397167   207497364+  83  Linux
```
    When boot, the grub menu is somehow skipped, I mean, it directly boot to the default option. And, when I try to backup sda1 using clonezilla, the partition sda1 could not be found, while sda2 is ok. So, I decide to do disk backup, this time, the whole disk sda, could not be found by clonezilla.
    I guess there might be something wrong in my sda1 partition, while I could not format it...
    Could someone help me with this issue.

---

### Post by Dennis N on 2013-08-29
With only one OS on your disk, the grub menu is skipped by default. You can force it to appear, however. Why is there no swap partition?

---

### Post by huangyingw on 2013-08-29
> **Dennis N said:**
> With only one OS on your disk, the grub menu is skipped by default. You can force it to appear, however. Why is there no swap partition?
   Because my hard disk is SSD, I don't want too much unnecessary I/O on it, so no swap partition.
   How to force it to appera? Setting this in /etc/default/grub? ```
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false

``` . I have tried, but failed. 
   I don't care on grub menu page. What I care is in clonezilla, the sda1 partition could not be recognize, this make me impossible to do a partition or disk backup..

---

### Post by carl4926 on 2013-08-29
IIRC if you hold the SHIFT key at boot,you should get the grub menu
And it looks like the HD could afford some swap

Can you still boot in to ubuntu?

---

### Post by huangyingw on 2013-08-29
> **carl4926 said:**
> IIRC if you hold the SHIFT key at boot,you should get the grub menu
And it looks like the HD could afford some swap

Can you still boot in to ubuntu?
To make it clear: I could boot into ubuntu. My problem is the Ubuntu partition: sda1, could not be found in clonezilla, which make it impossible for me to backup it.

---

### Post by Dennis N on 2013-08-29
On a per boot basis, you press shift during the boot up do display the menu. (I think any key may work?).

To make it always appear, see first answer here:

[http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time-on-a-single-boot-system-not-dual-boot](http://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time-on-a-single-boot-system-not-dual-boot)

Also, besides what is said there, I would try GRUB_TIMEOUT=-1 since this stops the boot from going to the default and wait at the menu. I have not tried this, however, for just one OS.

---

### Post by carl4926 on 2013-08-29
I haven't really used clonezilla

---

### Post by Dennis N on 2013-08-29
Clonezilla puts out lots of messages while working - maybe you can see something there? I have used it a few times, but never had a problem. Sorry I cannot be of more help on that.

---

### Post by mastablasta on 2013-08-29
hard to say why it doens't see the driver propperly. also as i knwo clonezilal has or at least had two variants (ubuntu and debian)

you could maybe try to use redo backup (ubuntu based) instead. see what it shows you.

---

### Post by oldfred on 2013-08-29
I have not used clonezilla, so cannot help on that.

But what is sda1, is it just the system and sda2 is /home? If so there is not much in sda1 to backup as it is system files. All user data and configuration is in /home and you can restore entire system with a new install and restore of /home.

The few things in the system you may want in a backup are any hardware configuration settings that are usually in /etc. If I manually edit hard ware configuration I just make a copy in a folder in my /home so I automatically include that. If you set any cron task you would want to back those up. And I like to export a list of installed applications to make it easy to reinstall everything if necessary.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by VMC on 2013-08-29
> **huangyingw said:**
> To make it clear: I could boot into ubuntu. My problem is the Ubuntu partition: sda1, could not be found in clonezilla, which make it impossible for me to backup it.
Using Clonezilla, are you trying to *savedisk *or* saveparts *? Also what are you using for *local_dev *? Make sure its different from the disk you cloning.

You could just use partimage. For me, its quicker and easier.

clone example:```
sudo partclone.ext4 -c -s /dev/sda01 | gzip -c --fast>image.gz
```


Restore example:
```
zcat image.gz | partclone.ext4 -r -o /dev/sda01
```

Replace (sda01) with your dev number. Also replce ext4 with you fs.

---

### Post by huangyingw on 2013-08-30
thank you all. My fault, after editing /etc/default/grub, I forget to run update-grub2, that's why I could not enter gru2 menu while pressing shift key..
After boot clonezilla from local disk, this time, it could find my sda1 partition. My previous try is to boot clonezilla via usb disk, it could only find sda2, not sda1.
Really, I don't know why after this change, the sda1 partition could be found again. I will continue investigate.

---

### Post by huangyingw on 2013-08-30
> **VMC said:**
> Using Clonezilla, are you trying to *savedisk *or* saveparts *? Also what are you using for *local_dev *? Make sure its different from the disk you cloning.

You could just use partimage. For me, its quicker and easier.

clone example:```
sudo partclone.ext4 -c -s /dev/sda01 | gzip -c --fast>image.gz
```


Restore example:
```
zcat image.gz | partclone.ext4 -r -o /dev/sda01
```

Replace (sda01) with your dev number. Also replce ext4 with you fs.
Clonezilla could do more than just partition backup, it could resize, restore my MBR, which are quite important, when I want to transplant my OS from one machine to another machine.
Certainly I would prefer to do this in shell, could you provide me with such a shell.
Or, I believe, there are run log of clonezilla, which will tell us what exact command and parameter it use, I will try to capture and save the log of clonezilla, so, I could base on that to mimics my shell.

---

### Post by huangyingw on 2013-08-31
> **oldfred said:**
> I have not used clonezilla, so cannot help on that.

But what is sda1, is it just the system and sda2 is /home? If so there is not much in sda1 to backup as it is system files. All user data and configuration is in /home and you can restore entire system with a new install and restore of /home.

The few things in the system you may want in a backup are any hardware configuration settings that are usually in /etc. If I manually edit hard ware configuration I just make a copy in a folder in my /home so I automatically include that. If you set any cron task you would want to back those up. And I like to export a list of installed applications to make it easy to reinstall everything if necessary.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
Thank you so much for these information about backup. In fact, I have my own self-design backup shell, while only specifically works for my file system structure.

---

