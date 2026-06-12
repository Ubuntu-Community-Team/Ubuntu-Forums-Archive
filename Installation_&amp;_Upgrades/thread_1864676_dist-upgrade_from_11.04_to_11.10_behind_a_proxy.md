---
title: "dist-upgrade from 11.04 to 11.10 behind a proxy"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by rakete on 2011-10-19
I had problems with the dist-upgrade behind my companys webproxy.

Solutions found in the www were not really helpful. Of course I had set the proxy anywhere possible (apt.conf, .profile)

Somehow the apt-get dist-upgrade, do-dist-upgrade and update-manager failed to find the Release Information and threw some "404 Network problems" Errors.

To my surprise the command 
```
sudo update-manager -p
```started the update-manager somehow different and I was able to start the dist-upgrade. I am not quite sure what the -p parameter does differently from all the other commands, but it must be something. I put this up on here in case someone else behind proxys finds this information useful.

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

