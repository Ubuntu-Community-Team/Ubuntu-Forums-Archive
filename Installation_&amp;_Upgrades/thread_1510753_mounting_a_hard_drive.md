---
title: "mounting a hard drive"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by eldinv on 2010-06-15
hello all, 

im a newbie again to ubuntu got the newest version and im so suprise with the speed of everything. AWESOME job! 

i got a second hard drive that i want to mount but dont know if im to change something so that it will mount. can anyone point me to the right direction. this drive came from windows 7 and is basically media files and school docs.

screenie at the bottom and thank you for any help in advance. 

[[IMG]http://a.imagehost.org/0433/Screenshot.png[/IMG]]("http://a.imagehost.org/view/0433/Screenshot")

[IMG]http://a.imagehost.org/view/0433/Screenshot[/IMG][IMG]http://a.imagehost.org/view/0433/Screenshot[/IMG]

---

### Post by oldfred on 2010-06-16
It is saying it is already mounted. You often auto mount under a default name by looking at a partition using places and looking at places on the left panel. But since it is a part of your system you may want to mount it at the time of booting with fstab.

You do not mount drives but partitions. You create a name to mount it to and then mount it to that name. Commands are slightly different depending on whether partition is ext3, ext4, NTFS, FAT etc.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

If  you have some understanding of the settings from above links you can use this to create mount and edit fstab.

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

But you still should know how to edit and update fstab.
 Before rebooting after editing fstab alway run this to reload fstab and make sure it has no errors

```
sudo mount -a
```

---

### Post by eldinv on 2010-06-16
[[IMG]http://img717.imageshack.us/img717/5607/screenshot1ks.png[/IMG]]("http://img717.imageshack.us/i/screenshot1ks.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")


why is it in red say says to mount? those sites lost me, i thought it would be simple like the other partition i mounted on the same drive, then i deleted after i transfer all the information..

i think the problem might have to do with permissions and taking ownership or something

---

