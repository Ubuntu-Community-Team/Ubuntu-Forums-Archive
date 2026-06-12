---
title: "System Size"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by robbik on 2007-12-10
Hi,

I have a couple of days old installation of Ubuntu 7.10 and everything works fine...except!

When I installed it I did a partition roughly to:

/         5GB
/home 500MB
/boot  100MB

I thought this should be enough for my everyday need. But now I suddenly discovered that the root system is almost full. Is that normal?

df -h gives me (some items removed)
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             4.6G  4.4G   53M  99% /
/dev/sda7              92M   33M   55M  38% /boot
/dev/sda9             464M  126M  315M  29% /home

```

I've had several other distros and never experienced such a large need for root partition.

I'm dual-booting with Windows but I have some space available, so I want to do a fresh installation with a larger size for the root before I spend too much time on customizing the system.

Thanks,

[EDIT]I did ```
sudo apt-get clean
``` which reduced the used space to about 74% (3.3G used). What is your recommendation for the root partition?

---

### Post by Pumalite on 2007-12-10
A good size for '/' is about 10 GB

---

### Post by robbik on 2007-12-11
Just as I suspected. 

I had to do a fresh re-install of Ubuntu because my boot partition was too small (couldn't upgrae). Now it seems I have to do another install because the root filesystem is too small.

Guess it would be appreciated if Ubuntu would add some messages or even warning if you try to create too small partitions in the installation process.

But I really like Ubuntu, and it's easy to install so I'll just to a fresh install with larger root partition :)

---

### Post by mozetti on 2007-12-11
You're going to need more than 500 **MB** for your /home partition, too. It's similar to your "My Documents" folder in linux, with the added bonus of storing all your configuration settings for most (if not all) of the programs you install. These will be in hidden files (starting with a "." , ie .thunderbird), but they're in there nonetheless.

---

### Post by Pumalite on 2007-12-11
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by robbik on 2007-12-11
Thanks for your replies.

Actually I have a specific NTFS partition that contains pictures and music. I'm hoping for getting the best of both worlds since I still need to process my digital images in Windows. But I think I will use 1 GB for /home and the rest (about 9BG for /).

I'm actually used to Gentoo were I set up the system specifically for the hardware it was running on, no more and no less. It is a great challange and I learned a lot, but nowadays I unfortunately don't have the time to compile everything and set everything up - and Ubuntu works perfectly.

Cheers,

---

