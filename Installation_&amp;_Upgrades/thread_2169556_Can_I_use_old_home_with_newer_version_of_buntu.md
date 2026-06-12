---
title: "Can I use old /home with newer version of buntu?"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by nick7076 on 2013-08-22
Let me explain.....
Partition 1 has Ubuntu 12.04LTS. This install I have badly corrupted, to the extent that Ubuntu will not boot, nor will any of the earlier kernel versions. I can access all the files and have backed up everything I need.

Partition 2 has Ubuntu 13.04 and is a clean new install with no added apps etc.

Partition 3 is Win XP

How can I use the /home folder from partition 1 with the copy of ubuntu on partition 2?

Could I create another partition for a new /home and copy all the files from partition 1? Or if I reinstall 13.04 on partition 2 will the option during install to import settings work?

What I need to end up with is 13.04 with all my settings from my original (12.04) install. I do not want to have to set up email and download thousands of emails from my server and I also need to access thunderbird archived emails. I don't mind reinstalling programs, but things like bookmarks, tomboy notes, etc I need to retrieve.

Hope the question is clear. And somebody knows the answer!

Thanks

---

### Post by SeijiSensei on 2013-08-22
If you can mount the old partition into the filesystem (I'll use /dev/sda1 for the old partition and /mnt as the mount point in the example), try this:

```

sudo mount /dev/sda1 /mnt
cd /mnt/home
sudo rsync -av . /home

```

As a trial run, first use "-avn" as the parameters to rsync.  That will list the files the program will transfer but not copy any files.  If everything looks okay, run it with just "-av" to create a complete copy of the old home directory tree under the new /home.  (You can use Ctrl-C to cancel the dry run midway through once you're sure it will produce the proper results.)

I keep /home on a separate partition so I can change operating systems without losing my files.

**Update**:  Actually this task is best performed after booting into a "recovery mode" session using your new installation.  Choose "root shell" when you are presented with a menu of choices.  You won't need to use "sudo" as you already have root privileges in recovery mode.  However you may need to make the new installation's filesystem writable by running the command:

```
mount -o remount,rw /
```

at the initial shell prompt.  Note there is no space between the comma and "rw".

---

### Post by nick7076 on 2013-08-22
Many thanks,

I thought I could simply copy everything but did not know about rsync. 

I have only tried Thunderbird email but all my settings and archive seems to be there.

It worked without having to be in recovery mode.

---

