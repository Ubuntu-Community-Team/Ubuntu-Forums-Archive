---
title: "Moving usr and var to their own partitions"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by gwi on 2007-01-08
I tried to move /usr and /var to their own partitions, using the following steps:
[LIST=1]
[*]boot with the live cd
[*]create two new partitions, formatted with reiserfs, and labeled var and usr
[*]mount the partitions as /mnt/var and /mnt/usr
[*]mount the root partition as /mnt/root
[*]move contents of /mnt/root/var to /mnt/var
[*]move contents of /mnt/root/usr to /mnt/usr
[*]add var and usr to /mnt/root/etc/fstab:
```
[FONT="Courier New"]LABEL=usr       /usr            reiserfs defaults                            0       2
LABEL=var       /var            reiserfs defaults                            0       2[/FONT]
```
[*]remove /mnt/root/var and /mnt/root/usr
[/LIST]

After rebooting, I see the message
```
mount point /var/run not found
```
among the messages in the splash screen. After that the screen turns into an all text screen.
After
```
* Running local boot scripts (/etc/rc.local)
```
the system freezes.

After moving the contents of the var and usr partitions back to their original position in the root partition, the system boots normally again.

What did I do wrong?

Here are the current contents of /etc/fstab:
```
[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>                           <dump>  <pass>
proc            /proc           proc     defaults                            0       0
LABEL=root      /               reiserfs defaults                            0       1
LABEL=boot      /boot           ext3     defaults                            0       2
LABEL=home      /home           reiserfs defaults                            0       2
# LABEL=usr       /usr            reiserfs defaults                            0       2
# LABEL=var       /var            reiserfs defaults                            0       2
LABEL=fotos     /fotos          reiserfs defaults                            0       2
LABEL=vmware    /vmware         reiserfs defaults                            0       2
LABEL=swap      none            swap     sw                                  0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=30F43340F433081C /media/winprogs ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto                      0       0[/FONT]
```

---

### Post by eXisor on 2007-01-08
Possibly you didn't copy the symbolic links correctly.

I suggest you look at this Howto on psychocats.net to see how to go about this (the example is for the /home folder, but will work for /usr etc).

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by chris_nava on 2007-01-08
You removed /mnt/root/var and /mnt/root/usr instead of their contents.
The empty folders are required to give mount a target to mount the other file systems.
Just create empty directories in their place and you should be set.

---

### Post by gwi on 2007-01-13
You're right. I removed /var and /usr, assuming the mount points were created automatically. Strange enough, after the failed boot there was a /var/lock.

I tried again with the empty /var and /usr directories. The system now boots and starts Gnome, but there are three problems that are not there when I revert to the original situation:
[LIST=1]
[*]I still get the error "mount point /var/run not found" when running init-bottom script;
[*]there are no eth0 and lo network interfaces (so no network, no internet);
[*]Gnome sensors applet shows a harddisk temperature of -1 degree C, while hddtemp on the commandline shows the correct value.
[/LIST]
I have now moved back to the original situation: /var and /usr are back on the root partition, and everything is fine (except less free disk space on the root partition, and two empty partitions doing nothing).
What is going wrong, and how can I solve it?

---

