---
title: "Space Reduced"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by FahadMKS on 2011-02-01
Hi,

I have upgraded my Ubuntu from 10.04 LTS to 10.10. Before upgrading, I had about 25 Gb of free space on my computer and now after the upgradation is complete I see a great reduction in the space of my Hard disk.
About 10 Gb space has been cut off. Is this normal and if not, please can anyone help me in getting back the space I had with the 10.04 version.

---

### Post by vanadium on 2011-02-01
Very strange indeed. A clean Ubuntu system does not need more than 4 GB. An upgrade will probably increase disk usage, but that should still be limited.

Try to see where all the disk space went, using the du command or the graphical tool under Applications - Accessories. It might likely hint to another cause of your disk usage.

---

### Post by mörgæs on 2011-02-01
This is one of the reasons why I always do a clean install :-)

You could try **sudo apt-get clean** to see if it frees up some space.

---

### Post by FahadMKS on 2011-02-01
The problem here is when I check with the Disk usage analyzer, it shows as 23.6 Gb free. But when I open up a window, at the bottom, it just shows as 15 Gb free.
Why is this occurring.

I have attached the images on how it is.

---

### Post by matt_symes on 2011-02-01
Hi

Open a terminal and type

```
sudo du -sh /
```

What does that return ?

Kind regards

---

### Post by FahadMKS on 2011-02-01
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo du -sh /
```What does that return ?

Kind regards
The message I get there is 

fahad@fahad-desktop:~$ sudo du -sh /
du: cannot access `/home/fahad/.gvfs': Permission denied

Why is this so? I am logged in as an admin user.
Please help me.

---

### Post by matt_symes on 2011-02-01
Hi

> fahad@fahad-desktop:~$ sudo du -sh /
du: cannot access `/home/fahad/.gvfs': Permission denied

Why is this so? I am logged in as an admin user.

I believe it because it's a FUSE mount point under your user and root cannot see it.

```
mount | grep gvfs
```

This is my output of the command above.

```
gvfs-fuse-daemon on /home/matthew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matthew)
```

You should be able to see it from your user.

```
ls ~/.gvfs
```

Anyways, after the sudo du -sh command it shouild have given you a grand total of disk usage for /.

What did it give you ?

This is mine.

```
matthew@matthew-laptop:~$ sudo du -sh /
[sudo] password for matthew: 
du: cannot access `/home/matthew/.gvfs': Permission denied
45G     /
matthew@matthew-laptop:~$
```

Kind regards

---

### Post by Carson5696 on 2011-02-01
Hello,
When you upgraded ubuntu, ubuntu installed a new swap space (is a portion of a hard disk drive (HDD) that is used for virtual memory) Swap Space can take up 5 to 11 GB. I would recommend that you you first download Remastersys (Takes all of your files and programs and put them on a live ubuntu install disc so you can reinstall ubuntu with you old files and programs.) Then do a clean install with the live CD that you made

---

### Post by vanadium on 2011-02-01
It might be possible indeed that disk usage analyzer lists all space on the entire file system, i.e. including attached storage, whereas a nautilus window lists the free space available on the volume where the directory is located. This makes sense, because the user will not be able to store more data than is available on the current volume.

What is the output of "df -h"? This commands works for each individual volume.

---

### Post by FahadMKS on 2011-02-01
> **matt_symes said:**
> Hi



I believe it because it's a FUSE mount point under your user and root cannot see it.

```
mount | grep gvfs
```This is my output of the command above.

```
gvfs-fuse-daemon on /home/matthew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matthew)
```You should be able to see it from your user.

```
ls ~/.gvfs
```Anyways, after the sudo du -sh command it shouild have given you a grand total of disk usage for /.

What did it give you ?

This is mine.

```
matthew@matthew-laptop:~$ sudo du -sh /
[sudo] password for matthew: 
du: cannot access `/home/matthew/.gvfs': Permission denied
45G     /
matthew@matthew-laptop:~$
```Kind regards
  This is what I got.

fahad@fahad-desktop:~$ sudo du -sh /
du: cannot access `/home/fahad/.gvfs': Permission denied
du: cannot access `/proc/2517/task/2517/fd/3': No such file or directory
du: cannot access `/proc/2517/task/2517/fdinfo/3': No such file or directory
du: cannot access `/proc/2517/fd/3': No such file or directory
du: cannot access `/proc/2517/fdinfo/3': No such file or directory
120G    /

---

### Post by vanadium on 2011-02-01
This indicates your data occupies 120G, information we got already from the screenshot, although we now have it in a more efficient way (only 4 bytes).

---

