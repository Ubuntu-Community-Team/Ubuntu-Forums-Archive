---
title: "Failed to fetch packages (404 Not Found)"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by rmp251 on 2013-01-12
I'm having trouble updating packages. Running "sudo apt-get update" produces many lines like the following:

```
W: Failed to fetch http://mirror.cs.uwaterloo.ca/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

```This started when I was trying to install sqlite3 and ran into the following:

```
Err http://mirror.cs.uwaterloo.ca/ubuntu/ maverick-updates/main sqlite3 amd64 3.7.2-1ubuntu0.1
  404  Not Found
Failed to fetch http://mirror.cs.uwaterloo.ca/ubuntu/pool/main/s/sqlite3/sqlite3_3.7.2-1ubuntu0.1_amd64.deb 404  Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```I noticed those particular packages (3.7.2) aren't there but a newer version (3.7.4) seems to be there.

I'm using Ubuntu 11.04.  When I updated from version 10 a while ago, something may have gone wrong (I experienced minor issues which seemed inconsequential at the time and so I ignored them and have hence forgotten about them). I have no idea if that plays into my current issue.

Any assistance in getting my system back to relative normal would be greatly appreciated.

---

### Post by iponeverything on 2013-01-12
11.04 has reached its end of life --

11.10 is the LTR. 

if you wish to continue using 11.04 

edit your /etc/apt/sources.list 

to use old-releases

[http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

---

### Post by dude6595 on 2013-01-12
> **iponeverything said:**
> 11.04 has reached its end of life --

11.10 is the LTR. 

if you wish to continue using 11.04 

edit your /etc/apt/sources.list 

to use old-releases

[http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

what about those of us on 12.10? It wont let me check for updates cause of those 404 errors

---

### Post by deadflowr on 2013-01-12
> **dude6595 said:**
> what about those of us on 12.10? It wont let me check for updates cause of those 404 errors

I would say start a new thread to solve your problem and post the results from the command:

```
sudo apt-get update
```

The OP for this thread is running a dead release.
12.10 is very much alive, so the issues are quite different.

Also, 11.10 is not an LTS, 12.04 is. 
Support for 11.10 ends in April.

---

