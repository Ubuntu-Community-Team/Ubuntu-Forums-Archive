---
title: "Ubuntu 10.04 LTS main mirror problem"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by alphacrucis2 on 2011-10-04
I notice just now an apt-get update worked ok but a following apt-get upgrade listed 18 packages to be upgraded but they all returned error 404 file not found error. Anyone else getting this?

---

### Post by subehsharma on 2011-11-10
> **alphacrucis2 said:**
> I notice just now an apt-get update worked ok but a following apt-get upgrade listed 18 packages to be upgraded but they all returned error 404 file not found error. Anyone else getting this?

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

[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

