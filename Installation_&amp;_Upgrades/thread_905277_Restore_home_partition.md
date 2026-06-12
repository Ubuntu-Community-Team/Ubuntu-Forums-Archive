---
title: "Restore /home partition"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by toontastic on 2008-08-30
I followed some instructions many moons ago in the Linux Format magazine to create a partition for my home directory. This all worked fine and I have a nice partition which feels safe and can be backed up dead easy. This was a good job as a few weeks ago Ubuntu died. Rather than fighting to fix the problem I decided to format and reinstall which worked great and now Ubuntu is happy again. 

The problem is this, since reinstalled I now have a drive which contains all of my old home directory and the home directory which is created when I installed ubuntu. How do I go about removing the newly created home directory and make ubuntu use the 126gb partition as the home folder ?

Thanks in advance. :KS

---

### Post by forger on 2008-08-30
you should change the /etc/fstab file:
```
gksu gedit /etc/fstab
```

for example:
> # /dev/sda3
UUID=f5c288aa-acd3-48e7-9217-e2dc412f3de3 /home           ext3    defaults        0       2

You change the UUID number to match the partition you want it to use.
You can find the partition's UUID (unique id) using:
```
ls -l /dev/disk/by-uuid/
```

---

### Post by ugm6hr on 2008-08-30
For future reference, when reinstalling Ubuntu, use the "manual" option with LiveCD (or use Alternate), and simply select your /home partition as /home mount point (but ensure the "format" box is unticked).

That way, after reinstalling, your old /home will be ready to go...

---

### Post by toontastic on 2008-09-02
> **ugm6hr said:**
> For future reference, when reinstalling Ubuntu, use the "manual" option with LiveCD (or use Alternate), and simply select your /home partition as /home mount point (but ensure the "format" box is unticked).

That way, after reinstalling, your old /home will be ready to go...


Thanks for that I'll try and remember that next time.


Thanks also for the details on how to change my /home about, I've not been near that computer for a while I'll try and get it done shortly and I'll let you know if it all worked.

---

### Post by toontastic on 2008-09-06
Ok I finally got round to trying this but it didn't seem to work.

I went into fstab which looked like this 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=94cb0b3d-a167-4094-915f-18e880baa7fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=567d86fb-7077-4e6c-bed2-2371640405a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

So as you can see no mention of /home so I followed your other terminal link found the UUID code and added the line

> # /dev/sda4
UUID=12c07134-d4c4-414e-a6d8-73e3cc395a4b /home ext3 defaults 0 2  to just above /dev/sda5 but after a restart I got nothing new and the /home folder is still wrong. Any ideas ?

---

### Post by toontastic on 2008-09-06
Ok I did a full restart of my machine as in turning it totally off and turning it back on and it worked. Problem is I'm now back with the same problem I had before I had before a reinstalled ubuntu. 

Basically I've lost the advanced desktop effects which kills the rest of the machine.

---

