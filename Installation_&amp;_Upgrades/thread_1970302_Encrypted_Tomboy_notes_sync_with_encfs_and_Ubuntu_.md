---
title: "Encrypted Tomboy notes sync with encfs and Ubuntu One"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by raffen on 2012-05-01
Hi

I currently use Ubuntu One to sync Tomboy notes unencrypted.  I want to change this to sync Tomboy notes encrypted using encfs.

I have set up a simple encfs configuration to sync a directory as follows:

```
encfs -o nonempty ~/Ubuntu\ One/Clouded ~/Cloud'

```

How do I change Tomboy to write all notes to ~/Cloud rather than the default .local/share/tomboy/ ? 

This is Tomboy 1.60 on Ubuntu 11.10.

SOLUTION:

Turns out it is easy: 

Simply press "Clear" in the Preferences -> Synchronization tab and select "Local folder" and e.g. "~/Cloud/tomboy/".  

Then only encrypted note data will leave the machine and be stored in the cloud.

---

