---
title: "Post upgrade to 22.04 facing problem with package update"
date: 2022-05-05
forum: Installation &amp; Upgrades
---

### Post by bluepicaso2 on 2022-05-05
Hi,
I recently upgraded to 22.04 and since then I am facing to problems while using 
```
sudo apt update
``` and ```
sudo apt upgrade
```.

Running ```
sudo apt update
``` gives me following message, specially problem with slack package key
> 


Hit:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy-updates InRelease                                                                                                          
Hit:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy-backports InRelease                                                                                                        
Hit:4 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease                                                                                                      
Hit:5 [https://deb.nodesource.com/node_16.x](https://deb.nodesource.com/node_16.x) focal InRelease                                                                                                                 
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                                                                                                           
Hit:7 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease                    
Hit:8 [https://downloads.1password.com/linux/debian/amd64](https://downloads.1password.com/linux/debian/amd64) stable InRelease       
Reading package lists... Done                                                   
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: [https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease:](https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.


The other problem is with the 2 packages that are mention above for upgrade but are holded back.
Here is the output for ```
> sudo apt list --upgradable
```
> 
Listing... Done
libapache2-mod-php7.4/jammy 8.1.2-1ubuntu2 amd64 [upgradable from: 7.4.29-1+ubuntu20.04.1+deb.sury.org+1]
libapache2-mod-php8.0/jammy 8.1.2-1ubuntu2 amd64 [upgradable from: 8.0.18-1+ubuntu20.04.1+deb.sury.org+1]


These both are never upgraded. If i run ```
sudo apt upgrade
``` I get following
> 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libapache2-mod-php7.4 libapache2-mod-php8.0
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

The response is same with ```
sudo apt-get --with-new-pkgs upgrade
```

Please help

---

### Post by deadflowr on 2022-05-06
Try apt full-upgrade instead of plain apt upgrade

The problem with both *apt upgrade *and* apt-get --with-new-pkgs upgrade* is both of those will install new packages,
but neither can remove packages if the upgrade requires it.
apt full-upgrade can remove packages if the upgrade requires it to do so.
apt-get dist-upgrade can do this as well.

---

### Post by bluepicaso2 on 2022-05-06
> **deadflowr said:**
> Try apt full-upgrade instead of plain apt upgrade

The problem with both *apt upgrade *and* apt-get --with-new-pkgs upgrade* is both of those will install new packages,
but neither can remove packages if the upgrade requires it.
apt full-upgrade can remove packages if the upgrade requires it to do so.
apt-get dist-upgrade can do this as well.

Same issue, behaves as normal ```
sudo apt upgrade
```

---

