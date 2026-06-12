---
title: "Lucid: /var/cache/apt/archives problem..."
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by casperl on 2010-05-19
A few releases ago things used to work this way, but seemingly since Jaunty it no longer does seem to work:

**This used to work:** I have several Ubuntu machines to upgrade and limited (and highly expensive) bandwidth available.  In the past I would upgrade/update one machine and copy the contents of /var/cache/apt/archives to the other machines to be upgraded. When updating/upgrading the distro the packages that already exist in /var/cache/apt/archives would not be downloaded from the Internet while utilising the locally cached .deb files, saving time and bandwidth. 

**The Problem: **I have noticed that since 9.10 (and with 10.04) this no longer appears to work.  While the .deb packages may exist in /var/cache/apt/archives, the same packages would be downloaded from the Internet regardless of the same .deb file existing in /var/cache/apt/archives/.

**Question:** What is wrong and how can I restore the functionality present in copying cached packages from machine to machine in order to save bandwidth?

**Why I need this to work:** At work (and I have no control over this...) we are limited to a total bandwidth of 3Gb per month for multiple users.  Needless to say a single upgrade of a recent Ubuntu distro can decimate a large proportion of our monthly available bandwidth.  Upgrading multiple machines is absolutely out of the question if the packages have to be downloaded every time.

**An apt-cache server is not an option:** The option of a local apt-cache server is not feasible  due to the same 3Gb bandwidth constraint.  An apt-cache server requires 15Gb storage per version of Ubuntu and the downloading/upgrading of 15Gb worth of packages for that storage is not an option due to the 3Gb limitation.

Thanks in advance

---

### Post by Ashocka on 2010-05-19
See if this reply helps you
[http://ubuntuforums.org/showpost.php?p=9320942&postcount=2](http://ubuntuforums.org/showpost.php?p=9320942&postcount=2)

I haven't tried it on a ubuntu upgrade.  When I tried it on Linux Mint it (Synaptic) is configured different so I couldn't apply this.

---

### Post by casperl on 2010-05-20
I have not been able to test this (yet) but will do so soon.  

I have added this line to /etc/apt/sources.list

## local cache folder
deb file:///var/cache/apt/archives lucid main restricted lucid-security universe multiverse

I will update this thread with the results.

---

### Post by casperl on 2010-05-20
> See if this reply helps you
> [http://ubuntuforums.org/showpost.php...42&postcount=2](http://ubuntuforums.org/showpost.php...42&postcount=2)

The above fix involves:
> Copy the .debs to /var/cache/apt/archives.
Go to System -> Administration -> Synaptic Package Manager
click the 'origin' button in the bottom left.
click local.

I have done so and a list of "local" packages appear in synaptic.  However this list contains considerable fewer packages than the number of files in /var/cache/apt/archives (about 20% of the list).

The file permissions of all the debs in archives is set to "-rw-r--r--" and the ownership as root | root.

However, "lrwxrwxrwx 1 root root 14 2010-03-13 11:53 archives -> /home/archives" is a symlink pointing to a separate, mounted partition so that I can copy debs before the upgrade / clean install.  Might this have something to do with the problem?

---

