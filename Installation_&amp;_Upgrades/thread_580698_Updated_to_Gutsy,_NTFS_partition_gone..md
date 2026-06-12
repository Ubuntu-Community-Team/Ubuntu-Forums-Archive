---
title: "Updated to Gutsy, NTFS partition gone."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by FFighter on 2007-10-19
When I switched to Feisty from XP, I left a backup NTFS partition for migration purposes putting all my  important files there and Feisty had detected it successfully - I was able to access the NTFS partition (mounted on media/hda5) to read files.

I just updated to Gusty and my NTFS partition is gone. How could I re-activate it?

Thanks.

---

### Post by JunSeok Kang on 2007-10-19
I had the exact same problem, and I found the dev name has been changed.

At the terminal, type 

fdisk -l

and you will see the list of partitions.
In my case, /dev/hdc1 has been changed to /dev/sba1.

You should apply this in your /etc/fstab.

But, I am kinda looking for away to apply this automatically, just out of curious. :)

---

### Post by Hyporeal on 2007-10-20
I had the same problem as well, but for a different reason. The EVMS package was causing the trouble for me.

I had to remove the EVMS package to regain access to my NTFS partition. Use Synaptic or enter the following:

```
sudo apt-get remove evms
```

It also solved the problem of /sbin/udevd consuming all of my CPU resources.

---

### Post by peter771 on 2007-12-06
> **Hyporeal said:**
> I had the same problem as well, but for a different reason. The EVMS package was causing the trouble for me.

I had to remove the EVMS package to regain access to my NTFS partition. Use Synaptic or enter the following:

```
sudo apt-get remove evms
```

It also solved the problem of /sbin/udevd consuming all of my CPU resources.

This solved my NTFS mounting problems

---

### Post by spookyct on 2008-01-10
I am having the same problem...  after my gutsy install.

i can get to the folder /media/hdb1, however there is nothign in it.  I tried removing the package above...  and got this...

```
james@james-desktop:~$ sudo apt-get remove evms
[sudo] password for james:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package evms is not installed, so not removed
The following packages were automatically installed and are no longer required:
  liblockdev1 libflac++5c2 liboggflac3 libpoppler1-qt libtdb1 libjack0.100.0-0
  libqt4-qt3support libpostproc0d libsqlite0 libavformat0d libjasper-runtime
  libdb3 libqt4-sql libavcodec0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Please help!:mad:

---

