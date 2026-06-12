---
title: "Write Permission to Ext3 Partition"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by kidrock on 2005-03-07
Hi how do I set write permissions to an Ext3 partition 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /SM1            ext3    defaults        0       0
/dev/hda7       /SM2            ext3    defaults        0       0
/dev/hda8       /SM3            ext3    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0


Thanks...

---

### Post by kidrock on 2005-03-07
Someone please help I dont want to reinstall again....

---

### Post by rwabel on 2005-03-07
I guess you want to have write permission as normal user on your partition?

Linux partition are different to windows partition. You mount them normally and only root as write permission. You can then change the permission of directories on that partition so normal user can write to it.

I hope I could help. Somebody correct me if I'm wrong, but as far as I understood, that's  the linux way of it.

Works just fine like that for me. I've in the beginning also tried to mount the partition with write permission for normal user, as I mounted the fvat partition in fstab :-)

---

### Post by kidrock on 2005-03-07
No help mate... thanks though...

These are 3 ext3 partitions on the same drive....but i dont have write permission..
so i need to know...how to go about doing this....


thanks

---

### Post by rwabel on 2005-03-07
as I said, only root has write permission. try sudo mkdir test on one of the ext3 partition. That should work.
If you want to have write permission as normal user just chmod the needed directory so you have permission to write to it.

[QUOTE=kidrock]No help mate... thanks though...

These are 3 ext3 partitions on the same drive....but i dont have write permission..
so i need to know...how to go about doing this....


thanks[/QUOTE]

---

### Post by kidrock on 2005-03-07
Please give me the chkmod for write permissions...but them i would have to do it everytime i reboot?

---

### Post by alastair on 2005-03-07
/dev/hda6 /SM1 ext3 defaults 0 0

So, /SM1 is mounted?

mount 

and look.

If mounted - then something like :

sudo chown <yourname>.<yourgroup> /SM1  (<-- you own this - type "id" to see your user/group id)

sudo chmod 777 /SM1    (<-- full access to world)

---

### Post by rwabel on 2005-03-07
exactly :-)

---

### Post by kidrock on 2005-03-08
I can mount it...but then i have to do it everytime i restart....how do i make it permanent?

---

### Post by krusbjorn on 2005-03-08
[QUOTE=kidrock]I can mount it...but then i have to do it everytime i restart....how do i make it permanent?[/QUOTE]

to mount it automatically everytime you boot the computer, add a line for it in /etc/fstab. a google search on fstab will give you the information needed.

good luck!

---

### Post by kidrock on 2005-03-08
I tried umask but that doesnt  mount the drives....thanks

---

### Post by alastair on 2005-03-08
No, "umask" does not mount drives.

See : man umask

Remember, unix system have extensive manual pages (see : man man). There is also a lot of documents online all over the web.

To mount a filesystem at boot, the OS looks at the file :

/etc/fstab

See : man mount

It should be fairly self-explanatory.

You already seem to have a decebt fstab line mentioned :

/dev/hda6 /SM1 ext3 defaults 0 0

Get it mounted, do the chmod/chown, or whatever, and get going. What's the problem?

---

