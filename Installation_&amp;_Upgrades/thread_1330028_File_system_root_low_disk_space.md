---
title: "File system root low disk space"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by prickee on 2009-11-18
I just did a dual boot install of win 7 and ubuntu 9.10.  My ubuntu install went off without a hitch until I started installing my normal programs.  I ran into this error.  During install here were my partitions.  / 10G /boot 64M and Swap 6G /home for rest of space.  When I hit examine it's shown on 2nd screen shot.  All help is appreciated.  Btw I'm not really liking the fact that I lost my custom login/logout sound ability and I cant switch my login screen to another theme....not liking 9.10 right now.....:(

---

### Post by tommcd on 2009-11-18
Can you post the output of these commands:
```

sudo du -csh /*
sudo du -csh /root/*
sudo du -csh /media/*
sudo ls -a /root/

```
The command **du** is for disk usage. 
What do you have in your /media directory? It looks like /media is taking up most of the space.
Have you been deleting stuff as root in nautilus by hitting ALT + F2 and running "gksudo nautilus". Or have you enabled the root account and are running as root?

---

### Post by prickee on 2009-11-18
I have not enabled root account and I'm not sure if it's necessary but I will enable it if it helps this problem.

Ok here is the results requested:

[COLOR="Red"]$ sudo du -csh /*[/COLOR]
 
5.4M	/bin
17M	/boot
0	/cdrom
760K	/dev
17M	/etc
du: cannot access `/home/marcus/.gvfs': Permission denied
3.0G	/home
4.0K	/index.html~
0	/initrd.img
127M	/lib
16K	/lost+found
72G	/media
4.0K	/mnt
369M	/opt
12K	/outputs.html~
du: cannot access `/proc/5213/task/5213/fd/3': No such file or directory
du: cannot access `/proc/5213/task/5213/fdinfo/3': No such file or directory
du: cannot access `/proc/5213/fd/3': No such file or directory
du: cannot access `/proc/5213/fdinfo/3': No such file or directory
0	/proc
860K	/root
12M	/sbin
4.0K	/selinux
200K	/srv
0	/sys
4.6M	/tmp
7.0G	/usr
675M	/var
0	/vmlinuz
83G	total

[COLOR="red"]sudo du -csh /root/*[/COLOR]
du: cannot access `/root/*': No such file or directory
0	total

[COLOR="red"]$ sudo du -csh /media/*[/COLOR]
 
0	/media/cdrom
4.0K	/media/cdrom0
4.0K	/media/cdrom1
0	/media/floppy
4.0K	/media/floppy0
72G	/media/Strorage
72G	total

[COLOR="red"]$ sudo ls -a /root/[/COLOR]

.	       .bashrc	 .esd_auth  .gnome2_private  .pulse-cookie	  .wapi
..	       .cache	 .gconf     .gstreamer-0.10  .recently-used.xbel
.aptitude      .dbus	 .gconfd    .profile	     .synaptic
.bash_history  .debtags  .gnome2    .pulse	     .tvtime

---

### Post by tommcd on 2009-11-19
> **prickee said:**
> I have not enabled root account and I'm not sure if it's necessary but I will enable it if it helps this problem. 
Ok, good. I was just checking. Don't enable the root account.
> **prickee said:**
> 
3.0G	/home
7.0G	/usr
675M	/var

Ok, so /home is on a separate partition, is that correct? If /home is on a separate partition, then we can rule that out as a problem.
Your /usr is 7GB. This seems to be quite large, since you said in your first post that when you installed Ubuntu you made the root partition 10GB. I think this is your problem.
All program binaries, libs, and files get installed to /usr. Do you have any big programs like 3D games installed on your system? If so, then you may need to remove some programs to free up some space.
Post the output of:
```

sudo du -csh /usr/*

``` 
and
```

sudo du -csh /usr/local/*

``` 
Your can free up a bit of space in /var by running:
```
sudo apt-get autoclean
```
This will remove old stored package files that can not be downloaded any more (i.e., old versions of packages that have been updated).
You can free up more space in /var with:
```
sudo apt-get clean
```
This will remove all stored package files. This means that if you ever want to reinstall any of your programs apt will have to download them again from the Ubuntu repos. This is not a problem though. However, if you have a slow internet connection and it takes you a while to download stuff from the repos then you may not want to do that.

---

### Post by prickee on 2009-11-19
I have 250G partition just for linux so if /10G partition isn't efficient what is??? I hate to re-install.  I have used sudo apt-get autoremove & autoclean usually after fresh install.

Here are the post:

[COLOR="Red"]$ sudo du -csh /usr/*[/COLOR]
 
328M	/usr/bin
2.8M	/usr/games
46M	/usr/include
2.4G	/usr/lib
92K	/usr/lib64
1.4M	/usr/local
12K	/usr/man
34M	/usr/sbin
4.2G	/usr/share
78M	/usr/src
148K	/usr/X11R6
7.0G	total

[COLOR="Red"]$ sudo du -csh /usr/local/*[/COLOR]
 
4.0K	/usr/local/bin
4.0K	/usr/local/etc
4.0K	/usr/local/games
4.0K	/usr/local/include
44K	/usr/local/lib
0	/usr/local/man
4.0K	/usr/local/sbin
1.4M	/usr/local/share
4.0K	/usr/local/src
1.4M	total

---

### Post by tommcd on 2009-11-20
> **prickee said:**
> I have 250G partition just for linux so if /10G partition isn't efficient what is??? 

2.4G	/usr/lib
4.2G	/usr/share

So it looks like you don't have any big games in /usr/games or /usr/local/games. I don't know why your /usr/lib and /usr/share are so big. My entire root partition is only 3.1GB.
 I did not think it would be possible to fill a 10GB root partition unless you had a lot of games on the system. Apparently you have managed to do it though. You must have a lot of stuff on your system.
I would think you would need at least 15GB for root. If you decide to add a lot more stuff then make it 20GB.
You can try using a GParted or Parted Magic live CD to shrink one of the adjacent partitions and grow your root partition into the newly created unallocated space. Consult the documentation if you are unfamiliar with this:
[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
GParted from the Ubuntu live CD could probably do this as well.

---

