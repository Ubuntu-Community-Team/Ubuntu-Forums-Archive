---
title: "Upgrade a very very old version!"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by anthonyhollingsworth on 2010-11-01
Hi, im having some trouble upgrading to the new version of ubuntu.

Ive been away and havent used this machine in a while, Its running 7.04 and Id like to upgrade it!

The update manager wont let me upgrade to 7.10, its says it cant find the release notes.

I suspect Im just so out of date Ive just been left behind.  I'm not too sure what to do with this now, Ive edited the sources.list to look at the out of date stuff:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multi
verse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted univer
se multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted unive
rse multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse

and I did manage one small update, but I still cant upgrade

checking for updates also fails now for some reason :(

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.169 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.169 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.169 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.92.169 80]

any help would be much appreciated!

---

### Post by wilee-nilee on 2010-11-01
Your only option I think and really the safest is to back up your stuff and fresh install a version that is still in release and getting updates.
[http://fridge.ubuntu.com/node/1655](http://fridge.ubuntu.com/node/1655)

Hopefully others may have better options, personally I don't like upgrades, even under the best of circumstances.

---

### Post by davec64 on 2010-11-01
Wilee-nilee's suggestion is probably the safest but an alternative is to upgrade 7.04 to the next LTS version and then again until you get up to date. :)

---

### Post by SaintDanBert on 2010-11-01
You can do whatever you need to get to an LTS.  You can then "upgrade" from one LTS to the next.

If it were me:
1. backup everything
2. clean install Lucid (v10.04 LTS) or the most recent Maverick (v10.10)

I just bought a new SATA 500 GB drive for under $100 USD. If your box is "that olde" you options may vary with EIDE or PATA drives.
Get one and make a clean and fresh install. Install your olde drive into a USB & firewire enclosure for use as backup or archives or scratch pad
... once you get your goodies moved to the new drive.

Bonne chance,
~~~ 0;-Dan

---

### Post by iThinkSo on 2010-11-01
I am new to Unix but was old hand at Dos. Trying to ditch Windows I backed my data up to a 1 terabyte (ntfs) USB drive, which includes a lot of recorded movies and pics. I used a Puppy Linux boot stick to do it because some malware had trashed two Windows systems leaving us with black screens on any attemp to boot. I then installed Ubuntu 7.04 from a CD I had just to get going and presumed I could start to update from there.

I am getting the picture a clean install of Meerkat 10.10 is the way to go (thanks).

However Ubuntu like my wifes Apple Macbook cannot write to the the 1T USB drive. Also files read from the drive are read only and owned by /root. Pupply Linux has no problem because I think it logs in as /root. (Terminal prompt is also #). In Ub I tried 
~$ sudo chmod +wx "Expansion /Drive" from the /media directory but it did not change the general access permision to the drive.

(1) How can I set up access to the 1T ntfs USB drive from Ubuntu so it works as if the drive were owned by me. There are no other users or network security issues. The drive is only plugged in for backup purposes.? (I don't want to reformat the drive)

(2) If I back up some files I downloaded for use on the Ubuntu system on the ntfs USB drive (with Puppy) or say burn to CD and I am the current owner. LIke /Mike - My Machine. After I do a new clean install of Meerkat do I have to repeat the above exercise to get my new user identity to own the drive and the files again?

---

