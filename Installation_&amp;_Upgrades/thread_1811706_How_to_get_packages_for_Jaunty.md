---
title: "How to get packages for Jaunty"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by maidenfan on 2011-07-25
Hi Guys,

This probably has been answered before...but I could not find it.

I have ubuntu 9.04 Jaunty at my office machine. I need to install some development libraries (or any packages for that matter...) on it. And support for Jaunty has been suspended for quite some time now since its not an LTS. So, I can not "apt-get" the packages. So can I use repository packages of any other ubuntu distro such as ubuntu 8.04 Hardy, or even better...from Lucid ? Or will it cause any problems ?
If any other solution ( any other repository I don't know about...) exists, pls let me know.
Thanks in advance guys...

---

### Post by mikewhatever on 2011-07-25
The packages for Jaunty should be available at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com). Replace the contents of your /etc/apt/sources.list with the following, and you'll be good to go.

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse 

---

### Post by blackbird3216 on 2011-07-25
Hmm, although you cannot get new packages, I think the old packages that have been updated up to the last day of Jaunty suppport can still be downloaded through synaptic. 

The lack of support simply means you don't get the newest updates. 
Although, another option is to simply upgrade to the newest release, or try the LTS. I actually just upgraded to 10.04 on Friday, and its working great.

---

### Post by maidenfan on 2011-07-25
@Mikewhatever : superb... : ) can not believe I missed that !!! Thanks a lot...
But just out of curiosity...does it really make a difference that I am using packages of Lucid/Hardy on Jaunty ? I mean, are the packages made or _tweaked_ depending on the distribution they are going to run on ?
@Blackbird3216 : Ya, actually I also wanted to upgrade to Lucid LTS. See, we want to put customized Linux & rootfs using a tool called Linux Target Image Builder (LTIB) on a Freescale target (imx25pdk) linux development platform with QT on it. But the freescale people (and their documentation...) insists that I (developers... I mean) use 9.04. They have some build issues on other distros :confused: So, that's the only reason that is stopping me from using other distro. Anyway, I am experimenting with LTIB on Lucid at my home machine, and trying to make it work.
So I will give it a try and let you know. Thanks a lot again guys...

---

### Post by mikewhatever on 2011-07-26
The packages are not necessarily customized, but different releases would have different versions, so that you'll most probably have problems mixing releases.

---

### Post by maidenfan on 2011-07-26
I did run into problems actually... :)
Too many jaunty packages were being downgraded since I switched to Hardy repo. My samba file sharing does not work :(
Anyway, I will try using Lucid repo and let you know...

---

### Post by thecheekymonkey on 2011-07-27
> **mikewhatever said:**
> The packages for Jaunty should be available at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com). Replace the contents of your /etc/apt/sources.list with the following, and you'll be good to go.

oh mate, believe me, youve just saved my bacon. I want 9.04, simple as and these three lines have ended a nightmare ive just been having all afternoon.


many many thanks..............

---

