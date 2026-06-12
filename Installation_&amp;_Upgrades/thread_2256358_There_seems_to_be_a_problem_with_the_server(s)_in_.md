---
title: "There seems to be a problem with the server(s) in Germany"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by robert-kormar on 2014-12-11
Hi,

I'm running 12.04.5 LTS and when executing > apt-get update I get the following:

                        W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Hash Sum mismatch
 

 W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Hash Sum mismatch
 

 E: Some index files failed to download. They have been ignored, or old ones used instead.

I'm located in Germany so my sources.list contains URLs to the server(s) here in Germany. I tried to research the problem and came across the suggestion to perform the following:

mv /var/lib/apt/list/* ~/Desktop/
apt-get update
apt-get upgrade

This did not help, so I edited my sources.list file changing all de. references to us. then moved the files from /var/lib/apt/list/ again, performed the apt-get update again and got an "error/warning" free update. This tells me there is a problem with the Ubuntu mirror(s) here in Germany, and not with my machine(s).

This has been happening now for a couple of weeks, and I first experienced it when I wanted to do a distribution upgrade from 12.04 LTS to 14.04 LTS. Can somebody please get this info to the proper people so I can finally upgrade to 14.04 LTS?

Thank you!

---

### Post by bapoumba on 2014-12-13
Have you tried to use the main servers ?

---

