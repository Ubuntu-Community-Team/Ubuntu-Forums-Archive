---
title: "Can't upgrade, missing release notes"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by bfallik on 2011-10-20
I'm trying to update my PC from 10.10 to 11.04 and then 11.10 but I'm stuck on the first step.

update-manager complains that it "Could not find the release notes".  When I run d-release-update from the command line, I see:
```
$ sudo do-release-upgrade 
Checking for a new ubuntu release
Err Upgrade tool signature                                                     
  404  Not Found [IP: 91.189.92.190 80]                                        
Err Upgrade tool                                                               
  404  Not Found [IP: 91.189.92.190 80]                                        
Fetched 0B in 0s (0B/s)                                                        
WARNING:root:file 'natty.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 

```

Networking is otherwise fine.  I can use update-manager and apt-get to query packages and perform updates.

Help!

---

### Post by zvacet on 2011-10-21
I don´t know if this will help but try to put your system up-to-date 

```
sudo apt-get update && sudo apt-get upgrade
```

See if you can upgrade after that.

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

### Post by geoffp on 2012-02-23
I was having a similar problem upgrading from Oneiric. Running ppa-purge on all PPAs, and then removing them one by one with software-sources fixed it.

---

