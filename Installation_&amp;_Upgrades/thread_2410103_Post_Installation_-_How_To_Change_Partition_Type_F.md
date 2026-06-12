---
title: "Post Installation - How To Change Partition Type From Media To Home"
date: 2019-01-11
forum: Installation &amp; Upgrades
---

### Post by yuvarajvelmurugan on 2019-01-11
[ATTACH=CONFIG]282173[/ATTACH]

When in installed Ubuntu on my 1 TB hard-drive i choose **[COLOR=#444444][FONT=Roboto-Regular]/media[/FONT][/COLOR]** as partition type for my data storage.

Whenever i boot my PC, i see the media type partition only mounts when i click the drive.

I would like to change the partition type from **/media** to **/home **without loosing the data in the drive.

Could anyone let me know how to do it.

---

### Post by TheFu on 2019-01-11
Please post the cmd and output from
**df -Th**

BTW, avoid spaces in any names, directories, labels.  If you want to read ahead, here's a guide:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Most of the work is easiest when performed by booting from a separate flash drive with Ubuntu on it. Then,
* make a know-you-can-restore backup. Do this first, unless you understand 100% what is being done and can live with 100% data loss.
* create a new directory for all the current files on the "media" partition. Move everything inside that partition inside the newly created directory.  
* create a directory, perhaps /home/ on the "media" drive (assuming it has a Linux file system, not Windows)
* move the old /home/* from the old partition to the new partition.  /home/ isn't mandatory for the name. Lots of places use something else.  The move is important, don't copy.  Things work differently when you move things.
* modify the /etc/fstab on the old /etc/ to include the new partition that gets mounted to /home/
* if you didn't use /home/ on the new mount, then you'll need to modify the /etc/passwd file for any userids that have /home/{userid} to point to the new location.  There are many different ways to accomplish this.  If you aren't an expert, then it is best to just keep the /home/ location. That makes stuff much easier.

You'll need to use sudo to move the data over so all the user, group, and permissions are retained.  All of these steps should be using sudo.

When you know what you are doing, the actual time to accomplish what needs to happen is about 30 seconds, not counting the time to move any data over.

In the end, you want /home/ to appear just like before, in exactly the same place, with exactly the same permissions.

---

