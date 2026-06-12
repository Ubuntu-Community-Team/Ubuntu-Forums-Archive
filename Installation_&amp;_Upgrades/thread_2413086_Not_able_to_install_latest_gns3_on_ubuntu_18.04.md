---
title: "Not able to install latest gns3 on ubuntu 18.04"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by class007 on 2019-02-21
Hi ,

Need support on installing latest GNS3 on Ubuntu 18.04 (FOLLOWING [https://launchpad.net/~gns3/+archive/ubuntu/ppa](https://launchpad.net/~gns3/+archive/ubuntu/ppa)) ..Tried installing it as below steps...got stuck...


sudo add-apt-repository ppa:gns3/ppa
[sudo] password for saks: 
 PPA for GNS3 and Supporting Packages. Please see [http://www.gns3.com](http://www.gns3.com) for more details
 More info: [https://launchpad.net/~gns3/+archive/ubuntu/ppa](https://launchpad.net/~gns3/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Error: retrieving gpg key timed out.


After getting this error message , tried manually downloading the key from [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/) and imported on software updater ...looks everything fine..again getting the same above mentioned timed out error message ..


Then Force it to use port 80 instead of 11371

gpg --keyserver [http://keyserver.ubuntu.com:80](http://keyserver.ubuntu.com:80) --recv-keys <kye>

The output looks like this...

gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys F88F6D313016330404F710FC9A2FD067A2E3EF7B
gpg: key 9A2FD067A2E3EF7B: "Launchpad PPA for GNS3" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


Still i m not able to install it (same timed out error message) ; What are the steps needs to be taken next to complete the installation of GNS3 on ubuntu 18.04...

Is there any other way to install GNS3 from source ..if so ,kindly post me the steps to follow...


thanks..

---

