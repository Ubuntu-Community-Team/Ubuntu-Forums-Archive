---
title: "Problem with network automated installation"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by Zrc on 2010-04-12
I'm trying to configure an unattended network installation using Ubuntu Server 8.04LTS to install an Ubuntu Alternate 9.10 client. Preseeding, TFTP, DHCP and this works fine, but process always needs human intervention because of a debootstrap warning. User Nimdae described the same problem a few months ago but nobody answered him.

Nimdae wrote:
[I]
[COLOR=Gray]I use netboot installs inside my network because it makes things easier and faster (no CDs to maintain). I loaded up the karmic alternative ISO and created the appropriate configs, tftp repo, and http repo for karmic and discovered there appears to be a problem with the ISO build, possibly. In this directory:

/dists/karmic/restricted/binary-i386

There are two files:

-r--r--r-- 1 root root  20 2009-09-29 06:46 Packages.gz
-r--r--r-- 1 root root 100 2009-09-29 06:45 Release

I ran into this warning when attempting install:

Warning:
http://<address>/<path to>/dists/karmic/restricted/binary-i386/Packages was corrupt

When I compared the Packages.gz to the one from jaunty in the same location, it is considerably larger:

-r--r--r-- 1 root root 1786 2009-04-20 09:02 Packages.gz

The Packages.gz in karmic is a valid gzip file, and extracts to an empty Packages file.[/COLOR]        [/I]        [COLOR=Gray]
[/COLOR] 
I've checked also Packages.gz and it seems is empty but ok.

Any idea?

---

### Post by CVirus on 2010-04-14
Me and my team are facing the exact same problem with amd64 !

---

### Post by CVirus on 2010-04-14
Found the solution cd dists/karmic/restricted/binary-amd64/ && gunzip Packages.gz .. Now the error is gone. Don't forget to adjust to i386 instead of amd64.

---

### Post by Zrc on 2010-04-19
> **CVirus said:**
> Found the solution cd dists/karmic/restricted/binary-amd64/ && gunzip Packages.gz .. Now the error is gone. Don't forget to adjust to i386 instead of amd64.

I'm trying an automated installation and need to avoid any human intervention. Have you unzipped the Packages.gz package into the server's repository folder? Can you specify which is exactly the solution you have found?

Ok, that solved my error too!

---

### Post by P1STOL on 2010-08-26
> **CVirus said:**
> Found the solution cd dists/karmic/restricted/binary-amd64/ && gunzip Packages.gz .. Now the error is gone. Don't forget to adjust to i386 instead of amd64.

So this is more of a 'work around' as opposed to a 'solution' and kind of takes the automation out of this process.

I'm mounting an ISO as I don't want to replicate it's contents on the local file system (nor should I have to) - making that path read-only.

---

