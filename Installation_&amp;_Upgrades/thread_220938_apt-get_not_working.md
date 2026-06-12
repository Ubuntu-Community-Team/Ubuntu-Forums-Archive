---
title: "apt-get not working"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by saqibm on 2006-07-22
anyone else having this problem? is us.archive.ubuntu.com down?

>>apt-get update

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [39.4kB]        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [9552B]          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg                            
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out
Fetched 85.3kB in 11m33s (123B/s)                        
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by saqibm on 2006-07-22
hmmm....looks like this issue is already posted.
[http://www.ubuntuforums.org/showthread.php?t=217867](http://www.ubuntuforums.org/showthread.php?t=217867)

---

### Post by Greg2 on 2006-07-22
> **saqibm said:**
> anyone else having this problem? is us.archive.ubuntu.com down?

>>apt-get update
-snip-
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg                            
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out
-snip-

Yes... It appears that the us.archive.ubuntu.com is down or having temporary problems at this time.
```

http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
```

Can anyone else confirm this?

---

### Post by Phil196949 on 2006-07-22
I am having the same problem as well. I try to apt-get and it goes through all the rep. urls and it just hangs.:-?

---

### Post by kpurcell on 2006-07-22
is there any other source to download from

I'm trying to install something that needs make and gcc

---

### Post by Greg2 on 2006-07-22
> **kpurcell said:**
> is there any other source to download from

I'm trying to install something that needs make and gcc
You can use the UK instead of the US:

uk.archive.ubuntu.com/ubuntu

save your old sources.list for when it gets fixed

---

### Post by SuperMike on 2006-07-22
I can confirm with Greg2 that this technique works in your /etc/apt/sources.list file to switch 'us.' to 'uk.', but note that if you ever update your system's word processor or anything dealing with dictionaries, you could be in for a bit o' kick in y'bum, mate.

I really wish they could get this working again. When I did a whois on this, I found that the problem appears DNS related. Somehow the DNS databases on the Internet got corrupted and us.archive.ubuntu.com (146.137.96.15) got sent to Argonne National Laboratory. What's sad is that if someone has hacked Argonne National Laboratory, they could send fake package updates through it and we'd all download and install them automatically.

My take? This is the work of malicious hackers. I can't confirm, but the pieces seem to fit too well with their interests.

---

### Post by sog on 2006-07-22
i'm having similarly frustrating issues. i cut the sources.list file over to the uk.archive... versions, did an apt-get update, but i'm unable to install build-essential, subversion, and a couple of other things i need. i keep getting an error that says: 

Package build-essential is not available, but is referred to by another package. That may mean the package is missing, has been obsoleted, or is only available from another source. 

i've tried to turn on the multiverse and every repository i can think of, but it's not finding build-essential so i can't "make" a driver i need. 

any ideas?

---

### Post by jpyanowski on 2006-07-22
Thanks for this info. I thought something was wrong with my computer.

---

### Post by blitzd on 2006-07-23
> **SuperMike said:**
> I can confirm with Greg2 that this technique works in your /etc/apt/sources.list file to switch 'us.' to 'uk.', but note that if you ever update your system's word processor or anything dealing with dictionaries, you could be in for a bit o' kick in y'bum, mate.

I really wish they could get this working again. When I did a whois on this, I found that the problem appears DNS related. Somehow the DNS databases on the Internet got corrupted and us.archive.ubuntu.com (146.137.96.15) got sent to Argonne National Laboratory. What's sad is that if someone has hacked Argonne National Laboratory, they could send fake package updates through it and we'd all download and install them automatically.

My take? This is the work of malicious hackers. I can't confirm, but the pieces seem to fit too well with their interests.

Uhhh, Argonne is a/the US Ubuntu mirror. [https://launchpad.net/distros/ubuntu/+mirror/mirror.anl.gov-cd](https://launchpad.net/distros/ubuntu/+mirror/mirror.anl.gov-cd)

It was good conspiracy theory while it lasted though... heh ;) 

...errr, UNLESS - they've also hacked launchpad to lull us into a false sense of security!!! :o 

(CA mirror is also down FYI)

---

