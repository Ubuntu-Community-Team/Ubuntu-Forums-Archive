---
title: "removing win98?"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by eilu on 2006-10-17
Hello all. I've been using Ubuntu for ~3 days now, and I have a question:

Since I just wanted to try out Ubuntu 6.06, I chose to dual boot when I installed. I used the first option in the CD (resize current partition and use freed space).

I'm now considering switching for good. Is there a way I can change my partitions and get rid of Windows without wiping out my Ubuntu installation? I'd hate to loose all those updates and packages I've already installed. Also, now that I know more about it, I'd like to move the /home to its own partition and maybe add a fwe MB's to the swap partition as well. Is there a quick way to do this?

My current system is on a 40GB HD, evenly split between a FAT32 (Win98SE) and an Ext3 (Ubuntu) partition. I'm still playing around with it and learning the ropes (I've only had it for 3 days so far).

Thanks for any solutions/suggestions you might have.

---

### Post by Kateikyoushi on 2006-10-17
You can repartition your drive with gparted.

You can install it with the following commands.
```
sudo aptitude update
sudo aptitude install gparted
```

To run it type this to terminal.
```
sudo gparted
```

If you need help how to use it tell us how would you like to use the free space.

---

### Post by bulldog on 2006-10-17
You're relative new to Ubuntu,so I would say,keep your windows a bit longer.

If you mess up your Ubuntu you can't go to the forums for a solution.

When you have a bit more experience and are able to solve some trouble on your own,then comes the time to delete your windows.

Just my opinion. :D

---

### Post by Helios89 on 2006-10-17
I think so, too. You should be able to receive support if your Ubuntu doesn't work. I still keep Windows just in case....but i prefer Kubuntu! :)

---

### Post by joff13 on 2006-10-17
as Kateikyoushi said with gparted you'll find a ggod way to do your job.

because you are using win98 (fat32) you could resize win98 to just 5GB and as you told enlarge swap (about the double of your RAM) and make /home in a separated partition

have a look to /etc/fstab 

```
cat /etc/fstab
```

to understand that all is quite easy

just to let you think, this is myone 

```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs defaults        0       1
/dev/hda5       /boot           ext2    defaults        0       2
/dev/hda8       /home           reiserfs defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

hda1 and hda3 are two win partition (but not loaded on startup)

enjoy

---

### Post by eilu on 2006-10-17
> **bulldog said:**
> You're relative new to Ubuntu,so I would say,keep your windows a bit longer.

If you mess up your Ubuntu you can't go to the forums for a solution.

When you have a bit more experience and are able to solve some trouble on your own,then comes the time to delete your windows.

Just my opinion. :D

That's a good point. I think I'll go with that for now, since Ubuntu and win98 together use less than half of my HD anyway.

> **Kateikyoushi said:**
> You can repartition your drive with gparted.

You can install it with the following commands.
```
sudo aptitude update
sudo aptitude install gparted
```

To run it type this to terminal.
```
sudo gparted
```

If you need help how to use it tell us how would you like to use the free space.

Thanks! Glad to know it won't require me to jump through hoops to get it done. *saves info*

---

