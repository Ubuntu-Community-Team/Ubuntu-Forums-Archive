---
title: "Central Updates"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by Gordon D on 2012-04-15
I have a number of Ubuntu computers and was wondering if there is a way to download all the updates to a central server which would then distribute the updates to the other PCs.

At the moment, each PC has to download and apply its updates individually which can be time consuming and kills my ADSL.

I realise that my PCs are all different and have different hardware and software builds, but 90% of the updates seem to be the same.

Any ideas would be much appreciated.

Gordon

---

### Post by oldfred on 2012-04-17
I have not done any of this, but the question comes up so I have accumlated some links.

Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

Document system backup or multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

Multiple installs with rsync.
[http://askubuntu.com/questions/5938/how-can-i-do-mass-installs-on-multiple-computers](http://askubuntu.com/questions/5938/how-can-i-do-mass-installs-on-multiple-computers)
Up to 10 free
[http://puppetlabs.com/puppet/puppet-enterprise/](http://puppetlabs.com/puppet/puppet-enterprise/)
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

