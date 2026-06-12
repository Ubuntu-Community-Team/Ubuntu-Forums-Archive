---
title: "update error"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by baracuda on 2008-11-01
I was updating my system using update manager. This time I got the message of:

E: /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb: failed in buffer_write(fd) (10, ret=-1)

There is no message on what to do. 

I tried to rerun the updater but I keep getting this error. What do I do?

---

### Post by stevespo on 2008-11-02
I've seen it several times as well.  We can't really be the only 2 users seeing this problem, can we?

E: /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb: failed in buffer_write(fd) (10, ret=-1)

---

### Post by DougieFresh4U on 2008-11-02
Have you tried terminal?
```
sudo apt-get - install
sudo dpkg --configure -a
```
Just a suggestion.

---

### Post by fshwcrs on 2008-11-03
> **DougieFresh4U said:**
> Have you tried terminal?
```
sudo apt-get - install
sudo dpkg --configure -a
```
Just a suggestion.

> Unpacking replacement linux-image-2.6.24-21-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during [COLOR="Red"]**`./boot**[/COLOR]/System.map-2.6.24-21-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)


I think that might be whats wrong with it? What script can I edit to fix that path?

---

### Post by Kevbert on 2008-11-03
The first command should be
```
sudo apt-get -f install
``` to force a repair of any damaged packages.
It looks like your boot partition is full. Enter
```
cd /boot
ls -l
```
to see all installed kernels. To remove unwanted/unused kernels go to Synaptic and search for linux-image. Then do a complete removal of any kernels that you don't need - the file in each case that you need to get rid of is linux-image-2.6....-generic. Then try the two repair commands and a
```
sudo apt-get update
``` If you have any .bak files in the /boot partition you should remove them as well.

---

### Post by stevespo on 2008-11-03
Thanks very much for the help.  When I installed Ubuntu a few months back, it was recommended that I create a small /boot partition (32MB, I believe).  That was nearly full, which was causing the error.

Can I increase the size with the partition editor, or leave things alone and check du periodically?

Steve

---

### Post by Kevbert on 2008-11-03
Here's a [[COLOR="Red"]link[/COLOR]]("http://sudan.ubuntuforums.com/showthread.php?t=839845") on how to increase your boot partition size.

---

### Post by fshwcrs on 2008-11-04
Thanks! I removed the .bak files and it worked perfectly.

---

