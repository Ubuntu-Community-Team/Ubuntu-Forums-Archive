---
title: "XUbuntu 12.04, update stop working, can't unpack/open DEB files"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by mbogevik on 2013-09-25
A few day's ago my XUbuntu got problem updating the system.  On last Samba update dpkg-deb give error message when unpacking downloaded DEB updates.  Error message contains only invalid ASCII chars, but later in terminal windows I gets "subprocess dpkg-deb --control returned error exit status 2".  The same message is given on all 7 updates downloaded.

I have tested the DEB archives on a second Linux computer and they all are valid DEB archives and can be opened and unpacked with "Archive manager"

To me it looks like dpkg-deb is damaged in a way that it do not unpack DEB files anymore.  I have located dpkg-deb in folder /usr/bin and replaced it with a "fresh" version from a DEB file downloaded on a second computer (same date and size on file), but with same result.

Also I found that open a DEB file with "Archive manager" do not work either, I get an similar error message

Because of invalid char's I am not able to post complete terminal message but I have picture of error message from "Archive manager".

Really hope anyone has an idea where to look for this fault as for now I am stuck.

Best regard
Morten

[ATTACH=CONFIG]246505[/ATTACH]

---

### Post by mbogevik on 2013-09-26
Must add that between this working and not working the computer startup have executed a HDD boot check and it is possible that that have something to do with this, although lost&found only contains a few very old files.

It is also worth mentioning that update sources are unchanged (Ubuntu main server) and HDD is at 6% and is not full.

---

### Post by mbogevik on 2013-09-26
As I have been many "places" in an effort to fix the problem.  Among other I have tried to use "Synaptic Package Manager", found "dpkg" package and tried to reinstall, only with same error as result.  I then located this package (/var/cache/apt/archives/dpkg_1.16.1.2ubuntu7.1_amd64.deb) unpacked with my Ubuntu 13.04 computer and .tar.gz archive of it.  I then opened this again in XUbuntu, and as first thing I tried to replace the program files from archive and copied them to /usr/bin, 7 different dpkg* programs and "update-alternatives".

And the magic is, after copy of these 8 executable files computer now updates and everything seems to work 100% perfect, at least as much as I have tested.

My Linux server is again in perfect condition :)

---

### Post by mbogevik on 2013-10-11
This turned out a bit ugly as it turned out that my system disk, a OCZ Petrol 64GB SSD, had stability issues related to firmware.  After finally updating SSDs firmware, my XUbuntu 12.04 simply died.  As /home was on a different drive that was not very critical, I now installed XUbuntu 13.10 (beta 2) and SSD seems stable so far....  Only a lot of work, but I needed installation/setup experience anyway.

---

