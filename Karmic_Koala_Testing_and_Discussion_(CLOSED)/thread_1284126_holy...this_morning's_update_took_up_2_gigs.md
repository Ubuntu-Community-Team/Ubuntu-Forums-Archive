---
title: "holy...this morning's update took up 2 gigs"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-10-06
updated in synaptic, first it says the update is going to take 500 mb, but after the update, the diskspace dropped 2 gigs.
o.o
consider this as a warning for those who have low disk spaces left...

update:
anyone who have this "huge" update might want to check this thread and read through it.
[http://ubuntuforums.org/showthread.php?t=1284203](http://ubuntuforums.org/showthread.php?t=1284203)

---

### Post by VMC on 2009-10-06
Have you been updating daily or is this an older alpha you installed. I've updated today and it was minimal MB's.

---

### Post by Vanishing on 2009-10-06
> **VMC said:**
> Have you been updating daily or is this an older alpha you installed. I've updated today and it was minimal MB's.

i update everyday(actually everytime i see and update, and i check very frequently).:lolflag:
you didnt get those updates?
weird o.o
im using the main server, which server are you using?

---

### Post by drs305 on 2009-10-06
Also don't forget you can remove the downloaded packages after the update to free up some of the space:
```

sudo apt-get clean

```

---

### Post by slakkie on 2009-10-06
I went from 5.x GB used to 4.88 GB in use on my root..

---

### Post by DougieFresh4U on 2009-10-06
I updated last evening and now it only has this for me:
[B]```
The following packages will be upgraded:
  aptdaemon binutils coreutils evolution-couchdb gnome-bluetooth 
  gstreamer0.10-ffmpeg gstreamer0.10-tools libgnome-bluetooth7 
  libgstreamer0.10-0 locales os-prober pm-utils python-aptdaemon 
  python-aptdaemon-gtk python-gst0.10 software-center tomboy 
17 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 11.3MB of archives. After unpacking 77.8kB will be freed.
```[/B]

---

### Post by jms-ubuntu-en on 2009-10-06
My /usr ran out of disk space during latest grub update (grub_0.97-29ubuntu57). Following is 'ls -lSr' during installation phase "Unpacking replacement grub ...":
```
---------- 1 root root  87470080 2009-10-06 18:28 reiserfs_stage1_5.dpkg-new
-rw-r--r-- 1 root root 134504696 2009-10-06 13:01 minix_stage1_5
-rw-r--r-- 1 root root 134504696 2009-10-06 13:01 jfs_stage1_5
-rw-r--r-- 1 root root 134504696 2009-10-06 13:01 e2fs_stage1_5
-rw-r--r-- 1 root root 268959664 2009-10-06 13:01 stage2
-rw-r--r-- 1 root root 268960688 2009-10-06 13:01 stage2_eltorito
```

---

### Post by Leighman on 2009-10-06
Yep, I've now got a 540MB Grub, and about 20MB of space left :/

---

### Post by other guy on 2009-10-06
> **Leighman said:**
> Yep, I've now got a 540MB Grub, and about 20MB of space left :/


I checked Boabab. I still have a relatively small boot folder. Well under 15megs with 8 items in the folder. Grub is 3megs of it, with 127 items.

My /usr folder is getting plump at 2.2gigs. Outside of my /home  and additional drives. The /usr is the largest folder on my system.

I like the Boabab visual disk tool. Makes it really easy to see what is on the disk and find out where bloat is. Plus it just looks cool.

---

### Post by Regenweald on 2009-10-06
```

The following NEW packages will be installed:
  linux-headers-2.6.31-12{a} linux-headers-2.6.31-12-generic{a} 
  linux-image-2.6.31-12-generic{a} 
The following packages will be upgraded:
  aptdaemon binutils chromium-browser coreutils gparted grub 
  gstreamer0.10-ffmpeg gtk2-engines-pixbuf libatspi1.0-0 libgail-common 
  libgail18 libgnome-bluetooth7 libgstreamer0.10-0 libgtk2.0-0 libnetpbm10 
  libnm-glib2 libnm-util1 linux-generic linux-headers-generic 
  linux-image-generic linux-libc-dev locales modemmanager netpbm 
  network-manager network-manager-gnome os-prober pm-utils python-aptdaemon 
  python-gst0.10 wget 
The following packages are RECOMMENDED but will NOT be installed:
  dmraid radeontool 
31 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 69.2MB of archives. After unpacking 734MB will be used.
Do you want to continue? [Y/n/?] y

```

Kind of big :)

Update:
```

The following packages will be upgraded:
  aspell-en binutils capplets-data gettext-base gnome-control-center grub 
  hdparm hunspell-en-us libgnome-window-settings1 pm-utils shared-mime-info 
The following packages are RECOMMENDED but will NOT be installed:
  evolution-data-server gnome-user-guide radeontool screen-resolution-extra 
11 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,534kB of archives. After unpacking 538MB will be freed.
Do you want to continue? [Y/n/?] y

```

---

### Post by fifth on 2009-10-06
Well not having updated for few days ;)

```
403 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 569MB of archives.
After this operation, 710MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

---

### Post by Vanishing on 2009-10-06
it seems that everybodies' sizes are different..
had to gpart to increase the root partition, now its at 22 gig free.

is it a problem with grub?

---

### Post by VMC on 2009-10-06
In a related [thread]("http://ubuntuforums.org/showthread.php?t=1284203") someone has opened a bug report.

---

