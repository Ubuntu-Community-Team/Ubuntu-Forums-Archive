---
title: "How to compile the latest amule in ubuntu 16.04?"
date: 2016-12-29
forum: Installation &amp; Upgrades
---

### Post by hopelessone on 2016-12-29
Hi, the amule website and forum are down, and i cannot locate the compile instructions anywhere...

I've downloaded the latest amule from github, and i cannot find step by step instructions to compile amule in ubuntu 16.04

I'd like to install: amuled, amulegui, amule

the reason i'd like to install the latest as i'm getting the well known crashes in ubuntu as its an old snapshot in the repo.

Thanks a bunch

---

### Post by mörgæs on 2016-12-30
If you want a new version of Amule the first step should be to test if the one delivered in 16.10 suits your needs and is stable.

---

### Post by hopelessone on 2016-12-30
> the reason i'd like to install the latest as i'm getting the well known crashes in ubuntu as its an old snapshot in the repo.

there is some bug in the ubuntu repo to do with false packets being sent, its already been reported multiple times.

I managed to follow an Arch Forum post to get sorted, i got everything working except upnp requires 1.6.6 and that is non existent in the main repos.. anyway might be able to run without upnp..

---

### Post by macdogdaddy on 2017-04-24
I was yet another user with this problem.  I wanted to post my simple solution here because most people with this problem will likely find this thread, but won't be ready to compile their own packages.  So here's what I did:

1) Uninstall amule:

```
sudo apt-get remove amule amule-common amule-utils
```

2) Downgraded to the latest aMule-stable release "aMule 2.3.2" 

Install the ".deb" packages of a stable amule release by going to this site [https://pkgs.org/download/amule](https://pkgs.org/download/amule) and downloading the ".deb" packages for "Debian Sid" (*the packages for Ubuntu 16.10 suffer the same problem, and the packages for Ubuntu 17.04 won't install*).  Then use GDebi to install each of the main packages, amule, amule-common, amule-utils.  GDebi will complain of unmet dependencies, but no worries.  On the download page there is a "requires" tab.  Click on that tab and dl each of the unmet dependencies GDebi complains about until you've managed to install the entire bundle.   I'm running Ubuntu 16.04 MATE, so for me it looked like this:

  1) libcrypto++6_5.6.4-6_amd64.deb
  2) libboost-system1.62.0_1.62.0+dfsg-4_amd64.deb
  3) amule-common_2.3.2-1_all.deb
  4) amule_2.3.2-1+b2_amd64.deb
  5) libreadline7_7.0-2_amd64.deb
  6) amule-utils_2.3.2-1+b2_amd64.deb

This will likely be the same for you on all flavors of Ubuntu, but may vary slightly by flavor.   So you may have to dl a few different dependencies before GDebi will install aMule for you.  In total, once I figured out what to do, this took me no more than 10-20 mins to complete.  I've been running v2.3.2 for over a week now with my ports open and a hi-ID, and not a single crash so far. 

It's a shame that nobody from Ubuntu's LTS team has decided to fix this well know problem by updating the repo's from "aMule v.2.4.0-svn" to a newer version where this problem is long ago fixed.  But for now, downgrading to a stable release is a viable option.  Hope this helps.

---

### Post by mörgæs on 2017-04-25
> **macdogdaddy said:**
> ...a newer version where this problem is long ago fixed.

Does this mean that it all works in a standard Buntu 17.04?

---

