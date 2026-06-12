---
title: "Need help on resizing partitions"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by agiledata on 2005-08-22
I'm a recent convert from Windows to Ubuntu Linux. When I did the original installation, everything was very clear apart from how to partition the disk. I realise now that I should have used LVM for flexible partitioning, but I didn't. I made /var too small and wanted to increase its size, given it's already over half full.

I didn't know of a Linux equivalent to Partition Magic, but I thought, no problem: I'll just  back up and delete one large, nearly empty partition and create two smaller ones in its place, of the size I wanted. Unfortunately, the partition that I chose was /home. Deleting this with fdisk was not a good idea!  :-|  

I've made my replacement /var partition, but Ubuntu won't boot because it can't find my home directory.  I accept the offered "use root as your home directory?" and I can get an emergency command window, with root access using sudo. However, when I try to format or mount the new partitions, using standard commands, I get loads of error messages, and realise I'm out of my depth. Please could someone tell me the correct commands from this emergency window, to do what I think is the correct sequence: (see further details in next post)

[list=1]
[*]format /home (replacement)
[*]mount /home
[*]copy /usr/home_backup to /home
[*]reboot Ubuntu with my account back working again!
[*]format /var_new
[*]mount /var_new
[*]copy /var to /var_new
[*]rename /var to /var_old
[*]rename /var_new to /var
[/list]

---

### Post by agiledata on 2005-08-22
Perhaps some more details would help...

I have formatted my new /home directory using
```
sudo mkfs.ext3 /dev/hda7
``` 
Then I mount it with:
```
sudo mount -v -l -t ext3 /dev/hda7 /home
``` 
All the files need to be recursively copied from the backup, preserving attributes:
```
sudo cp -r -p all -v . /home
```
The files appear to copy Ok, but when I try to reboot, I get a message that says my session lasted less than 10 seconds, and suggests trying a failsafe session.
The xsession errors file shows:
```
/etc/gdm/Xsession: Beginning session setup...
Could not set mode 0700 on private per-user gnome configuration directory '/home/rob/.gnome2_private/': Operation not permitted
```
What else do I need to do in the copying from /home backup to enable the necessary permissions?

Thanks in advance,  

Rob

---

