---
title: "Update Manager"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by tvillamil on 2010-05-02
I keep on getting these errors when running Update Manager:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

I've reached my wit's end in trying to get this figured out....

Can someone help me out?

Thanks

---

### Post by KiLaHuRtZ on 2010-05-02
```
sudo apt-get update
```

If that doesn't work, perhaps the repository is not complete or under high load (which happens on release day...).

---

### Post by tvillamil on 2010-05-02
Thanks, I tried that and I get the results below.  This has been happening for a couple of weeks now.  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 172kB of source archives.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe vpnc 0.5.3r449-2 (dsc) [998B]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe vpnc 0.5.3r449-2 (tar) [119kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe vpnc 0.5.3r449-2 (diff) [51.6kB]
Fetched 4,659B in 1s (3,657B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.5.3r449-2.dsc](http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.5.3r449-2.dsc)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.5.3r449.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.5.3r449.orig.tar.gz)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.5.3r449-2.diff.gz](http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.5.3r449-2.diff.gz)  Hash Sum mismatch
E: Failed to fetch some archives.
demoadmin@demoadmin-laptop:~/tmp_dir$ sudo apt-get update
[sudo] password for demoadmin: 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
99% [2 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
55% [3 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
38% [4 Translation-en_US bzip2 0B] [Connecting to www-proxy.oracle.us.com (205.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                 
  
Fetched 6,627B in 2s (2,624B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by KiLaHuRtZ on 2010-05-02
Make this file...

```
/etc/apt/apt.conf.d/01translations
```

And put this line in it...

```
APT::Acquire::Translation "none";
```

Then try again...

```
sudo apt-get update
sudo apt-get upgrade
```

Also, you might want to try a different repository...

For example...us.archive.ubuntu.com

---

### Post by tvillamil on 2010-05-02
Thanks for the advice... Sadly.... it didn't work... :(

I created the 01translaton file in the directory specified.. and performed the update, but still received the same error

After changing to the US server, it got worse..... I received the following errors:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
99% [3 Packages bzip2 0B] [Connecting to www-proxy.oracle.us.com (205.178.189.1bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
  Sub-process /bin/bzip2 returned an error code (2)
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                   
99% [4 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
99% [5 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
99% [6 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
99% [7 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
99% [8 Sources bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 12.4kB in 3s (3,843B/s)
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas??

---

### Post by KiLaHuRtZ on 2010-05-02
Ok, can I see your sources.list file?

```
cat /etc/apt/sources.list
```

---

### Post by tvillamil on 2010-05-03
Thanks Kilahurtz!!!

Here you go:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

##  Toni comment out

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free # disabled on upgrade to lucid


##  Toni comment out

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main multiverse universe

##  Toni added, but later commented out

###### Ubuntu Update Repos

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates

---

### Post by lechien73 on 2010-05-03
Are you behind a proxy server?

---

### Post by tvillamil on 2010-05-03
No Proxy Server.

---

### Post by KiLaHuRtZ on 2010-05-03
I didn't catch this at first either...

```
www-proxy.oracle.us.com
```

Could be the repository?

Can you resolve 'archive.ubuntu.com'?

```
nslookup archive.ubuntu.com
```

Should be all 91.189.x.x addresses.

---

### Post by wojox on 2010-05-03
Go into System > Admin > Software Sources > Ubuntu Software and click on Download from and then other. Then click on Select Best Server.

---

### Post by Bumper44 on 2010-05-03
I have the same problem as this guy. I tried all the suggested option and none worked. However I am using a different dns server then I originally started with, if that means anything.

---

### Post by tvillamil on 2010-05-03
Yes, see below and thanks for taking the time to look at this!!

Server:        192.168.1.254
Address:    192.168.1.254#53

Non-authoritative answer:
Name:    archive.ubuntu.com
Address: 91.189.92.166
Name:    archive.ubuntu.com
Address: 91.189.92.167
Name:    archive.ubuntu.com
Address: 91.189.88.31
Name:    archive.ubuntu.com
Address: 91.189.88.40
Name:    archive.ubuntu.com
Address: 91.189.88.46
Name:    archive.ubuntu.com
Address: 91.189.88.45
Name:    archive.ubuntu.com
Address: 91.189.88.30
Name:    archive.ubuntu.com
Address: 91.189.92.165

---

### Post by Bumper44 on 2010-05-03
nslookup archive.ubuntu.com

I ran that and got what I was supposed to. All 91.189.x.x addresses.

Is that not what was supposed to happen?

---

### Post by tvillamil on 2010-05-03
Thx Wojox...

I also attempted the Best Server option.... It delivered even more errors.... :(

********************

Get:1 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid Release.gpg
Get:2 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid Release
Ign [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid Release
Get:3 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/main Packages
99% [3 Packages bzip2 0B] [Connecting to www-proxy.oracle.us.com  (205.178.189.1bzip2: (stdin) is not a bzip2 file.
Err [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:4 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/restricted Packages
99% [4 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a  bzip2 file.
Err [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:5 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/main Sources
99% [5 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a  bzip2 file.
Err [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:6 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/restricted Sources
99% [6 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a  bzip2 file.
Err [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:7 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/universe Packages
99% [7 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a  bzip2 file.
Err [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:8 [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/universe Sources
99% [8 Sources bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 12.4kB in 4s (3,006B/s)
W: GPG error: [http://ftp.citylink.co.nz]("http://ftp.citylink.co.nz/")  lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ftp.citylink.co.nz/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)   Sub-process /bin/bzip2 returned an error code (2)
 W: Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/lucid/restricted/binary-amd64/Packages.bz2](http://ftp.citylink.co.nz/ubuntu/dists/lucid/restricted/binary-amd64/Packages.bz2)   Sub-process /bin/bzip2 returned an error code (2)
 W: Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/lucid/main/source/Sources.bz2](http://ftp.citylink.co.nz/ubuntu/dists/lucid/main/source/Sources.bz2)   Sub-process /bin/bzip2 returned an error code (2)
 W: Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/lucid/restricted/source/Sources.bz2](http://ftp.citylink.co.nz/ubuntu/dists/lucid/restricted/source/Sources.bz2)   Sub-process /bin/bzip2 returned an error code (2)
 W: Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/lucid/universe/binary-amd64/Packages.bz2](http://ftp.citylink.co.nz/ubuntu/dists/lucid/universe/binary-amd64/Packages.bz2)   Sub-process /bin/bzip2 returned an error code (2)
 W: Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/lucid/universe/source/Sources.bz2](http://ftp.citylink.co.nz/ubuntu/dists/lucid/universe/source/Sources.bz2)   Sub-process /bin/bzip2 returned an error code (2)
 E: Some index files failed to download, they have been ignored, or  old ones used instead.

---

### Post by Bumper44 on 2010-05-03
I fixed my problem by following this - [http://ubuntuforums.org/showthread.php?t=1221323]("http://ubuntuforums.org/showthread.php?t=1221323")

Your problem seems different. I doubt that will work for you. Hope you find a fix.

---

### Post by tvillamil on 2010-05-03
Yep, I saw that thread...

You're right.... It didn't work for me... :(

---

### Post by Bumper44 on 2010-05-03
Well, I wish you luck. :D

---

### Post by tvillamil on 2010-05-04
Solved.  A proxy setting was hiding in the etc/apt/apt.conf file.  Once I remarked it out... it was like magic..:)

---

### Post by Geximus on 2010-05-18
How do you check for proxy in the ect/apt/apt.conf.d location? I'm kind of lost here. Could I get a step by step to get this to work?

---

### Post by klyndt on 2010-07-31
I had a similar problem and it wasn't a proxy issue. It was solved here:
[http://ubuntuforums.org/showthread.php?t=1488419](http://ubuntuforums.org/showthread.php?t=1488419)

Klyndt

---

