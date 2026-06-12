---
title: "Is Ubuntu 12.04 LTS still supported?"
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by The Cog on 2015-12-23
According to this page, it is still supported: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
And this page: [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
But according to thie page, it's well past end of life: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I was just trying to install new software on a 12.04 server:
```
~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise
```

But I get lots of errors like this:
```
~# apt-get update
Ign http://security.ubuntu.com precise-security Release.gpg
Ign http://gb.archive.ubuntu.com precise Release.gpg
Ign http://gb.archive.ubuntu.com precise-updates Release.gpg
Ign http://security.ubuntu.com precise-security Release
```
lots more like that, and then:
```
Err http://security.ubuntu.com precise-security/main Sources
  403  Forbidden
Err http://security.ubuntu.com precise-security/restricted Sources
  403  Forbidden
Err http://security.ubuntu.com precise-security/universe Sources
  403  Forbidden
Err http://security.ubuntu.com precise-security/multiverse Sources
  403  Forbidden
```
lots more like that, and then:
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  403  Forbidden
```
lots more like that, and then:
```
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I checked with a browser, and the URLs that failed to download don't appear to exist on the server.

I was hoping to wait until 16.04 LTS before upgrading the OS. 
Has 12.04 been dropped out of support early, or is something else wrong?

---

### Post by mörgæs on 2015-12-23
12.04.3 is out of support, but it should be possible to upgrade to 12.04.5 which has five years.
Have you tried to change mirror?

---

### Post by Bucky Ball on 2015-12-23
As above. I'm on 14.04.3 and to keep up with point releases I use 'sudo apt-get dist-upgrade' along with my regular update/upgrade (I do it manually in a terminal a couple of times a week rather than with Software Updater). 

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Just thought I'd throw that in. Have you been using the 'dist-upgrade' command when updating/upgrading?

---

### Post by The Cog on 2015-12-23
I don't think changing mirror will help. For example, this URL (listed above) fails: [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources) but opening [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/) in the browser shows that both Sources.gz and Sources.bz2 exist and are only a few days old. So perhaps my apt is broken.

I don't know what to do about that. This box is configured for automatic security updates. Did they release a change to apt-get and not put it in securty updates?

---

### Post by Bucky Ball on 2015-12-23
Pondering and just a thought. I've never seen it or used it, but isn't there an option to upgrade on install media? Just wondering ... if you created 14.04.3 install media and then updated/upgrade from that ...

As I say, thinking out loud ... :-k

* But yea, what your saying in your post does point to broken something. Strange you didn't get to 12.04.4 at some stage, though, if there was one, with your regular updates/upgrades, seeing as you made it to 12.04.3

---

### Post by grahammechanical on 2015-12-23
Can I make a point about using install media to upgrade?

Some of us found a few months ago that yes we do get an offer to upgrade an existing Ubuntu install to a newer version but the result was the same as Erase disk and install Ubuntu. This was reported in the Ubuntu Development section of this forum during the last development cycle.

Has it been fixed? Has anybody tested it?

It is the hardware enablement stack on 12.04.3 that is no longer supported. This wiki page should help to install the hardware enablement stack in 12.04.4 & then 12.04.5

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by The Cog on 2015-12-23
I may have been sending people on a wild goose chase here. 
Although the URL in the error message doesn't exist, the error number is 403 forbidden, not 404 not found. 
If I try to use curl for the URL, I get a squid error html page.
I wonder if the real problem is our proxy not letting the server out. 
I will try to find out and get back to you.

---

### Post by The Cog on 2015-12-23
Sorry to have bothered you all. Yes, it was our local proxy blocking the requests.
The server now says it's 12.04.5 after a full update.

I guess that after failing to get the non-compressed listing, apt tries again and gets the compressed one. Or maybe the main index now says to fetch compressed listings instead - I'm not that familiar with apt.

Anyway, the clue was there from the beginning in the **Forbidden **instead of **Not Found**.
When did the proxy get changed? That's another question entirely. I can guess.

@grahammechanical
Thanks for the heads-up about the HWE thing - that's new to me too. 
It looks as though my options are to install the 14.04 HWE+kernel or to a release-upgrade.

At the moment, I'm thinking I will clone the VM as is (a a  backup), and then do a release-upgrade to 14.04.

---

### Post by ajgreeny on 2015-12-23
If this is a server with no xorg it will surely be only the kernel that might be your problem and ought to be solvable, if it needs solving, by installing the appropriate linux-generic-lts-trusty or whatever version is the most recent for precise.

What kernel are you running? If you are still on 3.2.#-#, the 3.2 series being the original for precise as far as I can remember, there should be nothing else to upgrade.  If now using 3.5, 3.8, or 3.11, I think you need to upgrade to the linux-generic-lts-trusty package mentioned above.  If you do have xorg installed as well you probably need to consider that as well, but I'm afraid I am not sure how necessary that is, nor if you can update the kernel but not the xorg packages without causing problems.

---

### Post by The Cog on 2015-12-24
I ended up running do-release-upgrade, which appears to have left me with a working 14.04 system. As the reason for all this in the first place was wanting to install and use ipset features with iptables, I thought a full upgrade was probably best. It seems that ipset was quite new in 12.04 and I'm guessing that the upgrade to 14.04 probably contained improvements in both userspace and the kernel. I did some testing today, and the new rules with ipset seem to be working nicely. 

There was no X on this box, it's just a server.

Come 16.04, I want to try out nftables and see if I can use maps for looking up NAT translations. But that's another story.

---

