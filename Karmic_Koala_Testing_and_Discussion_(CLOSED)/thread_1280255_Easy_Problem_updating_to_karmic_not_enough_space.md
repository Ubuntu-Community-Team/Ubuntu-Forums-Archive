---
title: "Easy Problem updating to karmic: not enough space"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Awareness on 2009-10-01
I've got an Asus eee pc 901

It comes with 2 drives: hda (4Gb) and hdb (16Gb)

As recommended, I mounted / in hda and /home in hdb... (I dont even need that much for home anyway)

The thing is, When I tried to update via

```
update-manager -d
```

It says I need 1,700 Gb to upgrade. I unistalled OpenOffice, evolution and all kind of stuff (emptied trash, apt-get clean) but it still says i lack 800 Mb to make the upgrade...

I dont know what else to do... reinstall / in the 16Gb drive?
Can I change the mount point for /share to hdb and move all its content for example?

Any other suggestion? (i dont mind to start over)

---

### Post by running_rabbit07 on 2009-10-01
Back up your info and do a clean install. 

During the upgrade your system will need room for two OSes and plus all of your regular files, while it moves, copies, unpacks, and deletes files and folders.

---

### Post by mac9416 on 2009-10-01
When update-manager does a dist-upgrade, it install a meta-package called "ubuntu-desktop" that depends on a bunch of software that  probably isn't in Netbook Remix by default, resulting in a huge download. It is a really irritating "feature" in my mind, but they must have some reason to do it that way.

The way to get around that is to upgrade using a few other tools.

```
$ sudo sed s/jaunty/karmic/ /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade
```

Good luck!

---

### Post by running_rabbit07 on 2009-10-01
> **mac9416 said:**
> When update-manager does a dist-upgrade, it install a meta-package called "ubuntu-desktop" that depends on a bunch of software that  probably isn't in Netbook Remix by default, resulting in a huge download. It is a really irritating "feature" in my mind, but they must have some reason to do it that way.

The way to get around that is to upgrade using a few other tools.

```
$ sudo sed s/jaunty/karmic/ /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade
```Good luck!
+1 This sounds more productive than doing a clean install.

---

### Post by Awareness on 2009-10-02
> **mac9416 said:**
> When update-manager does a dist-upgrade, it install a meta-package called "ubuntu-desktop" that depends on a bunch of software that  probably isn't in Netbook Remix by default, resulting in a huge download. It is a really irritating "feature" in my mind, but they must have some reason to do it that way.

The way to get around that is to upgrade using a few other tools.

```
$ sudo sed s/jaunty/karmic/ /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade
```

Good luck!

```
$ sudo apt-get dist-upgrade
```

Does nothing. It says I have nothing to upgrade. I have to do 

```
update-manager -d
```

And then it suggests me to upgrade to 9.10

Anyway, after running that sed in sources.list, I tried to 

```
update-manager -d
```

Again. It still says I lack 500 Mb

Maybe that "keryx" from your signature could be useful, Ill give it a try...
Also... Im gonna have this problem always. 4Gb is not enough. Can't I move /share somehow to the other drive?

btw, Thanks for your answers :)

---

### Post by running_rabbit07 on 2009-10-02
Did you copy and paste the whole command into terminal or try it in peices?

---

### Post by slakkie on 2009-10-02
I,

have a look at the pointers in the following thread:

[http://ubuntuforums.org/showthread.php?t=1238309](http://ubuntuforums.org/showthread.php?t=1238309)

* Remove your apt cache
* Remove unneeded kernels

You could also try to upgrade via the alternate CD:

```

# Mount the alternate CD
sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0
gksu "sh /cdrom/cdromupgrade"

```

---

### Post by Awareness on 2009-10-02
> **running_rabbit07 said:**
> Did you copy and paste the whole command into terminal or try it in peices?

I copied the whole command :)

---

### Post by Awareness on 2009-10-02
> **slakkie said:**
> I,

have a look at the pointers in the following thread:

[http://ubuntuforums.org/showthread.php?t=1238309](http://ubuntuforums.org/showthread.php?t=1238309)

* Remove your apt cache
* Remove unneeded kernels

You could also try to upgrade via the alternate CD:

```

# Mount the alternate CD
sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0
gksu "sh /cdrom/cdromupgrade"

```

I followed that thread and did what they say

I removed the kernels and the /var/cache/apt/

I still need 241 Mb :S

---

### Post by running_rabbit07 on 2009-10-02
Probably be easier to do a clean install then. If anyone knows how to get an upgrade going, it would be Slakkie.:wink:

---

### Post by dwinks on 2009-10-02
Do you have a thumb drive?  If so, mount it at /var/cache/apt/archive.

Also, try the following:

```
apt-get clean && apt-get autoclean && apt-get autoremove
```

That will clear out a bit of space.  Mounting the thumb drive at the above path will allow you to download all of the files without them actually taking any of the 4GB of space up.

---

### Post by Awareness on 2009-10-02
> **dwinks said:**
> Do you have a thumb drive?  If so, mount it at /var/cache/apt/archive.

Also, try the following:

```
apt-get clean && apt-get autoclean && apt-get autoremove
```

That will clear out a bit of space.  Mounting the thumb drive at the above path will allow you to download all of the files without them actually taking any of the 4GB of space up.

Thats actually a good idea... I was going to do that, but I think I removed some stuff that I shouldn't and screwed my install... im gonna make a fresh install with 9.04 and then try to upgrade to 9.10 with that

---

### Post by Awareness on 2009-10-03
In the end, i made a fresh 9.04 installation and made a partition to /var... then upgraded without problems ;)

thanks to you all!

:guitar:

---

### Post by arnasd on 2009-10-07
hi,

i get "not enough space on partition" error when trying to update to 9.10 karmic koala.
i have two partitions on my hdd: first is about 50mb (boot partition), second is ~39gb. I am using boot partition only for grub, because i got (grub stage 1.5 error 18 )
> "18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general)." 

i think that upgrade suftware is downloading all packages to first boot partition - how can i change the default download location, and make it use the root partition?

---

### Post by mac9416 on 2009-10-07
> how can i change the default download location, and make it use the root partition? 

I think it should default to the root partition. Try this page explaining how to cache packages in your home partition.
[http://www.ubuntu-fl.org/2009/08/27/hacklet-apt-cache-redirect/](http://www.ubuntu-fl.org/2009/08/27/hacklet-apt-cache-redirect/)

---

