---
title: "aptget not updating packages"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by roon on 2006-09-09
Hi,
  I am a noob.I have just installed drapper.Prior to that I was also using FC 5.I have configurerd my web browser to connect to the internet by choosing the manual proxy settings and entering the proxy's url and port.It is running perfectly.But the problem is with apt-get.when I enter the```
sudo apt-get update
```

it returns this:

```
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err http://au.archive.ubuntu.com dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (195.248.90.23), connection timed out
Err http://au.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Err http://au.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to archive.ubuntu.com:80 (195.248.90.23), connection timed out
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (130.95.128.79), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```

In FC 5 I tried this command to get yum working:

```
env htp_proxy=http://proxy.xxxxxx.com:pppp yum update
```

I tried this command in dapper too:

but got this output:

```
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper/universe Packages
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://archive.ubuntu.com dapper/universe Packages
  403 Forbidden
Err http://archive.ubuntu.com dapper/main Packages
  403 Forbidden
Err http://archive.ubuntu.com dapper/restricted Packages
  403 Forbidden
Err http://archive.ubuntu.com dapper/multiverse Packages
  403 Forbidden
Get:2 http://au.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:4 http://au.archive.ubuntu.com dapper-updates Release.gpg [189B]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Err http://security.ubuntu.com dapper-security/main Packages
  403 Forbidden
Err http://security.ubuntu.com dapper-security/main Sources
  403 Forbidden
Err http://security.ubuntu.com dapper-security/universe Packages
  403 Forbidden
Err http://security.ubuntu.com dapper-security/universe Sources
  403 Forbidden
Get:5 http://au.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://au.archive.ubuntu.com dapper Release
Hit http://au.archive.ubuntu.com dapper-updates Release
Hit http://au.archive.ubuntu.com dapper-backports Release
Ign http://au.archive.ubuntu.com dapper/main Sources
Ign http://au.archive.ubuntu.com dapper/restricted Sources
Ign http://au.archive.ubuntu.com dapper/universe Sources
Err http://au.archive.ubuntu.com dapper/main Sources
  403 Forbidden
Ign http://au.archive.ubuntu.com dapper-updates/main Packages
Ign http://au.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://au.archive.ubuntu.com dapper-updates/main Sources
Ign http://au.archive.ubuntu.com dapper-updates/restricted Sources
Err http://au.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden
Err http://au.archive.ubuntu.com dapper/universe Sources
  403 Forbidden
Ign http://au.archive.ubuntu.com dapper-backports/main Packages
Ign http://au.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://au.archive.ubuntu.com dapper-backports/universe Packages
Ign http://au.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://au.archive.ubuntu.com dapper-backports/main Sources
Ign http://au.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://au.archive.ubuntu.com dapper-backports/universe Sources
Ign http://au.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://au.archive.ubuntu.com dapper-updates/main Packages
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-updates/restricted Packages
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/main Packages
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/restricted Packages
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/universe Packages
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/multiverse Packages
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/main Sources
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/restricted Sources
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/universe Sources
  403 Forbidden
Err http://au.archive.ubuntu.com dapper-backports/multiverse Sources
  403 Forbidden
Fetched 945B in 7s (129B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

plz help me.

here is my sources.list:


```

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by roon on 2006-09-09
plz help me.

---

### Post by Laki on 2006-09-09
Well, I'm noob too, but did you setup your internet connection? System->Administration->Networking

---

### Post by roon on 2006-09-09
well I posted those other two posts from ubuntu and also posting this from ubuntu.

---

### Post by roon on 2006-09-09
the method of getting updates behind the proxies is given in this url[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html]("http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html")

---

### Post by strabes on 2006-09-25
I am super bummed cuz I am having this same problem. Wierd thing is that it just started happening last week but before that it was fine. This link doesn't seem to be loading for me =\

---

### Post by wonk-o-matic on 2006-09-25
Change http to ftp.  

Maybe tonight I'll take a look at why this is happening.

---

### Post by kamazu on 2006-09-26
I had to do two things. Export the proxy settings

```
export http_proxy=http://username:password@proxyserver.net:port/
```

and then change in /etc/apt/apt.conf the line into
```
Acquire::http::Proxy "true";
```

that worked for me.

greetings, kamazu

---

### Post by bigken on 2006-09-26
hi i had the same problem it was the dns settings in /etc/resolv.conf
all I had to was add my broadband suppliers dns and in my router change the lan config to   
Router as Domain Name Server 
DNS1 xxx.xx.xxx.xx  
DNS2 xxx.xx.xxx.xx

Router as Default Gateway.
Gateway xxx.xxx.xxx.xxx (your ip address)

still dont why when it run out of the box for over 6 months

---

### Post by pradeepadapa on 2006-09-26
hi, u can use synpatic manager instead of apt-get or adept instead of apt-get manager, 

why d u go for aptget man when we hav adept , just try it

---

