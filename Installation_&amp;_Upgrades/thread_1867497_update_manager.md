---
title: "update manager"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by donhinrichs on 2011-10-23
for days the update manager worked just fine.  Now I get the following error message. The internet connection is working correctly and is connected
DMH  

Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by dino99 on 2011-10-23
you try an url that dont exist for oneiric !!! (just need to be curious and know how to google !!!)

[http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/](http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/)

so comment out these entries into /etc/apt/sources.list (or via synaptic or software center)

---

### Post by raja.genupula on 2011-10-23
> **dino99 said:**
> you try an url that dont exist for oneiric !!! (just need to be curious and know how to google !!!)

[http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/](http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu/dists/)

so comment out these entries into /etc/apt/sources.list (or via synaptic or software center)

+1 
open your update manager ->settings-> at other software tab uncheck those following ppa's and reload .

All the best.

---

### Post by jds340 on 2011-10-23
<<<<<
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-30-generic_2.6.35-30.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-30-generic_2.6.35-30.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011k-0ubuntu0.10.10_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011k-0ubuntu0.10.10_all.deb) 404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.59_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.59_all.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30-generic_2.6.35-30.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30-generic_2.6.35-30.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
<<<
I get the above messages when I try to update to the latest patches. They look like they're from the standard repositories, but the files aren't in the locations discovered by the update manager. It sounds like a mis-configuration issue with the repositories.

---

### Post by raja.genupula on 2011-10-23
> **jds340 said:**
> <<<<<
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-30-generic_2.6.35-30.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-30-generic_2.6.35-30.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011k-0ubuntu0.10.10_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011k-0ubuntu0.10.10_all.deb) 404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.59_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.59_all.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30-generic_2.6.35-30.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30-generic_2.6.35-30.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
<<<
I get the above messages when I try to update to the latest patches. They look like they're from the standard repositories, but the files aren't in the locations discovered by the update manager. It sounds like a mis-configuration issue with the repositories.

ok change your server to other mirror from settings of update manager and try again .

All the best.

---

### Post by Old_Grey_Wolf on 2011-10-23
> **jds340 said:**
> <<<<<
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-30-generic_2.6.35-30.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-30-generic_2.6.35-30.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011k-0ubuntu0.10.10_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011k-0ubuntu0.10.10_all.deb) 404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.59_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.59_all.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30-generic_2.6.35-30.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30-generic_2.6.35-30.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.59_i386.deb) 404  Not Found [IP: 91.189.92.167 80]
<<<
I get the above messages when I try to update to the latest patches. They look like they're from the standard repositories, but the files aren't in the locations discovered by the update manager. It sounds like a mis-configuration issue with the repositories.

If changing the server didn't help then you will probably have a partial update which will need to be fixed before updating again. The updates to the packages in the error message are old and no longer on the server you were using. Enter these commands in the terminal to clean up partial updates, check for new updates, then update.
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

[http://www.upubuntu.com/2011/07/remo...e-404-not.html](http://www.upubuntu.com/2011/07/remo...e-404-not.html)

---

### Post by vasa1 on 2011-11-10
> **subehsharma said:**
> ...[http://www.upubuntu.com/2011/07/remo...e-404-not.html](http://www.upubuntu.com/2011/07/remo...e-404-not.html)
That link needs to be fixed.

---

### Post by subehsharma on 2011-11-10
> **Old_Gray_Wolf said:**
> If changing the server didn't help then you will probably have a partial update which will need to be fixed before updating again. The updates to the packages in the error message are old and no longer on the server you were using. Enter these commands in the terminal to clean up partial updates, check for new updates, then update.
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

> **vasa1 said:**
> That link needs to be fixed.

[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

