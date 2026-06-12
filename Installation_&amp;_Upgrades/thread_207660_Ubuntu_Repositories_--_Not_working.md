---
title: "Ubuntu Repositories -- Not working?"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by programgeek on 2006-07-02
It seems that when I try to update and refresh my package list through the internet the main ubuntu repositories aren't giving me anything back, and failing.  I can't download updates now.

Is this an isolated incident or can someone fire me over the solution?

Tony Eberly

---

### Post by angkor on 2006-07-02
Please post your /etc/apt/sources.list and the error you get when you try to update.

---

### Post by cacharreo on 2006-07-02
I had same problem updating from Breeze to Dapper. I did modified manually the backed sources.list of Brezze to Dapper and then works fine

---

### Post by programgeek on 2006-07-03
I'm Sorry if I wasn't specific enough.  I didn't mean to frustrate any of you.  I know what it's like. :KS   Your a star!

```

tony@tony-laptop:/etc/apt$ sudo apt-get update
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Ign http://us.archive.ubuntu.com dapper Release
Ign http://us.archive.ubuntu.com dapper/universe Packages
Get:1 ftp://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 ftp://us.archive.ubuntu.com dapper Release.gpg
Err http://us.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 146.137.96.15 80]
Ign ftp://us.archive.ubuntu.com dapper Release.gpg
Get:3 ftp://us.archive.ubuntu.com dapper-updates Release.gpg
Get:4 ftp://security.ubuntu.com dapper-security Release [30.9kB]
Ign ftp://us.archive.ubuntu.com dapper-updates Release.gpg
Get:5 ftp://us.archive.ubuntu.com dapper-backports Release.gpg
Ign ftp://us.archive.ubuntu.com dapper-backports Release.gpg
Get:6 ftp://us.archive.ubuntu.com dapper Release
Get:7 ftp://security.ubuntu.com dapper-security/main Packages [26.4kB]
Ign ftp://us.archive.ubuntu.com dapper Release
Get:8 ftp://us.archive.ubuntu.com dapper-updates Release
Ign ftp://us.archive.ubuntu.com dapper-updates Release
Get:9 ftp://security.ubuntu.com dapper-security/restricted Packages [4253B]
Get:10 ftp://us.archive.ubuntu.com dapper-backports Release
Ign ftp://us.archive.ubuntu.com dapper-backports Release
Get:11 ftp://us.archive.ubuntu.com dapper/main Packages
Get:12 ftp://security.ubuntu.com dapper-security/main Sources [6774B]
Ign ftp://us.archive.ubuntu.com dapper/main Packages
Get:13 ftp://us.archive.ubuntu.com dapper/restricted Packages
Get:14 ftp://security.ubuntu.com dapper-security/restricted Sources [974B]
Ign ftp://us.archive.ubuntu.com dapper/restricted Packages
Get:15 ftp://us.archive.ubuntu.com dapper/main Sources
Get:16 ftp://security.ubuntu.com dapper-security/universe Packages [6042B]
Ign ftp://us.archive.ubuntu.com dapper/main Sources
Get:17 ftp://us.archive.ubuntu.com dapper/restricted Sources
Ign ftp://us.archive.ubuntu.com dapper/restricted Sources
Get:18 ftp://security.ubuntu.com dapper-security/universe Sources [902B]
Get:19 ftp://us.archive.ubuntu.com dapper/universe Sources
Ign ftp://us.archive.ubuntu.com dapper/universe Sources
Get:20 ftp://us.archive.ubuntu.com dapper-updates/main Packages
Ign ftp://us.archive.ubuntu.com dapper-updates/main Packages
Get:21 ftp://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign ftp://us.archive.ubuntu.com dapper-updates/restricted Packages
Get:22 ftp://us.archive.ubuntu.com dapper-updates/main Sources
Ign ftp://us.archive.ubuntu.com dapper-updates/main Sources
Get:23 ftp://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign ftp://us.archive.ubuntu.com dapper-updates/restricted Sources
Get:24 ftp://us.archive.ubuntu.com dapper-backports/main Packages
Ign ftp://us.archive.ubuntu.com dapper-backports/main Packages
Get:25 ftp://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign ftp://us.archive.ubuntu.com dapper-backports/restricted Packages
Get:26 ftp://us.archive.ubuntu.com dapper-backports/universe Packages
Ign ftp://us.archive.ubuntu.com dapper-backports/universe Packages
Get:27 ftp://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign ftp://us.archive.ubuntu.com dapper-backports/multiverse Packages
Get:28 ftp://us.archive.ubuntu.com dapper-backports/main Sources
Ign ftp://us.archive.ubuntu.com dapper-backports/main Sources
Get:29 ftp://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign ftp://us.archive.ubuntu.com dapper-backports/restricted Sources
Get:30 ftp://us.archive.ubuntu.com dapper-backports/universe Sources
Ign ftp://us.archive.ubuntu.com dapper-backports/universe Sources
Get:31 ftp://us.archive.ubuntu.com dapper-backports/multiverse Sources
Ign ftp://us.archive.ubuntu.com dapper-backports/multiverse Sources
Get:32 ftp://us.archive.ubuntu.com dapper/main Packages
Err ftp://us.archive.ubuntu.com dapper/main Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:33 ftp://us.archive.ubuntu.com dapper/restricted Packages
Err ftp://us.archive.ubuntu.com dapper/restricted Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:34 ftp://us.archive.ubuntu.com dapper/main Sources
Err ftp://us.archive.ubuntu.com dapper/main Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:35 ftp://us.archive.ubuntu.com dapper/restricted Sources
Err ftp://us.archive.ubuntu.com dapper/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:36 ftp://us.archive.ubuntu.com dapper/universe Sources
Err ftp://us.archive.ubuntu.com dapper/universe Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:37 ftp://us.archive.ubuntu.com dapper-updates/main Packages
Err ftp://us.archive.ubuntu.com dapper-updates/main Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:38 ftp://us.archive.ubuntu.com dapper-updates/restricted Packages
Err ftp://us.archive.ubuntu.com dapper-updates/restricted Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:39 ftp://us.archive.ubuntu.com dapper-updates/main Sources
Err ftp://us.archive.ubuntu.com dapper-updates/main Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:40 ftp://us.archive.ubuntu.com dapper-updates/restricted Sources
Err ftp://us.archive.ubuntu.com dapper-updates/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:41 ftp://us.archive.ubuntu.com dapper-backports/main Packages
Err ftp://us.archive.ubuntu.com dapper-backports/main Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:42 ftp://us.archive.ubuntu.com dapper-backports/restricted Packages
Err ftp://us.archive.ubuntu.com dapper-backports/restricted Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:43 ftp://us.archive.ubuntu.com dapper-backports/universe Packages
Err ftp://us.archive.ubuntu.com dapper-backports/universe Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:44 ftp://us.archive.ubuntu.com dapper-backports/multiverse Packages
Err ftp://us.archive.ubuntu.com dapper-backports/multiverse Packages
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:45 ftp://us.archive.ubuntu.com dapper-backports/main Sources
Err ftp://us.archive.ubuntu.com dapper-backports/main Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:46 ftp://us.archive.ubuntu.com dapper-backports/restricted Sources
Err ftp://us.archive.ubuntu.com dapper-backports/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:47 ftp://us.archive.ubuntu.com dapper-backports/universe Sources
Err ftp://us.archive.ubuntu.com dapper-backports/universe Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Get:48 ftp://us.archive.ubuntu.com dapper-backports/multiverse Sources
Err ftp://us.archive.ubuntu.com dapper-backports/multiverse Sources
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.1521]
Fetched 76.5kB in 22s (3428B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed [IP: 146.137.96.15 80]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  ' [ IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  '  [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP:146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '  [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file. ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to openfile.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  Unable to fetch file, server said 'Failed to openfile.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file. ' [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '  [IP: 146.137.96.15 21]
Failed to fetch ftp://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Unable to fetch file, server said 'Failed to open file. ' [IP: 146.137.96.15 21]
Reading package lists... 1%
tony@tony-laptop:/etc/apt$

```

It happens on updates and when I try to upgrade too. :O  I've tried it on 2 PC's and still get the same thing.

---

### Post by programgeek on 2006-07-03
Bumpity :KS

---

### Post by ifican on 2006-07-03
For a large majority of us that have had the same problem it was a proxy setting in firefox. I run Kubuntu so i dont know the exact path but I know that mostlikely if you clear the proxy setting all should work fine.

---

### Post by houstonbofh on 2006-07-03
I had this problem a bit ago.  It seems the US mirror was having trouble.  (Of course that was never actually told to anyone...  Sheesh...)  Try substituting another repository.  I used "au" for "us" and it "got better..."  I put it back later, as Australia is a bit slow for daily updates... :D

---

### Post by mercuryman2000 on 2006-07-04
[QUOTE=programgeek]It seems that when I try to update and refresh my package list through the internet the main ubuntu repositories aren't giving me anything back, and failing.  I can't download updates now.

Is this an isolated incident or can someone fire me over the solution?

Tony Eberly[/QUOTE]
I had shipit Kubunu cd's with the same problem.  Downloaded and burned Ubuntu same problem.

Went into /etc/apt and sudo mv apt.conf apt.conf.old

Everthing works fine now!

---

### Post by hankintosh on 2006-07-22
apt-get update stalls on the following IP:

146.137.96.7
146.137.96.15

Switching to au. servers in sources.list resolves the problem.

---

### Post by sound_dezign on 2006-09-05
I have had this problem only when connected to certain networks. aptitude works fine on my home network, whereas at work it fails all the time. This problem only occurs in dapper drake. The fix is to delete the contents of your apt.conf file...

Try editing the following file:
/etc/apt/apt.conf (you will need to be su, i.e. sudo vi /etc/apt/apt.conf)

remove the line (you cannot comment it out, this does not work):
Acquire::http::Proxy "false";

you don't need to, but you can add the line:
APT::Authentication::TrustCDROM "true";

now run
sudo apt-get update
or
open synaptic package manager and click "reload"

Hope this works :mrgreen:

---

