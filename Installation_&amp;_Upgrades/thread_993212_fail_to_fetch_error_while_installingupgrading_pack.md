---
title: "fail to fetch error while installing/upgrading packages"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by trickytoad on 2008-11-25
hi, i m using ubuntu 8.04. When i tried to update my machine, couple of the packages are not been been downloaded coz of the error much similar to the following.

When i tried to reinstall firefox 3.0 through Synaptic package manager, i got the following error.

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found

Please help me in solving the above error.

---

### Post by trickytoad on 2008-11-26
help..! help..! help..!

---

### Post by trickytoad on 2008-11-30
Fixed with the following command.

sudo apt-get check
sudo apt-get clean

---

### Post by buckrodgers on 2008-11-30
trickytoad thanks for postiong the solution of your problem, I have a similar issue, I tried your fix but this did not work for me :(
```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  Unable to find expected entry  paner/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.heanet.ie/pub/ubuntu/dists/intrepid/Release  Unable to find expected entry  paner/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.heanet.ie/pub/ubuntu/dists/intrepid-updates/Release  Unable to find expected entry  paner/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.heanet.ie/pub/ubuntu/dists/intrepid-security/Release  Unable to find expected entry  paner/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.heanet.ie/pub/ubuntu/dists/intrepid-proposed/Release  Unable to find expected entry  paner/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.heanet.ie/pub/ubuntu/dists/intrepid-backports/Release  Unable to find expected entry  paner/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by buckrodgers on 2008-11-30
Works now, I removed all the reference to "paner" in /etc/apt/sources.list something seems to have gone wrong during the update & somme rubish went in the sourcelist.

---

