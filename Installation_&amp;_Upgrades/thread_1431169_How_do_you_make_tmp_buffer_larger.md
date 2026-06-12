---
title: "How do you make /tmp buffer larger?"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Nazaroo on 2010-03-16
I have read that if /tmp is too small, videos choke, and other problems occur.

On my machine, one of the problems was that I couldn't download things because /tmp got full and when I went in to delete some tmp files, I wrecked the system...(not too intuitive I guess).

So this time around, how can I increase the size of /tmp, as well as have it emptied on startup?

I don't want to have it emptied on shutdown, because if I get a crash, the /tmp will still be full...shutdown just doesn't seem to be a reliable place to put essential housekeeping tasks.

any ideas or comments?

Nazaroo

---

### Post by srs5694 on 2010-03-16
The /tmp directory is just a directory. Most people who install Ubuntu do so by setting up one big partition, so /tmp doesn't really have a fixed size limit, aside from the size of the main Ubuntu installation. It is possible, though, to set up /tmp on a separate partition, and if that's how your system is configured, /tmp will have a separate fixed size. To know what you've got, you should look at the output of "df -h". This will produce something like this:

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.0G  633M  5.4G  11% /
udev                   10M  348K  9.7M   4% /dev
/dev/sda5              20G   13G  7.6G  63% /usr
/dev/sda7             100G   78G   23G  78% /home

```

If you see a separate entry for /tmp, then you've got a separate /tmp partition; but if there's no separate entry for /tmp, it's just part of your main root (/) filesystem.

If you've got a separate /tmp partition, then you have just three choices for increasing its size:


[list]
[*]Use a partition resizing tool, such as GParted, to increase the size of the /tmp partition. You'll almost certainly have to decrease the size of another partition to do this. You may need to shut down and do this job from an emergency disc, depending on the layout.
[*]Stop using the /tmp partition, which will then cause the system to use space on the root filesystem for /tmp. You could optionally delete the /tmp partition and increase the size of the partition(s) around it, if you like. To do this, you must comment out or delete the entry for /tmp in /etc/fstab and reboot. (Actually, it can be done without rebooting, but it's easier to describe how to do it with a reboot.)
[*]Stop using the /tmp partition, and create a symbolic link to temporary space elsewhere. This is just like the previous option, but you'd remove the /tmp directory and replace it with a symbolic link to a new temporary space directory on another (non-root) partition. This involves jumping through another hoop or two to set up.
[/list]


If your system does not have a separate /tmp directory, then either your root filesystem is running out of space or you've got a quota configuration that limits the amount of space that /tmp can consume. AFAIK, Ubuntu doesn't set up quotas by default, so the latter seems unlikely. If you're running out of space on your root filesystem, then you'll need to increase its size, create and start using a new partition for /tmp, or create a symbolic link from /tmp to a partition that's got enough free disk space.

---

### Post by Nazaroo on 2010-03-16
Okay, I found this on the internet elsewhere, and I wonder if it is actually safe, or if this could damage my system:

 ```
Now we can modify our file with a happy conscious knowing we’ve made a backup.
 [INDENT]gksu gedit /etc/init.d/sysklogd
[/INDENT] Once you’ve got it open, look for the part  that says:
 [INDENT]stop)
log_begin_msg “Stopping system log daemon…”
start-stop-daemon –stop –quiet –pidfile $pidfile –name syslogd
log_end_msg $?
;;
[/INDENT] You’ll want to add the below line just before the double semi-colons “;;” above. Note also that “;;” looks something like a spider face, which may be of use to you at some point down the road.
 [INDENT]rm -fr /tmp/* /tmp/.??*
[/INDENT] That’s the command that will remove just about anything from your /tmp directory.
 Once you’ve added it, save the file and exit Gedit.  When you shutdown, your /tmp directory will have emptied!

```
I found this message here:
[http://www.arsgeek.com/2007/04/24/removing-files-from-your-tmp-directory-in-ubuntu-when-you-shut-down/](http://www.arsgeek.com/2007/04/24/removing-files-from-your-tmp-directory-in-ubuntu-when-you-shut-down/)

What do you think? Is this a safe thing to do?

- needing advice,
Nazaroo

---

### Post by Nazaroo on 2010-03-16
> **srs5694 said:**
>  


To know what you've got, you should look at the output of "df -h". This will produce something like this:

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.0G  633M  5.4G  11% /
udev                   10M  348K  9.7M   4% /dev
/dev/sda5              20G   13G  7.6G  63% /usr
/dev/sda7             100G   78G   23G  78% /home

```If you see a separate entry for /tmp, then you've got a separate /tmp partition; but if there's no separate entry for /tmp, it's just part of your main root (/) filesystem.
  

Okay I tried your command, and here is what I got. But I don't know what it means...

```
root@unknown:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             3.2G  3.0G   65M  98% /
udev                  502M  284K  501M   1% /dev
none                  502M  232K  502M   1% /dev/shm
none                  502M   96K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda1             5.6G  147M  5.2G   3% /media/sda1
/dev/mapper/pdc_ghijffhf3
                       25G   12G   13G  49% /media/Secured 02
root@unknown:~# 

```

In particular, what is a "mapper"?  and "/lock" ?


> 

If your system does not have a separate /tmp directory, then either your root filesystem is running out of space or you've got a quota configuration that limits the amount of space that /tmp can consume. AFAIK, Ubuntu doesn't set up quotas by default, so the latter seems unlikely. If you're running out of space on your root filesystem, then you'll need to increase its size, create and start using a new partition for /tmp, or create a symbolic link from /tmp to a partition that's got enough free disk space.

I think this is exactly what caused the crash in my previous 9.01 Ubuntu...
There WAS some limit on how much space was allowed in /tmp by some program.  This was triggered when saving files from Firefox.  It wouldn't let me download and save .pdfs or large pictures, just before the crash...

But I don't know where that was controlled or how to check it now with the new 9.10 OS...

Thanks for your help by the way,  :D
Nazaroo

---

### Post by mcduck on 2010-03-16
> **Nazaroo said:**
> Okay, I found this on the internet elsewhere, and I wonder if it is actually safe, or if this could damage my system:

 ```
Now we can modify our file with a happy conscious knowing we’ve made a backup.
 [INDENT]gksu gedit /etc/init.d/sysklogd
[/INDENT] Once you’ve got it open, look for the part  that says:
 [INDENT]stop)
log_begin_msg “Stopping system log daemon…”
start-stop-daemon –stop –quiet –pidfile $pidfile –name syslogd
log_end_msg $?
;;
[/INDENT] You’ll want to add the below line just before the double semi-colons “;;” above. Note also that “;;” looks something like a spider face, which may be of use to you at some point down the road.
 [INDENT]rm -fr /tmp/* /tmp/.??*
[/INDENT] That’s the command that will remove just about anything from your /tmp directory.
 Once you’ve added it, save the file and exit Gedit.  When you shutdown, your /tmp directory will have emptied!

```
I found this message here:
[http://www.arsgeek.com/2007/04/24/removing-files-from-your-tmp-directory-in-ubuntu-when-you-shut-down/](http://www.arsgeek.com/2007/04/24/removing-files-from-your-tmp-directory-in-ubuntu-when-you-shut-down/)

What do you think? Is this a safe thing to do?

- needing advice,
Nazaroo

looks quite pointless, since /tmp is already cleaned by default when you reboot the system... :D

---

### Post by mcduck on 2010-03-16
> **Nazaroo said:**
> Okay I tried your command, and here is what I got. But I don't know what it means...

```
root@unknown:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             3.2G  3.0G   65M  98% /
udev                  502M  284K  501M   1% /dev
none                  502M  232K  502M   1% /dev/shm
none                  502M   96K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda1             5.6G  147M  5.2G   3% /media/sda1
/dev/mapper/pdc_ghijffhf3
                       25G   12G   13G  49% /media/Secured 02
root@unknown:~# 

```


It tells you that your root partition (/dev/sda6) is almost completely full, and as your /tmp directory is in that partition this is what causes your problems with not enough space on /tmp.

3,2GB really is rather small for a root partition, you only have 65MB of available space there...

(there is no other limit for available space on /tmp than the amount of available free space on the partition where /tmp is located)

---

### Post by srs5694 on 2010-03-16
Your Ubuntu is installed in one partition (/dev/sda6), but it's only 3.2GB in size, with 3.0GB in use. You can ignore most of the other entries in your df output; they're specialized virtual filesystems, not real disk space. The one exception is another 5.6GB partition (/dev/sda1) mounted at /media/sda1. This partition is mostly empty (5.2GB free). For perspective, consider the example I posted. My Linux root filesystem is 6.0GB in size  (0.6GB used), and I've got separate /usr (20GB, 13GB used) and /home (100GB, 78GB used) partitions. Thus, your system is tiny compared to mine. Of course, individual use of /home (where users' data files go) varies a lot, but 3GB is very little space for a modern working Linux system. It's no wonder you're running out of space.

You'll need to do some more digging to figure out how to proceed. You could post the output of "sudo fdisk -l" (that's a lowercase L, not a digit 1), but you really need to know if you've got any partitions that are mostly empty that you could shrink to make room for expansion of your Linux system. Your /dev/sda1 is certainly a candidate, but there could be intervening partitions or reasons not to touch it. GParted might provide you the information you need in its GUI display, or if you've got Windows or some other OS installed you may need to boot into it and use its own disk space displays to ascertain where you've got free space.

In a worst-case scenario, you might need to add another hard disk or upgrade your existing one, but I suspect you'll be able to use /dev/sda1 in one way or another.

As to editing /etc/init.d/sysklogd, the edit you posted will have the effect of deleting everything in /tmp when the system shuts down. The edit could be wiped out by future package upgrades, though. Personally, I wouldn't bother; your real problem is lack of disk space on your root filesystem, and deleting old files from /tmp is a band-aid. Finding more disk space is the cure.

---

### Post by srs5694 on 2010-03-16
Oh, wait a second: I missed this entry:

```

/dev/mapper/pdc_ghijffhf3
                       25G   12G   13G  49% /media/Secured 02

```

This makes it look like you've got an LVM configuration with a 25GB logical volume that's about half full. This makes your installation more complex, with still more possibilities for finding more disk space. Try typing "sudo vgdisplay". Near the bottom of the output will be lines like this:

```

  Total PE              119086
  Alloc PE / Size       93184 / 364.00 GiB
  Free  PE / Size       25902 / 101.18 GiB

```

This tells you how much space you've got in your LVM and how much of that space is unused. It may be possible to create a new logical volume just for /tmp. Also, post the contents of /dev/mapper ("ls /dev/mapper").

I also recommend you find out what's in /dev/sda1 (mounted at /media/sda1). Since you've already got an LVM, it may be worthwhile to move some of your standard directories into logical volumes, and if there's not much free space in your volume group, it may be desirable to add /dev/sda1 to it, if the files that are there now are unimportant or can be moved elsewhere.

---

### Post by Nazaroo on 2010-03-16
Okay I think I understand a few points:

(1) the /tmp thing is maybe only a symptom, not a cause of my woes, at least now.

(2) its back to messing with partitions and directories...


I have been asking for help in another thread regarding recovering some 5 Gig of HD space here in this thread:
[http://ubuntuforums.org/showthread.php?t=1431132](http://ubuntuforums.org/showthread.php?t=1431132)

perhaps if you would review my output from the terminal there, and see the 1st msg as to how I got in this mess, something would become clearer as to what I should do now...

I will do the listing though:


...sudo vgdisplay gives "command not found".


ls /dev/mapper gives this:

control       pdc_ghijffhf1  pdc_ghijffhf3
pdc_ghijffhf  pdc_ghijffhf2  pdc_ghijffhf4
root@unknown:~#  
 

I hope this means something to you, because it looks like a machine dump to me.

Thanks for your help, 
Nazaroo

---

### Post by srs5694 on 2010-03-16
It looks like somewhere along the line you created an LVM on this system, but then uninstalled at least some of the LVM tools. You should re-install the LVM tools by doing a "sudo apt-get install lvm2". That will restore your LVM tools and you'll be able to see how your current LVM is configured, and use the LVM tools to modify that configuration, should you choose to do so.

---

### Post by srs5694 on 2010-03-16
OK, I took a look at your posts in your other thread, and it now appears that the two devices in /dev/mapper are actually Windows (NTFS) drives of some sort, probably in a Windows LVM or RAID configuration. I'm unfamiliar with Windows' LVM or RAID equivalents, so I can't offer much advice on dealing with them. You can forget about the Linux lvm2 package and all its tools, though.

---

