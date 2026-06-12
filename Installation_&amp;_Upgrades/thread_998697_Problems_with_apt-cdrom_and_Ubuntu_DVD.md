---
title: "Problems with apt-cdrom and Ubuntu DVD"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Tomás Ó hÉilidhe on 2008-12-01
I have the Ubuntu DVD, version 8.10. I want to use the repositories on the DVD instead of downloading everything from the internet.

Here's what I typed:

```

apt-cdrom add

```

And here's what I got:

```

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [ee77e034f56ca605d772814f91bb5d82-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)'
This disc is called: 
'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)'
Copying package lists...gpgv: Signature made Thu 30 Oct 2008 09:25:10 AM ICT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
[COLOR="Red"]W: Skipping non-exisiting file /cdrom/dists/intrepid/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/intrepid/main/debian-installer/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/intrepid/restricted/binary-i386/Packages[/COLOR]

```

Is there something wrong? See where it says that it can't find "Packages", well I navigated to the directory where it's supposed to be and I found "Packages.tgz" but no plain "Packages". So something tells me that if I unpacked Packages.tgz, it would work properly. But I thought the whole point was to be able to use the DVD as a repository?

---

### Post by Tomás Ó hÉilidhe on 2008-12-01
bump bump bump

---

