---
title: "&quot;Could not download all repository indexes&quot;"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by NJC on 2007-09-05
How do I eliminate this error - always after updating program via package manager:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

EDIT: I lost the window that included missing repos ... but 2 of them were CD Rom related.

---

### Post by Pumalite on 2007-09-05
Check your /etc/apt/sources.list. Comment (#) or remove old or obsolete repositories.
Backup first:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
Then:
gksudo /etc/apt/souces.list
Save and exit.

---

### Post by merlinus on 2007-09-05
> 
gksudo /etc/apt/souces.list
should be:

```

gksudo gedit /etc/apt/souces.list

```

Also, delete any lines referring to cd.

-merlin

---

### Post by Pumalite on 2007-09-05
Thank you Merlin; I'm in the Moon as usual.

---

### Post by merlinus on 2007-09-05
No problema.  You will certainly have ample opportunity to return the favor.

:)

-merlin

---

### Post by Pumalite on 2007-09-05
What's 'problema'?.Me speecko no English

---

### Post by NJC on 2007-09-30
I went into sources and deleted the CD lines - but I don't know which are obsolete repositories. :confused: Here's a screenshot of when check repositories:

[IMG]http://i18.photobucket.com/albums/b107/Volvo745/Misc/Screenshot-Downloadingpackageinform.png[/IMG]


And the error I now receive:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of 
network problems. If available an older version of the failed index will be used.
Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

And this is problematic line from above error:
```

http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:[/url] Sub-process gzip returned an error code (1)
```

How to fix!!

---

### Post by Pumalite on 2007-09-30
Post the entire output of:
sudo apt-get update

---

### Post by NJC on 2007-09-30
```
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://security.ubuntu.com dapper-security Release [50.9kB]
Get:6 http://archive.ubuntu.com dapper Release [34.8kB]
Get:7 http://ca.archive.ubuntu.com dapper Release [34.8kB]
Ign http://archive.ubuntu.com dapper/main Packages
Get:8 http://ca.archive.ubuntu.com dapper-updates Release [50.9kB]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Get:9 http://archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:10 http://ca.archive.ubuntu.com dapper/main Sources [255kB]
Get:11 http://archive.ubuntu.com dapper/main Packages [821kB]
90% [11 Packages gzip 0] [10 Sources 133176/255kB 52%]                                                                          4294B/s 28s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/main Packages
  Sub-process gzip returned an error code (1)
Get:12 http://ca.archive.ubuntu.com dapper/restricted Sources [1478B]
Get:13 http://ca.archive.ubuntu.com dapper-updates/main Packages [145kB]
Get:14 http://ca.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:15 http://ca.archive.ubuntu.com dapper-updates/main Sources [50.5kB]
Get:16 http://ca.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Fetched 719kB in 2m28s (4826B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Pumalite on 2007-09-30
You seem to have an old repo in your sources.list

---

### Post by NJC on 2007-10-01
Anything I need to fix?

---

### Post by Pumalite on 2007-10-01
Post your souces.list:
cat /etc/apt/souces.list

---

### Post by NJC on 2007-10-01
```
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univ erse multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by Pumalite on 2007-10-01
Hummm...I don't see anything that might be causing trouble.

---

### Post by NJC on 2007-10-01
Pumalite;

Thanks for your help - I guess I won't worry about it for now.

---

### Post by Pumalite on 2007-10-01
You are welcome. Happy Ubuntuing!

---

