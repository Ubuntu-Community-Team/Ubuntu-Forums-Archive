---
title: "Update Manager Broken"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by lightnin on 2010-12-24
Hi all

I am wanting to upgrade over the holidays

I am using 9.04, and want to upgrade to the latest .

I have had a problem with my upgrade manager for a while, but just ignored it.

I get this error


> 
Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

I think I tried a game emulator a while ago, and the upgrade link is now broken .. but it could be more (I think a lot more) than that.

So ... where do I (we :-)  ) start ?

Thanks 

Rich

---

### Post by Rubi1200 on 2010-12-24
You are most likely receiving this error because 9.04 has already reached its EOL (end of life), meaning that it is no longer supported with updates.

I recommend you backup all important data and do a fresh install of 10.04 which is an LTS (long term support) release.

It has updates for the Desktop version until 2013.

Release notes:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by lightnin on 2010-12-24
Thank you

I want to keep all my desktop and aplications and setting / passwords for bank accounts online etc etc

Last time, I just backed up my Home directory, and then copied it onto my new install ... is this still the correct way to do it ?

Thanks

Rich

---

### Post by lightnin on 2010-12-25
Bump :D

and Merry Christmas everyone :KS

---

### Post by dino99 on 2010-12-25
**** I want to keep all my desktop and aplications and setting / passwords for bank accounts online etc etc ***********

as long as you have a separate /home, your data & settings are safe :)

clear the cache: sudo rm /var/cache/apt/archives/*
open synaptic and
 uncheck ALL the third parties (ppa, ...)
 and change the release name, then update

note:
you can only dist-upgrade from LTS to LTS, or from Previous to Next

the other way is to install from scratch (often a good idea), just dont format /home
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by lightnin on 2010-12-25
Synaptic is unavailable to me. I think because of the same error.

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.



I think I need to fix the error, before I can upgrade.

I think if I just copy my Home folder to a fresh install, it will copy this error too ???

What do you think ?

---

### Post by AbeJarano on 2010-12-25
try
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade


If that don't work why not just remove the mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_di sts_jaunty_multiverse_binary-amd64_Packages in /var/lib/apt/lists/

---

### Post by sikander3786 on 2010-12-25
Remove the offensive list file and it would be automatically recreated once you run apt-get update.

Applications > Accessories > Terminal:
```
sudo rm /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_di sts_jaunty_multiverse_binary-amd64_Packages
```

```
sudo apt-get update
```

---

### Post by lightnin on 2010-12-25
> **sikander3786 said:**
> Remove the offensive list file and it would be automatically recreated once you run apt-get update.

Applications > Accessories > Terminal:
```
sudo rm /var/lib/apt/lists/mirror.ox.ac.uk_sites_archive.ubuntu.com_ubuntu_di sts_jaunty_multiverse_binary-amd64_Packages
```

```
sudo apt-get update
```

Thanks ...

I got

> W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by sikander3786 on 2010-12-25
Go to System > Administration > Software Sources and disable the CD-ROM.

**Reboot** and try apt-get again. It is supposed to return a 404 error as your are running Jaunty but if it still returns the lock /var/lib/dpkg/lock error, try this.

```
sudo rm /var/lib/dpkg/lock
```

Here is how you can still use repositories on your Jaunty install.

[http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

But, it is strongly reommended that you either do a clean install or upgrade it to a current version.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by lightnin on 2010-12-25
some success

After Sudo RM ..... and a couple of files, I can now get synaptic up.

I'll have a play .. :D

---

### Post by lightnin on 2010-12-25
more success ...

Update manager now working (and updating)

Thanks everyone :-)

I'll see if I can upgrade , after the update

---

### Post by lightnin on 2010-12-25
so , how do I get rid of this ...


> Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


If I close that window, it checks for updates.

It says I am 501 days old on my pakage updates

---

### Post by lightnin on 2010-12-25
ok ... I cliked and got rid of the CDROM error.

I am up to date as far as I can see, but there is not icon/button to upgrade ???

---

### Post by lightnin on 2010-12-26
ok, I found this command

> update-manager -d

makes the upgrade option appear.

I now dont have enough space on my partition to upgrade.

So ... I'll mark this one a solved, and see how to alter the partion size elsewhere.

Many thanks for all your help
Merry Christmas / Happy Holidays :)

---

### Post by lightnin on 2010-12-26
another update ...

I have successfully upgraded from 9.04 to 9.10

I will now try to get to 10.04

:D

---

### Post by lightnin on 2010-12-26
upgrade complete .. I'm now 10.04:D

10.10 , here I come ...

---

### Post by lightnin on 2010-12-27
10.10 loaded

It ran out of space and messed up a bit, but I resized the partition and it recovered ok.

Thats me done for tonight , it's nearly 4am

night all :-)



Edit >-  It would help if I press "submit" LOL

---

