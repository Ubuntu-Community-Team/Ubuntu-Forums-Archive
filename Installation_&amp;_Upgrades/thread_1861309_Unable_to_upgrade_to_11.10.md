---
title: "Unable to upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by euphgeek on 2011-10-15
I tried to upgrade to 11.10 today.  When I clicked the "Upgrade Now" button in the Update Manager, it told me I needed something like 4 GB available on my / partition and I only have a little less than 2.  That's fine, I have other partitions with plenty of space on them.  I decided to download a .iso, mount it and do a CD upgrade.

I added the ISO file successfully using "apt-cdrom add" and tried again, using do-release-upgrade.  I got back the following errors and 11.10 refused to install:

```
W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release 
amd64 (20111012)/dists/oneiric/Release Unable to find expected entry 
'restricted/binary-i386/Packages' in Release file (Wrong sources.list 
entry or malformed file) 
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release 
amd64 (20111012)/dists/oneiric/main/binary-i386/Packages Please use 
apt-cdrom to make this CD-ROM recognized by APT. apt-get update 
cannot be used to add new CD-ROMs 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 

```

I am using the 64-bit version of Ubuntu 11.04 currently.  I downloaded ubuntu-11.10-desktop-amd64.iso from ubuntu.com.  Does anyone have any idea for what's going wrong or what I can do to upgrade my current system?

---

### Post by euphgeek on 2011-10-15
I've decided to just uninstall several packages that I don't need and I'm able to install the upgrade now.  But if anyone has any insight into why I couldn't use the .iso file to upgrade, I'd like to know that, too.

---

### Post by 23dornot23d on 2011-10-15
The space needs to be free in the root directory signified by /

if there is not enough room in it then the partition for it needs expanding or files need to
be removed ..... but seeing as most are needed system files ......

The best way is to always create your / root partiition a reasonable size when first installing Linux .....

20 Gig is usually quite adequate ...... but some of mine especially after lots of upgrades
are bigger ...... 40 Gig to 60 Gig ...... should cover most users for a long long time.

there are tools to help you clean up a little too .....

apt-get clean (removes the old compressed packages it uses to upgrade with

bleachbit (this program has a lot of things already set up in it to help you tidy your system up )

hope this helps in some way ...... ;)

---

### Post by euphgeek on 2011-10-15
Yeah, I ended up uninstalling a bunch of debug packages, some compiler packages and a couple of games.  I only allocated 12GB for my / directory.  It's worked for every upgrade in the past.  I just don't know why I couldn't upgrade using the .iso file.

---

