---
title: "Updating an out of date package?  (Nagios3)"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by DigitalMocking on 2011-02-13
I installed Nagios via package install a few weeks back and started configuring it to work in my network, and its been going great. The package version is somewhat out of date however, being 3.2.1 and the newest version (3.2.3) has a number of enhancements and bug fixes I'd like to make use of.
 
The problem I have is that the ubuntu package spreads the nagios install all over the place, and I don't know how to update an installed package with downloaded source.
 
Is there any reasonably easy way to get my installed package up to 3.2.3, or should I scrap the package and just go with source and start transferring my configuration files over?
 
Thanks.

---

### Post by dino99 on 2011-02-13
add this ppa to synaptic repo tab (third parties) then update

[https://launchpad.net/~nicolashennion/+archive/nagios](https://launchpad.net/~nicolashennion/+archive/nagios)

---

### Post by DigitalMocking on 2011-02-13
> **dino99 said:**
> add this ppa to synaptic repo tab (third parties) then update
 
[https://launchpad.net/~nicolashennion/+archive/nagios](https://launchpad.net/~nicolashennion/+archive/nagios)
 
Thanks Dino, I'm fairly sure I followed the directions right, but I'm not getting the upgrade.
 
I added the PPA:
```
root@monitor:~/nagios-3.2.3# add-apt-repository ppa:nicolashennion/nagios
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 03534CAA948AE8BECFD1209E7C2669AE5FB9F7A9
gpg: requesting key 5FB9F7A9 from hkp server keyserver.ubuntu.com
gpg: key 5FB9F7A9: public key "Launchpad nicolargo" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
 
then;
```
root@monitor:~/nagios-3.2.3# apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,745B]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [578B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages [14B]
Fetched 10.7kB in 1s (6,330B/s)
Reading package lists... Done
```
 
So it appears I've got the information about the new PPA packages, right?
```
root@monitor:~/nagios-3.2.3# aptitude upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```
 
Any idea what I'm doing wrong?

---

