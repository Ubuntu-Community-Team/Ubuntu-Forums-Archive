---
title: "Install Ubuntu-Gnome 15.04 &quot;something else&quot; advanced options"
date: 2015-08-26
forum: Installation &amp; Upgrades
---

### Post by RobertoRecordo on 2015-08-26
I am in the middle of re-partitioning (separate home folder, room for installing a second distro)  and installing Ubuntu-Gnome 15.04 amd64.

The release notes warn 
[LIST]
[*]Installation freezing when selecting manual partitioning ([1361951]("https://bugs.launchpad.net/bugs/1361951")): This can be avoided by creating partitions with gparted before running the installer.
[/LIST]

So I have (successfully) re-partitioned my drive using the live DVD  gparted app. Now I can mount and see the filesystem, and was able to copy /home/usr1 and /home/user2 to remote areas of the drive.

What I need help with is the "something else" option of the installer. **It appears that there is no way to select existing partitions for home, root, and swap.**

I can, of course, select "upgrade 12.04" or let it do a standard install on the first partition ... but my first choice is to learn how to make it install on the existing partitions.

Any advice? Pointers to a tutorial?

-Rob

---

### Post by howefield on 2015-08-26
Where are you stuck, should be a fairly simple case of highlighting the partition that you want to use, press the change button , set the file system, check the format box (if you want it formatted) and finally set the mount point from the drop down or create your own.

---

### Post by RobertoRecordo on 2015-08-26
Thank You Howefield! This is solved. As in the release notes I got a blank screen after install, but a Power On Reset successfully booted the system! Vivid!

---

