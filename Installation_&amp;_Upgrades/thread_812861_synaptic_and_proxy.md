---
title: "synaptic and proxy"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by Carlbc18 on 2008-05-30
I think this is a known issue, but i use this computer at work and at home.  When I am home i don't want to connect via the proxy.  I have removed it from "netwrok proxy" and from the browser settings which allows me to browse the web, but Synaptic errors out with the below error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to <proxy address: 80> (1xx.xx.xx.xx), connection timed out

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> 0:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to <proxy address: 80>  (1xx.xx.xx.xx), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Unable to connect to<proxy address: 80> 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to<proxy address: 80>  (1xx.xx.xx.xx), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to <proxy address: 80> :

W: Some index files failed to download, they have been ignored, or old ones used instead.


Thanks for any help!

---

### Post by zvacet on 2008-05-30
This is just a guess but in **synaptic>settings tab<settings>network>direct connection**

---

### Post by Carlbc18 on 2008-05-30
Zvacet - I thought that too, but i checked that and its blank.  I did check the apt config and there is an entry in there but the file is read only - could it be pulling it from there?

---

### Post by Carlbc18 on 2008-05-30
I figured it out, i had to edit the /etc/apt/apt.conf file and remove the proxy entry.  Then i did sudo get-apt update from the terminal, and everything started working including synaptic.

---

