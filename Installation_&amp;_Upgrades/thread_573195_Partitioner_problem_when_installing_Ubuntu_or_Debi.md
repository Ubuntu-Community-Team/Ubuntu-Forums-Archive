---
title: "Partitioner problem when installing Ubuntu or Debian...."
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Artistar on 2007-10-11
I don' know what the hell is going on! :confused:

Here's the situation: Yesterday i installed Debian/Lenny on my Ubuntu partition (using format, and the same swap partition), and few hours later returned Ubuntu on the same partition using Acronis True Image. The i used Win Vista DVD to Fixmbr and Fixboot (remove Debian's GRUB), and took Ubuntu LiveCD to get Ubuntu's Grub boot loader back.
After that everything seemed fine, until this morning when i tried to install a fresh copy of Feisty....

When i use partitioner, it shows me only my whole hard disk, without any partition, and gives me the option to create new partitions by erasing the whole HDD!!
OK, then i tried to install Debian with its netinst installer, and i got the same thing!! Only the whole HDD, and the option to erase it and create new partitions.... Yesterday I had all of my partitions listed in partitioner, but now i don't know what to do.... Manual option takes me back to the list, so there's no way to bypass it.... :mad:

Btw, the BIOS is intacted....

I have 80GB Seagate Barracuda ATA disk and this partitions:

1. Win Vista (15GB)
2. NTFS (20GB)
3. NTFS (25GB)

4. Linux Swap (512MB)
5. Linux Ext3 (15GB)

What's wrong and what shall i do about it?? :(

Thanx in advance.

---

### Post by Pumalite on 2007-10-11
Have to use Vista partitioner to allocated space. Then use Gparted:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to partition the newly allocated space. A good scheme is:
10 Gb for '/'
1 GB /swap
The rest for /home. Then install.

---

### Post by Artistar on 2007-10-11
> **Pumalite said:**
> Have to use Vista partitioner to allocated space. Then use Gparted:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to partition the newly allocated space. A good scheme is:
10 Gb for '/'
1 GB /swap
The rest for /home. Then install.

Hm,but what is the problem? Now I can use both systems (Vista & Feisty), and all of the partitions normally, but they're just not recognized by both partitioners....
I also don't understand, what shall i do with Vista's partitioner? Format Ubuntu's current partition? :confused:

---

### Post by Pumalite on 2007-10-11
You restored Vista MBR. You are trying to install new Feisty. The method I offered was to obviate those problems, since your installation partitioner is giving you a problem. I would also follow this guide:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And give the Alternate CD a go. And, finally, If I were you, I'd wait 7 days and install Gutsy. Feisty support will not last very long.

---

