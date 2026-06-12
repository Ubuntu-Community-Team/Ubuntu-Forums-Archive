---
title: "Ubuntu 9.04 Repo?"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by marcmcn on 2011-06-07
Hi Guys
I'm using a system which is based around 9.04 and yes I know this is not the latest and greatest however the softwares in question hasn't been confirmed on the newest version of ubuntu.
However I was doing a new build and noticed when I went to do and apt-get install there didn't appear to be any repo's 
I'm just wondering have the repo's for 9.04 been turned off???
Cheers
Mark

---

### Post by Joe of loath on 2011-06-07
Yup, since it hit EOL the mirrors have been turned off.

I believe you can still access them if you use the archive mirrors, but I don't know how this is done unfortunately.

---

### Post by arpanaut on 2011-06-07
This may help, using the old-release repositories will get you started, but a fresh install to a supported LTS would be better.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by ajgreeny on 2011-06-07
See [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by snowpine on 2011-06-07
9.04 reached its end of life October 2010 and is no longer supported or recommended in any way.

If you wish to use the 9.04 repositories for educational purposes, you may change your mirrors to: old-releases.ubuntu.com

Keep in mind old-releases is a "snapshot" as of the end-of-life date; there will be no more bug fixes or security patches--no matter how critical--for 9.04.

If you tell us what "the softwares in question" are perhaps someone on the forums can help you get them working with a supported Ubuntu release?

---

### Post by drs305 on 2011-06-07
You can still access the old repositories by editing your /etc/apt/sources.list file. 

The new address should be:
> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)
replacing the following (or your designated current server):
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by marcmcn on 2011-06-07
Hey Guys 
Just wanna say a quick thanks for all the info and pointers 
I'm not a Deb/Ubuntu user I'm usually in the fedora land 
Changing the repo's to the old ones will do nicely thank you again for the help
Cheers
Marc

---

