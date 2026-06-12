---
title: "app-mirror for segregated network"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by sprocket12 on 2017-08-31
Hi everyone.  I am working through a tough one that I need some help with.  I have correctly set up all my ubuntu related repos to mirror to my local, internet connected system.  I rsync the mirror repos to a second, USB drive and 'sneakernet' that second drive to a repo server on a segregated, no internet, internal network.  These ubuntu repos work fine.  I've added the repo for webmin.  This works fine too.  It has a key that is downloaded and then added to each server to allow the webmin repo to be trusted.  Ok, all is good to this point.

I've added the stable cinnamon repo to the internet connected server and I am mirroring the content.  Problem is that this uses:

```
sudo add-apt-repository ppa:embrosyn/cinnamon
```

This imports the key to the server while connected to the internet.  I'm not real familiar with the 'apt' system, so how do I get this new, mirrored repo accepted by the internal servers?  Copying the /etc/apt/trusted.gpg.d/* does not work.  I have a few different repos I'd like to add for our internal network.

Thanks

---

