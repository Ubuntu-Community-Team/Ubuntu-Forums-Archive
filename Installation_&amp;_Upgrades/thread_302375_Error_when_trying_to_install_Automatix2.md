---
title: "Error when trying to install Automatix2"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by evereign on 2006-11-18
Hey guys,

I've been trying lately to install automatix2. but for some reason it fails me.
after i do: 
sudo apt-get update
it starts downloading some stuff and at 99% it fails to connect to some lunarbox.

Here's _exactly_ what I get:

Failed to fetch [http://lunarbox:9999/ubuntu/dists/breezy-backports/Release.gpg](http://lunarbox:9999/ubuntu/dists/breezy-backports/Release.gpg)
Could not connect to lunarbox:9999 (144.89.186.42), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I know if another process is using it?

Thanks guys.]

---

### Post by 0m3n on 2006-11-20
im having the same problem

---

### Post by saintj0n on 2006-11-20
This is the message you get when you have a window open with Synaptic (that or you have a terminal window open with apt-get running). I have never heard if anything else could do that.

---

