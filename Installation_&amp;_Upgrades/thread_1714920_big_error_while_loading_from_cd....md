---
title: "big error while loading from cd..."
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Rainscape on 2011-03-26
well, I was going to post cause it took a long time to load, I got to the ubuntu logo, and all five dots were red, ut staying that way for a LONG time, but now I gott this error (and please bare with my typing, I'm on my phone, I deleted the patition my WIN7 was on...): 

sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
chroot: can't execute '/usr/sbin/make-ssl-cert': Input/output error
dpkg-divert: failed to read on buffer copy for file copy: Input/output error
In /root/usr/sbin/anacron: File exists
sudo: unknown user: ubuntu
Using CD-ROM mount point /cdrom/
Identifying.. [e6fbe1571743a7752d144a427af01351-2]
Scanning disc for index files..
Found 2 package indexes, 0 sourse indexes, 0 translation indexes and 1 signetures
Found label 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
This disc is called:
'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
Copying package lists...gpgv: Signeture made 3hu Oct 7 16:24:55 2010 UTC using DSA key I'd FBB7545E
gpgv: Good signeture from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disk are:
deb cdrom:[Ubuntu 10.10 _Mavrick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping nonexistent file /cdrom/dists/maverick/main/binary-i386/Packages
W: Skipping nonexistant file /cdrom/dists/maverick/restricted/binary-i386/Packages
dpkg-divert: failed to read on buffer copy for file copy: Input/output error
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
init: Failed to spawn rsyslog main process: unable to execute: Input/output error
init: Failed to spawn network-manager main process: unable to execute: Input/output error
init: avahi-daemon main process (1313) terminated with status 2
[ 1769.615479] end_request: I/O error, dev sr0, sector 667880status lator/etc/acpi/power.sh: 9: CheckUPowerPolicy: not found/etc/acpi/power.sh: 11: pm-powersave: Input/output error        [OK]i
[ 1769.615988] Buffer.....


it keeps saying something about buffering, but my fingers are tired and I've been writing this for about 15-30 mins, if you want to know the rest, I'll think about it...

---

### Post by Quackers on 2011-03-26
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that's ok check the cd for errors by pressing any key at the first purple screen then choose your language and on the next screen choose the error checking option.

---

### Post by Rainscape on 2011-03-26
> **Quackers said:**
> Have you checked the md5sum of the downloaded iso file?

[url]

If that's ok check the cd for errors by pressing any key at the first purple screen then choose your language and on the next screen choose the error checking option.

I'll chack with that when I wake up, thanks for the reply though :)

---

### Post by Quackers on 2011-03-26
Yes, wake up first! :-)

---

### Post by Hedgehog1 on 2011-03-26
> **Quackers said:**
> Yes, wake up first! :-)

Now hang on - I have done some of my best coding half asleep.

Come to think of it, I have done MOST of my coding half asleep.


***The 'Sleeply' Hedge***

:KS

---

### Post by Quackers on 2011-03-26
Hmm, I suspect I've seen some of the results! :wink:  :-)

---

### Post by Rainscape on 2011-03-26
Well, I wrote 2 CD's, and both have 10 errors >.> one I wrote with Daemon Tools, the second one with InfraReader

---

### Post by Quackers on 2011-03-26
Have you tried burning the image at the lowest possible speed?

---

### Post by Rainscape on 2011-03-26
Nope, but I'll try that now

---

### Post by Rainscape on 2011-03-26
> **Quackers said:**
> Have you tried burning the image at the lowest possible speed?
 That gave me 11 errors :S

---

