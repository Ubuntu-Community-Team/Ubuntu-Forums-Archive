---
title: "Upgrading from Hoary"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by DKCO on 2007-10-21
Yeah, I know.  It's an old release and no longer supported.  But  I've tried downloading newer releases (including Gutsy) and For some reason my computer is having a hard time reading the CD.  It may be a burner problem.  I'd order a CD, but I live in the Middle East and it's hard to get CDs or even mail where I live.  Anyhow, that's just the background - here's the issue:

I have an official Hoary CD that works, but is no longer a supported release.  I did some homework and found that there are repositories for older releases if I go to Synaptic>Settings>Repositories and edit my Software Source (there's only one at this point) to look like this:

Type - Binary
URI - [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
Distro - breezy
Sections - main restricted
Comments -

So I went in and did that and when the package info gets updated, I get this message:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences:

[http://old-releases.ubuntu.com/releases/dists/breezy/main/binary-i386/Packages.gz:](http://old-releases.ubuntu.com/releases/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found
[http://old-releases.ubuntu.com/releases/dists/breezy/restricted/binary-i386/Packages.gz:](http://old-releases.ubuntu.com/releases/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found

Any ideas on this?  I'm using an AMD64 machine with about a GB of RAM.  I'm a little new to Linux, so I know the answer might be right in front of my face here.

Thanks, - DKCO

Also - Sorry for the edit.  I just noticed I got this message as well: 

W: Couldn't stat source package list [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/old-releases.ubuntu.com_releases_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/old-releases.ubuntu.com_releases_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Sef on 2007-10-21
> Yeah, I know. It's an old release and no longer supported. But I've tried downloading newer releases (including Gutsy) and For some reason my computer is having a hard time reading the CD.

1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? If not, then possibly the download was bad.

2) Did you burn at 4x or slower?  Higher may cause a bad burn.

3) Did you check the disk for errors?  Instead of installing, go down to check disk.

---

### Post by DKCO on 2007-10-21
I would try those things, but I think the problem is really my burner.  It used to just burn copies that were barely readable.  Now when it burns the disc, the computer still thinks that the CD is blank media even after I burn it.

---

### Post by Sef on 2007-10-21
Ah ok.  Also be sure to burn the download as an iso and not a data file.

---

