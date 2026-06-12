---
title: "Standard 6.06 Server cannot update"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by stalker145 on 2007-06-21
Standard Disclaimer:
I'm not sure if this has been asked before (and I've searched for the last hour - probably poorly ;) ) but here it goes...

I have your standard (mostly) 6.06 Server loaded on my box working perfectly with the exception of my update issue. I've seen a lot of posts asking about > You may want to run apt-get update to correct these problems but all of the answers seem to deal with repos outside of Ubuntu. 

OK, here's the problem:
```
> sudo apt-get update
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Err http://security.ubuntu.com dapper-security Release
  
Hit http://us.archive.ubuntu.com dapper-updates Release
Get:4 http://security.ubuntu.com dapper-security Release [50.9kB]
Get:5 http://us.archive.ubuntu.com dapper Release [34.8kB]
Ign http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Get:6 http://us.archive.ubuntu.com dapper-updates Release [50.9kB]
Ign http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 137kB in 25s (5363B/s)
Reading package lists...
[COLOR="Red"]W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems[/COLOR]

```

No problem. Just for fun I run
```
> apt-get update
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Err http://security.ubuntu.com dapper-security Release
  
Hit http://us.archive.ubuntu.com dapper-updates Release
Get:4 http://security.ubuntu.com dapper-security Release [50.9kB]
Get:5 http://us.archive.ubuntu.com dapper Release [34.8kB]
Ign http://security.ubuntu.com dapper-security Release
Ign http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Get:6 http://us.archive.ubuntu.com dapper-updates Release [50.9kB]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 137kB in 28s (4894B/s)
Reading package lists...
[COLOR="red"]W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems[/COLOR]
```
As expected, I get the same error. It's right there... it's staring me in the face, but I can't seem to figure it out on my own.

If anyone needs my sources.list for more info:
```
# 
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Thanks, in advance, for the assist.

---

### Post by stalker145 on 2007-06-22
<Bump>

---

### Post by stalker145 on 2007-06-23
Well, never mind for now. My power supply blew out this morning and I'll have to wait until I get a replacement to work on this. If anyone comes up with ideas before then, please let me know.

By the way... <Bump>

---

