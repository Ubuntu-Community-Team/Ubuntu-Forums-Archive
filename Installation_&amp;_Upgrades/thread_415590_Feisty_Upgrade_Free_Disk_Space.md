---
title: "Feisty Upgrade Free Disk Space?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by moxie0 on 2007-04-20
It looks like the update manager isn't following symlinks when verifying the amount of disk space available for an upgrade.  For instance, I have things setup such that /var/cache/apt is a symlink to the root partition, which has 4GB free.  The /var/ partition only has 600MB free, and the update manager keeps asking for another 400MB.  I have a feeling it's looking at the size of the /var/ partition, rather than the size of the / partition.  

Is there a way to make it see the free disk space, or otherwise force it to begin an upgrade even if it thinks there's not enough space available?

---

### Post by earobinson on 2007-04-20
can you post the output when you type df at the command line

---

### Post by moxie0 on 2007-04-20
moxie@searching:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             9.2G  4.9G  3.9G  57% /
varrun                490M  124K  490M   1% /var/run
varlock               490M  4.0K  490M   1% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                490M     0  490M   0% /dev/shm
/dev/hda3              26G   24G  648M  98% /home
/dev/hda4             989M  328M  611M  35% /var
/dev/sda1             459G  117G  319G  27% /media/ieee1394disk


moxie@searching:~$ ls -l /var/cache/
total 52
drwxr-xr-x  2 www-data www-data 4096 2006-01-07 08:01 apache
drwxr-xr-x  2 root     root     4096 2006-10-27 11:59 app-install
lrwxrwxrwx  1 root     root        4 2007-04-20 11:36 apt -> /apt
drwxrwxr-x  3 cupsys   lp       4096 2006-06-12 13:30 cups
drwxr-xr-x  2 root     root     4096 2007-04-20 02:09 debconf
drwxr-xr-x  2 root     root     4096 2006-05-08 06:04 dictionaries-common
drwxr-xr-x  5 root     root     4096 2006-07-23 21:44 fonts
drwxr-xr-x  3 root     root     4096 2006-05-08 05:57 gnome-system-tools
drwxr-xr-x  2 root     root     4096 2005-07-05 06:15 locate
drwxr-sr-x 16 man      root     4096 2007-04-20 11:29 man
drwxr-xr-x  2 root     root     4096 2007-03-02 11:11 modass
drwxr-xr-x  2 root     root     4096 2006-02-23 08:37 pppconfig
drwxr-xr-x  4 root     root     4096 2006-05-08 09:14 setup-tool-backends
drwxr-xr-x  3 root     root     4096 2006-10-29 01:11 system-tools-backends

---

### Post by viocudinti on 2007-04-21
Same issue here ... i would rather do a temporary symlink then start resizing partitions.
Any quick fix for this ?

---

### Post by jdong on 2007-04-21
There's probably no quick fix, but there probably is a way to circumvent disk space checking. That's quite an odd but interesting setup, and I'm not surprised it confuses the upgrader :D


You may have to resort to the manual upgrade (consult upgrade documentation on Ubuntu website)

---

### Post by moxie0 on 2007-04-21
It's somewhat common for people to encrypt the /var/ partition, but then symlink the apt archives out of it since they're just going to be encrypted to disk, unpacked, and then unencrypted as they move over to a root partition.  What's interesting is that the disk space checking worked correctly in previous releases, and only just now broke.

I guess I will resort to a manual upgrade.

---

### Post by jdong on 2007-04-21
> **moxie0 said:**
> It's somewhat common for people to encrypt the /var/ partition, but then symlink the apt archives out of it since they're just going to be encrypted to disk, unpacked, and then unencrypted as they move over to a root partition.  What's interesting is that the disk space checking worked correctly in previous releases, and only just now broke.

I guess I will resort to a manual upgrade.

If you believe this procedure is common and the installer should somehow account for it, then it's worth your time to file a bug report in Launchpad regarding it. I doubt any of the installer developers were considering this scenario!

---

### Post by moxie0 on 2007-04-21
Here's the quick fix.  Create or edit /etc/apt/apt.conf and add this line:

Dir::Cache::archives "/path/to/your/archive/dir";

---

### Post by henriquemaia on 2007-04-25
> **moxie0 said:**
> Here's the quick fix.  Create or edit /etc/apt/apt.conf and add this line:

Dir::Cache::archives "/path/to/your/archive/dir";

Thanks a lot. This is a great fix. I have an unusual partition setup and I was going a bit tired of this error.

---

