---
title: "Edgy: Why is my dos partition read only?"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by bigblueswope on 2007-02-14
I upgraded from Dapper to Edgy a couple of weeks ago.

Since then my dos partition has been read only.

Any ideas why?

I saw some posts regarding the new naming conventions for the partitions with the UUID so I've replaced the UUID line in /etc/fstab with one referring to the traditional /dev/hda5 name.

The post Edgy upgrade /etc/fstab entry was:

[FONT="Courier New"][B]# /dev/hda5 -- converted during upgrade to edgy
UUID=424B-27D9 /dos vfat user,uid=1000,gid=1000,umask=2 0 0[/B][/FONT]

I've commented out that line and replaced it with:
[FONT="Courier New"]**/dev/hda5 /dos vfat user,rw,exec,uid=1000,gid=1000 0 0**[/FONT]

Even as su I cannot write to files in the /dos partition.

---

### Post by mssever on 2007-02-14
Here are the options that I use: ```
rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8
```I think that umask is probably what's giving you problems.

---

### Post by bigblueswope on 2007-02-15
I'm a dufus!

dmesg is showing me the problem!

[17192291.424000] FAT: Filesystem panic (dev hda5)
[17192291.424000]     fat_get_cluster: invalid cluster chain (i_pos 0)


So there's a problem with the partition.  I'm going to copy the data off the partition, reformat it and see if that resolves it.  If not, it's a HW issue!  Yay, new laptop!

---

### Post by bigblueswope on 2007-02-17
reformatting the partition did it...

---

