---
title: "apt-get update fails"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by xymor on 2008-08-27
I unable to install anything after a fresh install. I'm using the default us source and binary repos. I've even reinstalled fresh a couple times but I keep getting the same errors with apt.

my apt-get update returns:
```
xymor@xymor-desktop:~$ sudo apt-get update
Get:1 http://archive.canonical.com hardy Release.gpg [189B]
Get:2 http://security.ubuntu.com hardy-security Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com hardy Release.gpg [191B]
Get:4 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]
Get:5 http://archive.canonical.com hardy Release [6998B]
Get:6 http://security.ubuntu.com hardy-security Release [58.5kB]
Get:7 http://us.archive.ubuntu.com hardy Release [65.9kB]
Get:8 http://archive.canonical.com hardy/partner Packages [3016B]              
Get:9 http://security.ubuntu.com hardy-security/main Packages [55.3kB]         
Get:10 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]
Ign http://us.archive.ubuntu.com hardy-updates Release                         
Get:11 http://security.ubuntu.com hardy-security/restricted Packages [6636B]   
Get:12 http://security.ubuntu.com hardy-security/main Sources [12.5kB]
Get:13 http://security.ubuntu.com hardy-security/restricted Sources [908B] 
Get:14 http://security.ubuntu.com hardy-security/universe Packages [28.0kB]
Get:15 http://us.archive.ubuntu.com hardy/main Packages [1178kB]           
Get:16 http://security.ubuntu.com hardy-security/universe Sources [4530B]      
Get:17 http://security.ubuntu.com hardy-security/multiverse Packages [8222B]   
Get:18 http://security.ubuntu.com hardy-security/multiverse Sources [14B]      
Get:19 http://us.archive.ubuntu.com hardy/restricted Packages [6986B]          
Get:20 http://us.archive.ubuntu.com hardy/main Sources [338kB]                 
Get:21 http://us.archive.ubuntu.com hardy/restricted Sources [1488B]           
Get:22 http://us.archive.ubuntu.com hardy/universe Packages [4297kB]           
37% [20 Sources bzip2 0] [22 Packages 477160/4297kB 11%]            206kB/s 18s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com hardy/main Sources                            
  Sub-process bzip2 returned an error code (2)
Get:23 http://us.archive.ubuntu.com hardy/universe Sources [1323kB]            
83% [22 Packages bzip2 1049600] [23 Sources 118678/1323kB 8%]        209kB/s 5s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com hardy/universe Packages                       
  Sub-process bzip2 returned an error code (2)
Get:24 http://us.archive.ubuntu.com hardy/multiverse Packages [179kB]          
97% [23 Sources bzip2 0] [24 Packages 454/179kB 0%]                  209kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com hardy/universe Sources                        
  Sub-process bzip2 returned an error code (2)
Get:25 http://us.archive.ubuntu.com hardy/multiverse Sources [60.9kB]          
Get:26 http://us.archive.ubuntu.com hardy-updates/main Packages [306kB]        
Get:27 http://us.archive.ubuntu.com hardy-updates/restricted Packages [6636B]  
Get:28 http://us.archive.ubuntu.com hardy-updates/main Sources [87.5kB]        
Get:29 http://us.archive.ubuntu.com hardy-updates/restricted Sources [908B]    
Get:30 http://us.archive.ubuntu.com hardy-updates/universe Packages [90.2kB]   
99% [28 Sources bzip2 0] [30 Packages 52820/90.2kB 58%]              243kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com hardy-updates/main Sources                    
  Sub-process bzip2 returned an error code (2)
Get:31 http://us.archive.ubuntu.com hardy-updates/universe Sources [22.3kB]    
Get:32 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [20.1kB] 
99% [30 Packages bzip2 200704] [32 Packages 357/20.1kB 1%]           243kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com hardy-updates/universe Packages               
  Sub-process bzip2 returned an error code (2)
Get:33 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [2795B]   
Fetched 8231kB in 39s (207kB/s)                                                
W: GPG error: http://us.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by VMC on 2008-08-27
I've checked that "W: GPG error" errors on the net and found several complaints with same issue. You might want to display your "/etc/apt/sources.list" here just so we can verify.

---

### Post by xymor on 2008-08-28
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by xymor on 2008-09-11
Well I installed debtorrent ,apparently the multiverses headers were corrupted since it took several retries to download a 100% checking copy. 


[SIZE="1"]us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386
1be4723758a2502d90e998c834145dc8f5cc4db6 	0:00:00 	100.0% 	4
0 	0.011 	54.7K/s
0.0K/s 	104MiB
0B 	41.2MiB 	0m00s 	piece 568 failed hash check, re-downloading it[/SIZE]

Maybe my network(virtualbox) is having packet loss/corruption but my other torrent downloads work just fine(no visible corruption/redownloading)

---

