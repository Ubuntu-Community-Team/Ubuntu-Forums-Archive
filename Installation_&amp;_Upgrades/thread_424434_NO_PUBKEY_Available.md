---
title: "NO PUBKEY Available"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2007-04-26
Is this a problem?
------------------------------------------
sudo aptitude update

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

roger@roger-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
roger@roger-desktop:~$

---

### Post by STREETURCHINE on 2007-04-26
you cant use dapper automatix for feisty install or dist upgrade.

you have to uninstall the dapper and install the feisty version(and dont forget to remove the dapper ones from the source.list

---

### Post by Vorian on 2007-04-26
you should be able to get help at the automatix forum [http://www.getautomatix.com](http://www.getautomatix.com)

also see [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

### Post by zvacet on 2007-04-27
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


gpg --keyserver hkp://subkeys.pgp.net --recv-keys CC919A31E23C5FC3
 gpg --export --armor CC919A31E23C5FC3  | sudo apt-key add -

---

