---
title: "apt-get update PROBLEM???"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by jmd8045 on 2010-03-31
apt-get update

How do I resolve this????


Never mind, the problem was the partner files are not carried by UT.

Jim

Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy Release.gpg
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/main Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/restricted Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/universe Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/multiverse Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/partner Translation-en_US
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates Release.gpg
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/universe Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/multiverse Translation-en_US
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security Release.gpg
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/main Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/restricted Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/universe Translation-en_US
Ign [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/multiverse Translation-en_US
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy Release
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates Release
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security Release
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/main Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/restricted Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/main Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/restricted Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/universe Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/universe Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/multiverse Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy/multiverse Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/universe Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/universe Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/multiverse Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-updates/multiverse Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/main Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/restricted Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/main Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/restricted Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/universe Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/universe Sources
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/multiverse Packages
Hit [http://ftp.utexas.edu](http://ftp.utexas.edu) hardy-security/multiverse Sources
W: Failed to fetch [http://ftp.utexas.edu/ubuntu/dists/hardy/Release](http://ftp.utexas.edu/ubuntu/dists/hardy/Release)  Unable to find expected entry  partner/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by kaizokuroof on 2010-03-31
I'm fairly new but your repositories might be out of date or you could have repos that aren't there anymore. Since you're using an old system maybe try to find some repos that are still maintained, or update to a newer version of ubuntu.

Have you checked that you've enabled the updates in SYSTEM -> ADMIN -> Software Properties

kaizoku roof.

Hope it helps.

---

### Post by conradin on 2010-03-31
Hardy is still the LTS and will have support for another few years. take a look at this thread.
[http://ubuntuforums.org/showthread.php?t=1359853](http://ubuntuforums.org/showthread.php?t=1359853)

---

### Post by kaizokuroof on 2010-03-31
Open a terminal as root and ping your apt-resources mirror. then run in another terminal at the same time apt-get update. There is/was a bug with an older release that had this problem, let me know if this helps.

---

