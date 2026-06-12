---
title: "Cannot connect  via apt-get update"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by pfwd.tech on 2007-10-05
Hi i have a few software updates that i cannot seem to connect to.
It hangs via update manager and doesn't get any 0% via apt-get update.
This is the output:
```
 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsndfile1 openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-style-human
  openoffice.org-writer python-uno ttf-opensymbol
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.3MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to security.ubuntu.com (91.189.88.31)]


```
any reason why it isn't working.  i cant connect to other things fine.

---

### Post by Symbolis on 2007-10-05
Just posting to note I'm having similar trouble.

Was thinking I messed something up, but even the Ubuntu 'base' install on the desktop is having trouble downloading updates.

Seems to be going faster now, but still not particularly fast.

The updates are to openoffice.org, ttf-opensymbol and a few others. Probably part of the reason.

---

### Post by pfwd.tech on 2007-10-05
Well its comforting to know other are in the same boat.  I'm still getting nothing.  Will try again later.

---

### Post by darkfame on 2007-10-05
Downloads are very slow from security.ubuntu.com at the moment.

---

### Post by pfwd.tech on 2007-10-05
Yeah its working fine now.  Just thought i would mention it

---

### Post by jeremy12 on 2007-10-05
there has to be something going on, it is not working for me as well when i try to install something:

```
 sudo apt-get install p7zip-full
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  p7zip-full
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 1393kB of archives.
After unpacking 3662kB of additional disk space will be used.
0% [Connecting to us.archive.ubuntu.com (91.189.89.8)]
```

my ssh terminal has been saying that for 20 minutes now i did apt-get update and upgrade last night and all was fine... i can ping 91.189.89.8

---

### Post by Symbolis on 2007-10-05
```
Hit http://ca.archive.ubuntu.com feisty-updates/main Sources
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 3B in 8m11s (0B/s)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (91.189.89.6), connection timed out [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (91.189.89.6), connection timed out [IP: 91.189.89.6 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
symbolis@symbolis-laptop:~$ 
```

As of 8:35AM EST.

---

### Post by SumitB on 2007-10-05
I am having the same problem since 10AM IST (0430GMT) today! It either does not connect or if it does, it is extremely slow! It seems that the archive servers are having connectivity issues today :confused:

---

