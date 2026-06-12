---
title: "Install apps using the &quot;unofficial ubuntu 5.04 starter guide&quot;"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by dictator88 on 2005-10-16
K, I'm really working at this from a linux beginner point of veiw but geeezzz.
After a month of reading, trying, re-installing, again and again, I am at my witz end.
Basicly the install goes great, I setup email, gaim, ect. So, then I want more. I start following the directions from the "unofficial ubuntu 5.05 starter guide". First nothing worked right at all just to find out a couple of lines it tells you to put in are not right. 
---- sources.list
deb http:.//ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse
& deb http:/ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse
---- (Someone may want to fix this)

THEN, I move on to page 11. "How to install menu editor for gnome"
( sudo apt-get install smeg ) - and I get E: Couldn't find package smeg

I get the same error for 90% of the things listed on this doc to install. I've run apt-get update and upgrade and it doesn't mention downloading anything else sooooooooo? Help please.

---

### Post by aysiu on 2005-10-16
Unfortunately, you've hit Ubuntu at a weird transitional period. The unofficial backports got shut down, so it's now just official backports. w32codecs and libdvdcss2 got taken out of the repositories (even the Universe ones) for legal reasons. The guide has yet to be updated for the new release of Breezy 5.10.

If you want extra repositories that work, follow these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Please keep in mind that a lot of the documentation for Ubuntu is volunteer effort. The Ubuntu Guide, for example--though it's wonderful--is all done by one person. The link I just gave you in this post I put together myself.

---

### Post by dictator88 on 2005-10-16
k, done. Now, running the apt-get update goes smooth but not the apt-get upgrade. ?
Also, tried the next one on the list of thigs to do, AKA apt-get install smeg ,,,,
and get the same problem, so, are all these apps down then? I just don't have a working understanding of what this is doing in the first place to know what isn't working and why...

---

### Post by ryan76 on 2005-10-17
My basic understanding is that it grabs files and installs them. (But I bet I'm even newbie-er than you!)

Is it OK to do that to the sources list for AMD64?

---

### Post by dictator88 on 2005-10-17
The exact error I'm till getting for "MOST" installs is - 

root@Homewall:/home/curthome # sudo apt-get install mozilla-acroread
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  acroread
Recommended packages:
  acroread-plugins
The following packages will be REMOVED:
  acroread-debian-files
The following NEW packages will be installed:
  mozilla-acroread
The following packages will be upgraded:
  acroread
1 upgraded, 1 newly installed, 1 to remove and 11 not upgraded.
Need to get 23.9MB of archives.
After unpacking 31.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse acroread 7.0-0.9~hoary1 [23.4MB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse acroread 7.0-0.9~hoary1  Connection timed out [IP: 82.211.81.151 80]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse mozilla-acroread 7.0-0.9~hoary1 [459kB]
Fetched 459kB in 2m25s (3151B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0-0.9~hoary1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0-0.9~hoary1_i386.deb)  Connection timed out [IP: 82.211.81.151 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

