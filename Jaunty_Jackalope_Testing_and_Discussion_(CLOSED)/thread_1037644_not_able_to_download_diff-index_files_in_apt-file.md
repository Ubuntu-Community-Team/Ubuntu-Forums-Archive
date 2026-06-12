---
title: "not able to download diff-index files in apt-file"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-12
Hi all, 
      I dunno whether some of you guys use apt-file or not. Its a good tool. Here is its description :-


> 
apt-file is a command line tool for searching files contained
in packages for the APT packaging system. 
You can search in which package a file is included or list the 
contents of a package without installing or fetching it.Now I've been using this tool for quite sometime now . The new version which is there has this new feature. 

> 

apt-file (2.2.0) unstable; urgency=low

  * Ship 'diffindex-download' and 'diffindex-rred' for downloading patches
    instead of the full Contents files. Use this for http and ftp in default
    config file (closes: #373589).
  * diffindex-download uses curl with progress meter enabled by default
    (can be changed in apt-file.conf). Closes: #381613
    Therefore always depend on curl and remove dependency on wget.
  * diffindex-download prints some error messages if no connection is possible
    (closes: #357031).
  * Make 'apt-file purge' remove old content files even if the sources.list
    line has been removed in the meantime (closes: #507092).
  * Make tests not require wget or curl during build-time. Thanks James Westby
    (closes: #506554).

 -- Stefan Fritsch <sf@debian.org>  Tue, 06 Jan 2009 16:59:04 +0100
Now a package called curl needs to be installed (that is a good package in itself but that's for another post I guess) 

anyways, 

what its doing is its unable to download the diff-index files. I have filed a bug for the same [lpbug]316155[/lpbug]

Any comments or suggestions to the same are welcome.

---

