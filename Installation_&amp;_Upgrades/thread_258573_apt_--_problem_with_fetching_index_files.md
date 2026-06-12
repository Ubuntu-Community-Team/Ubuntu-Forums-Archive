---
title: "apt -- problem with fetching index files"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by szopa on 2006-09-16
Hi,

I just moved from Poland to Belgium and suddenly apt-get update has started returning errors. That is:
```

Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:3 http://pl.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:5 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:6 http://pl.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:7 http://pl.archive.ubuntu.com dapper Release [34.8kB]
Get:8 http://archive.ubuntu.com dapper Release [34.8kB]
Get:9 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://security.ubuntu.com dapper-security/main Packages
Get:10 http://pl.archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Get:11 http://archive.ubuntu.com dapper/restricted Packages [4571B]
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Get:12 http://archive.ubuntu.com dapper/universe Packages [2458kB]
9% [9 Release gpgv 30903] [Connecting to pl.archive.ubuntu.com (153.19.251.225)] [12 Packages 74158/2458kB 3%]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com dapper/restricted Packages
  Sub-process bzip2 returned an error code (2)
Ign http://pl.archive.ubuntu.com dapper/main Packages
Get:13 http://pl.archive.ubuntu.com dapper/restricted Packages [4571B]
12% [Connecting to pl.archive.ubuntu.com (153.19.251.225)] [12 Packages 161758/2458kB 6%]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://pl.archive.ubuntu.com dapper/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:14 http://pl.archive.ubuntu.com dapper/universe Packages [2458kB]
Get:15 http://archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Ign http://archive.ubuntu.com dapper/multiverse Packages
Get:16 http://archive.ubuntu.com dapper-updates/main Packages [71.4kB]
Get:17 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Get:18 http://archive.ubuntu.com dapper-updates/universe Packages [15.4kB]
Get:19 http://archive.ubuntu.com dapper-updates/multiverse Packages [866B]
Get:20 http://archive.ubuntu.com dapper/multiverse Packages [121kB]
75% [20 Packages gzip 0] [12 Packages bzip2 10797056] [14 Packages 1241752/2458kB 50%] [Connecting to archive.ubuntu.com (195.248.90.54)]         186kB/s 7s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:21 http://archive.ubuntu.com dapper-updates/restricted Packages [20B]
77% [19 Packages bzip2 0] [14 Packages 1348360/2458kB 54%]                                                                                        186kB/s 6s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com dapper-updates/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Ign http://pl.archive.ubuntu.com dapper/universe Packages
Get:22 http://pl.archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Ign http://pl.archive.ubuntu.com dapper/multiverse Packages
Get:23 http://pl.archive.ubuntu.com dapper/main Packages [821kB]
Err http://pl.archive.ubuntu.com dapper/main Packages
  Error reading from server - read (104 Connection reset by peer)
Get:24 http://pl.archive.ubuntu.com dapper-updates/main Packages [71.4kB]
Ign http://pl.archive.ubuntu.com dapper-updates/main Packages
Get:25 http://pl.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Ign http://pl.archive.ubuntu.com dapper-updates/restricted Packages
Get:26 http://pl.archive.ubuntu.com dapper-updates/universe Packages [15.4kB]
Ign http://pl.archive.ubuntu.com dapper-updates/universe Packages
Get:27 http://pl.archive.ubuntu.com dapper-updates/multiverse Packages [866B]
44% [27 Packages bzip2 0] [Connecting to pl.archive.ubuntu.com (153.19.251.225)]                                                                 203kB/s 17s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://pl.archive.ubuntu.com dapper-updates/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:28 http://pl.archive.ubuntu.com dapper/universe Packages [3225kB]
Err http://pl.archive.ubuntu.com dapper/universe Packages
  Error reading from server - read (104 Connection reset by peer)
Get:29 http://pl.archive.ubuntu.com dapper/multiverse Packages [121kB]
30% [29 Packages gzip 0] [Connecting to pl.archive.ubuntu.com (153.19.251.225)]                                                      328kB/s 49710d 6h27m56s
gzip: stdin: not in gzip format
Err http://pl.archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:30 http://pl.archive.ubuntu.com dapper-updates/main Packages [97.9kB]
31% [Connecting to pl.archive.ubuntu.com (153.19.251.225)]                                                                           328kB/s 49710d 6h27m56s
gzip: stdin: not in gzip format
Err http://pl.archive.ubuntu.com dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Get:31 http://pl.archive.ubuntu.com dapper-updates/restricted Packages [20B]
Get:32 http://pl.archive.ubuntu.com dapper-updates/universe Packages [16.8kB]
31% [Working]                                                                                                                        328kB/s 49710d 6h27m56s
gzip: stdin: not in gzip format
Err http://pl.archive.ubuntu.com dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 2847kB in 31s (90.6kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://pl.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
szopa@kripke:/etc/apt$
szopa@kripke:/etc/apt$ sudo vim sources.list
szopa@kripke:/etc/apt$ sudo apt-get update
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:5 http://archive.ubuntu.com dapper Release [34.8kB]
Get:6 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Get:7 http://archive.ubuntu.com dapper/main Packages [619kB]
Get:8 http://security.ubuntu.com dapper-security/main Sources [12.1kB]
Get:9 http://security.ubuntu.com dapper-security/restricted Sources [964B]
Get:10 http://archive.ubuntu.com dapper/restricted Packages [4571B]
Ign http://archive.ubuntu.com dapper/restricted Packages
Get:11 http://archive.ubuntu.com dapper/main Sources [255kB]
Ign http://archive.ubuntu.com dapper/main Sources
Get:12 http://archive.ubuntu.com dapper/restricted Sources [1478B]
Get:13 http://archive.ubuntu.com dapper-updates/main Packages [71.4kB]
Ign http://archive.ubuntu.com dapper-updates/main Packages
Get:14 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:15 http://archive.ubuntu.com dapper-updates/main Sources [46.3kB]
Ign http://archive.ubuntu.com dapper-updates/main Sources
Get:16 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:17 http://archive.ubuntu.com dapper/restricted Packages [4320B]
Get:18 http://archive.ubuntu.com dapper/main Sources [336kB]
68% [17 Packages gzip 0] [7 Packages bzip2 3268608] [18 Sources 259289/336kB 77%]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/restricted Packages
  Sub-process gzip returned an error code (1)
73% [7 Packages bzip2 3596288] [Connecting to archive.ubuntu.com (195.248.90.23)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/main Sources
  Sub-process gzip returned an error code (1)
Get:19 http://archive.ubuntu.com dapper-updates/main Packages [97.9kB]
Get:20 http://archive.ubuntu.com dapper-updates/main Sources [58.4kB]
76% [Working]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Err http://archive.ubuntu.com dapper/restricted Sources
  Sub-process bzip2 returned an error code (2)
76% [Working]                                                                                                                                     205kB/s 1s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
76% [14 Packages bzip2 0]                                                                                                                         205kB/s 1s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Sub-process bzip2 returned an error code (2)
Fetched 947kB in 6s (158kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

At first I thought that something may be wrong with my sources.list, so I made them look like in [http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2). Still didn't help.

Is there a problem with the repos? Or I am still doing something wrong?

Thanks in advance for your help!

---

### Post by Nikos_M on 2006-09-23
Strangely enough i have exactly the same error messages...
Also since moving to Belgium.To be more precise moving from an external connection to a university one.What on earth are they doing in the belgian universities???

---

### Post by fangspeen on 2006-09-27
I'm experiancing the same exact prob from in South Africa:


Get:1 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/main Packages
Get:3 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/restricted Packages [4571B]
99% [3 Packages bzip2 0] [Waiting for headers] [Waiting for headers]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/restricted Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/main Packages
Get:4 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/main Sources
Get:5 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Fetched 283B in 7s (39B/s)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2](http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Macuyiko on 2006-10-09
Same problem here, also from a Belgian university...

---

### Post by Sircoelho on 2006-12-26
I'm facing the same problem here in Brazil

> 51% [10 Packages bzip2 7356416] [11 Packages 54106/126kB 42%] [12 Packages 8205
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
  Sub-processo bzip2 retornou um código de erro (2)

> Falha ao baixar [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2)  Sub-processo bzip2 retornou um código de erro (2)
Lendo Lista de Pacotes... Pronto
E: Alguns arquivos de índice falharam no download, eles foram ignorados ou os antigos foram usados em seu lugar.

Sad I never saw this on Dapper and now Edgy return this :(

---

### Post by silvari on 2008-01-06
I'm getting a similiar problem in the U.S.A. trying to upgrade an Edgy system to Feisty, using 'Update Manager'.

Failed to fetch [http://**security.ubuntu.com](http://**security.ubuntu.com)**/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

---

