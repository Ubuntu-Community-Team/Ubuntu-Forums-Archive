---
title: "Is anyone having this problem?"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2010-09-11
Two days ago, I upgraded from 8.04 to 10.04 using the installation disk.  The installation went without a hitch.  I have slowly been configuring my Ubuntu to my liking.  My problem is with going to different websites.  As soon as the website opens, the screen goes blank and the status bar shows that my computer is Waiting for either [www.google-analytics.com](www.google-analytics.com) or s7.addthis.com to load.  But, nothing happens.  My screen stays blank.  After searching the Internet, I found that by editing the Host file under the etc folder, it will solve my problem.  Now, other web analyzing websites are trying to do the same thing.  This does not happen in Windows using Firefox, but it does under Ubuntu.  Has anyone ever experience this or close to it?  I am trying to find out what could be causing this and if it can be corrected.  Thanks.

---

### Post by thegod_slayer on 2010-09-11
try this......


sudo apt-get --reinstall set up of firefox-3.0 xulrunner-1.9

---

### Post by lovinglinux on 2010-09-12
Use [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/9609/") to block those web tracking services.

> **thegod_slayer said:**
> try this......

sudo apt-get --reinstall set up of firefox-3.0 xulrunner-1.9

Firefox 3 is no longer supported and is not available in Ubuntu 10.04, so that one is a dummy package. The command you suggested does not exist.

The correct command would be:

```
sudo apt-get install --reinstall firefox xulrunner-1.9
```

---

### Post by gilloz on 2010-09-13
Thanks lovinglinux and thegod_slayer for your responses.  Xul-runner was already installed.  I added Ghostly to my Firefox and indeed it prevented these unwanted sites from taking over my browsing.  I also solved my problem of not being able to get on the Internet most recently by editing my Resolv.conf file and changing my DNS nameservers numbers.  That made all the difference for getting Online.  Part of the help also came from a poster name fatigue.  In any case, looks like I am back in business, for now.  Thank you all.

---

