---
title: "installation of Ubuntu 7.10 on an existing partition"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Geraldmanfroid on 2008-04-05
Hello !
I would like to install ubuntu on my computer. For now I have Windows XP and an old version of Fedora. What I would lie to do is to install Ubuntu in the place of Fedora.During the installation I have two possibilities :
either to use the option "guided"  : "resize scsi(0,0,0) ,partition n°5 and use freed space"
or to use the "manuel" mode which proposes me this list :
dev\sda1 ntfs media\sda1 (73000 MB)              <-- I suppose it is  windows
dev\sda2 ext3 media\sda2 (108 MB)                 | What is it ?
dev\sda3 swap                    (2000 MB)               | and that ?
dev\sda5 ext3 media\sda5 (44000 MB)              <-- I suppose it is fedora

What is the solution ? And what the difference between using the "guided" mode and the manuel mode and selecting sda5

Thanks a lot for your help and have a nice day !

Vincent

---

### Post by Pumalite on 2008-04-05
Install Ubuntu. Go 'Manual', delete sda5. In this new free space make 2 partitions:
10 GB for '/'
The rest for /home. Then press 'Forward'

---

### Post by housam on 2008-04-05
> **Geraldmanfroid said:**
> 
During the installation I have two possibilities :
either to use the option "guided"  : "resize scsi(0,0,0) ,partition n°5 and use freed space"
or to use the "manuel" mode which proposes me this list :
dev\sda1 ntfs media\sda1 (73000 MB)              <-- I suppose it is  windows
dev\sda2 ext3 media\sda2 (108 MB)                 | What is it ?
dev\sda3 swap                    (2000 MB)               | and that ?
dev\sda5 ext3 media\sda5 (44000 MB)              <-- I suppose it is fedora


Use the manual way. boot from the live cd, then system>> admin. >> partition editor.
This tool will allow you to delete / resize / create  partitions, use it to delete sda5 as **pumalite **advised you.
sda2 is a storage partition created while installing fedora ( you can delete it if you don't want it anymore )
swap partition is the virtual memory needed for installing ubuntu and it should be swap/solaris format.
the partition you need for installing ubuntu is ext3 format for the root with mounting sign (/).
then during the installation assign these partitions manually.

---

