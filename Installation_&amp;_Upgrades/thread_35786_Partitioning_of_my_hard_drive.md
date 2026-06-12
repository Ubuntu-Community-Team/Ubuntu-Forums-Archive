---
title: "Partitioning of my hard drive"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by henriette_holm on 2005-05-20
Hi.
Right now I have a really simple partitioning of my hard drive:

Filesystem            Size    Used   Avail   Use%   Mounted on
/dev/hda5             6,6G  3,3G    2,9G   54%     /
/dev/hda7             8,1G  2,4G    5,4G   31%     /home
"something"          1,2G                                  swap

Since I've gone from “total newbie” to “not quit as newbie” since I did this install I now find myself wondering whether there is any advantages in partitioning the hard drive differently if I'm to do a new installation of Ubuntu.
Hope somebody can give me some advise on this.

Thanks.

---

### Post by Sniffer on 2005-05-20
[QUOTE=henriette_holm]Hi.
Right now I have a really simple partitioning of my hard drive:

Filesystem            Size    Used   Avail   Use%   Mounted on
/dev/hda5             6,6G  3,3G    2,9G   54%     /
/dev/hda7             8,1G  2,4G    5,4G   31%     /home
"something"          1,2G                                  swap

Since I've gone from “total newbie” to “not quit as newbie” since I did this install I now find myself wondering whether there is any advantages in partitioning the hard drive differently if I'm to do a new installation of Ubuntu.
Hope somebody can give me some advise on this.

Thanks.[/QUOTE]

That's precisely (partition scheme) that i do, so  you will not notice any performance gains if you partition more your HDD. And the essential you already have, that's to keep your Home (Data) partition separated from the root one for future upgrades.

My 2 cents
Sniff.

---

### Post by henriette_holm on 2005-05-20
So whats the point when people have separate partitions for /usr, /var etc. ?

---

### Post by skoal on 2005-05-20
[QUOTE=henriette_holm]So whats the point when people have separate partitions for /usr, /var etc. ?[/QUOTE]

It's nice having a separate /usr/local and /opt partition especially.

If you install anything to /usr/local (like most game default installers do), it's a simple matter of mounting that partition on another box instead of reinstalling them again.  Also, if you ever have to reinstall your OS, you'll never lose that information.  The same applies to using a separate /opt partition.  I use /opt for commercial/non-Ubuntu packages.

* I suppose you could just have one huge /home directory instead, creating sym links to binaries and updating PATH, etc.  However, if you run multiple distributions (or even use NFS for mounting *NIX shares), the traditional Unix way is far more flexible.  In the end, it's what works best for your needs at the present.

---

### Post by henriette_holm on 2005-05-20
Ok, so here is a thought: If you have a separate partition for /usr and /opt where you install apps will you then be able to keep them eventhough you reinstall Ubuntu?

Skoal: Could you show me what your partition table looks like?

---

### Post by Sniffer on 2005-05-20
For instance var is recommended to be separated if you run a WebServer.

---

### Post by skoal on 2005-05-21
[QUOTE=henriette_holm]Ok, so here is a thought: If you have a separate partition for /usr and /opt where you install apps will you then be able to keep them eventhough you reinstall Ubuntu?[/QUOTE]

Absolutely.

skoal@morpheus://~ $ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              4883556   2487424   2396132  51% /
tmpfs                   388200         0    388200   0% /dev/shm
/dev/hda1                96312     52668     43644  55% /boot
/dev/hda8             14048332    991708  13056624   8% /data
/dev/hda7               979868    282668    697200  29% /home
/dev/hda5              4883556     32840   4850716   1% /opt
/dev/hda6              4883556   1054884   3828672  22% /usr/local

That's just my setup for one drive dedicated to Ubuntu.  On one other distro drive, I mount /dev/hda5, /dev/hda6 and /dev/hda8 under /opt, /usr/local, and /data, respectively, on the second drive (hdb).  No need fo rmutliple installs or partitions.  If you use NFS, you can do the same thing across a network.

* If I ever need to re-install Ubuntu or replace it with another distro on that drive, I just select to format /dev/hda3 (keeping all the others intact).  NOTE: At least on Ubuntu, the only thing you will need to recreate to get your old apps back is a .desktop entry in /usr/share/applications, or you can just add them with a menu editor and point the command line to /usr/local/bin or /opt/bin.

---

### Post by henriette_holm on 2005-05-26
I've had a look at Skoals partition table and I'm wondering about a few things:

    * /dev/hda1 - /boot

    * /dev/hda2 - ? (Is /dev/hda2 for swap?)

    * /dev/hda3 - /

    * /dev/hda4 - ? (What happend to /dev/hda4? Is that for an extended partition?)

    * /dev/hda5 - /opt

    * /dev/hda6 - /usr/local (Why a separate partition for /usr/local - why not /usr?)

    * /dev/hda7 - /home

    * /dev/hda8 - /data (What's the story with /dev/hda8? What do you use /data for? Well, I suppose it's obvious but why not use /home?)


And the final one: Do you use ext3 for all of them (except swap of course)?

---

