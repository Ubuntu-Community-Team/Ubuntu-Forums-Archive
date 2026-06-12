---
title: "Updating 12.04 to the Upgrade 12.10"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by tsunalugi on 2013-10-26
My Update Manager downloaded 189 update packages which are not installing. Primarily it resolved to the codex of letters which is usually resolved with the 'q' button. Such resolved to a highlighted 'END' this time. Posteri pushing the "END" key, it said 'Waiting for Data', though did not install. Now the Update Manager reads it installed 189 packages, though the 'Check' command button resolves to static 'Waiting', similarly does the 'Install' command button.

Your assistance is greatly appreciated.

:)

---

### Post by Bashing-om on 2013-10-26
tsunalugi; Hi !

What results from terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
seeing what the package manager relates.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by tsunalugi on 2013-11-01
> sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

sudo apt-get upgrade
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-ca i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-da i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-de i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-el i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-en i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-es i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-fi i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-fr i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-gd i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-hr i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-hu i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-it i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-ja i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-nl i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-pt i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-sl i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-sv i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-uk i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security/main firefox-locale-zh-hans i386 24.0+build1-0ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.156 80]
Fetched 146 MB in 27min 47s (87.7 kB/s)                                        
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-ca_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-ca_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-da_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-da_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-de_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-de_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-el_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-el_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-es_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-es_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-fi_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-fi_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-fr_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-fr_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-gd_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-gd_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-hr_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-hr_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-hu_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-hu_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-it_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-it_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-ja_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-ja_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-nl_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-nl_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-pt_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-pt_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-sl_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-sl_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-sv_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-sv_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-uk_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-uk_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-zh-hans_24.0+build1-0ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?> 

---

### Post by Bashing-om on 2013-11-01
tsunalugi; Hey ,

Are you running a 32 bit operating system ?
Post back the output of terminal code:
```

unmae -a

```
Looks like all the errors are from Mozilla's web site, recon the server is down ?
post pack:
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```
And I will see what I can find.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by tsunalugi on 2013-11-02
Thanks Bashing-om 

uname -a
Linux Teine-Laitalum 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux

cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     2	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     6	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise restricted main multiverse universe #Added by software-properties
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    11	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted main multiverse universe #Added by software-properties
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    17	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    18	
    19	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20	## team, and may not be under a free licence. Please satisfy yourself as to 
    21	## your rights to use the software. Also, please note that software in 
    22	## multiverse WILL NOT receive any review or updates from the Ubuntu
    23	## security team.
    24	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    25	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    26	
    27	## Uncomment the following two lines to add software from the 'backports'
    28	## repository.
    29	## N.B. software from this repository may not have been tested as
    30	## extensively as that contained in the main release, although it includes
    31	## newer versions of some applications which may provide useful features.
    32	## Also, please note that software in backports WILL NOT receive any review
    33	## or updates from the Ubuntu security team.
    34	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    35	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    36	
    37	## Uncomment the following two lines to add software from Canonical's
    38	## 'partner' repository.
    39	## This software is not part of Ubuntu, but is offered by Canonical and the
    40	## respective vendors as a service to Ubuntu users.
    41	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
    42	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
    43	
    44	## This software is not part of Ubuntu, but is offered by third-party
    45	## developers who want to ship their latest software.
    46	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    47	# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    48	
    49	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    50	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
    51	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    52	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    53	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe
goaw@Teine-Laitalum:~$ ls -la /etc/apt/sources.list.d
total 76
drwxr-xr-x 2 root root 4096 Oct 27 05:57 .
drwxr-xr-x 6 root root 4096 Nov  2 05:17 ..
-rw-r--r-- 1 root root   49 Oct 27 05:57 dropbox.list
-rw-r--r-- 1 root root   47 Oct 14  2011 dropbox.list.distUpgrade
-rw-r--r-- 1 root root   49 Oct 27 05:57 dropbox.list.save
-rw-r--r-- 1 root root  158 Oct 27 05:57 hydr0g3n-qbittorrent-stable-precise.list
-rw-r--r-- 1 root root  158 Oct 27 05:57 hydr0g3n-qbittorrent-stable-precise.list.save
-rw-r--r-- 1 root root  156 Oct 27 05:57 hydr0g3n-qbittorrent-trunk-precise.list
-rw-r--r-- 1 root root  200 Oct 27 05:57 jconti-gnome3-oneiric.list
-rw-r--r-- 1 root root  130 May 20  2012 jconti-gnome3-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  200 Oct 27 05:57 jconti-gnome3-oneiric.list.save
-rw-r--r-- 1 root root  256 Oct 27 05:57 spring-ppa-natty.list
-rw-r--r-- 1 root root  190 May 20  2012 spring-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root  256 Oct 27 05:57 spring-ppa-natty.list.save
-rw-r--r-- 1 root root  150 Oct 27 05:57 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  150 Oct 27 05:57 ubuntu-x-swat-x-updates-precise.list.save
-rw-r--r-- 1 root root  210 Oct 27 05:57 webupd8team-gnome3-oneiric.list
-rw-r--r-- 1 root root  140 May 20  2012 webupd8team-gnome3-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  210 Oct 27 05:57 webupd8team-gnome3-oneiric.list.save

I appreciate your help greatly. :)

---

### Post by Bashing-om on 2013-11-02
tsunalugi; Hey ;

Are you comfortable editing system files ? 
I presently do not know the source of the "404 Not Found [IP: 91.189.92.156 80]" errors. But for sure we need to clean up your source list files in both the /etc/apt/sources file and in the /etc/apt/sources.list.d directory. Getting rid of the references to repositories that no longer exit (obsolete).
For starters.. make a backup - standard operating procedure anytime a file is edited for any reason - of the current /etc/apt/source.list file:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak

```

Now fire up the text editor and make some changes.
```

gksudo gedit /etc/apt/sources.list 

```
comment out lines 34 and 35 -place a "#" at the start of the line,. That makes that line not to be parsed when the file is executed. As the maverick archive is no longer maintained - End Of Life.

Lines 41 and 42 .. comment out .. same reasons .. maverick is no longer in existence
Save the file and exit back to the desk top.

Now I am also not comfortable seeing oneric and natty in the 3rd party source directory. Before removal of those sources .. show me what they are:
```

cat /etc/apt/sources.list.d/jconti-gnome3-oneiric.list
cat /etc/apt/sources.list.d/jconti-gnome3-oneiric.list.distUpgrade
cat /etc/apt/sources.list.d/spring-ppa-natty.list
cat /etc/apt/sources.list.d/spring-ppa-natty.list.distUpgrade
cat /etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list
cat /etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list.distUpgrade

```

Unrelated but, If you do not compile and access source code for any reason,, you can gain a lot of speed increase in the update/upgrade process by eliminating all instances of - comment out - "deb-src"  within the main /etc/apt/sources.list file. As depicted currently in line 47.

I will look and see where we stand and advise further.

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

