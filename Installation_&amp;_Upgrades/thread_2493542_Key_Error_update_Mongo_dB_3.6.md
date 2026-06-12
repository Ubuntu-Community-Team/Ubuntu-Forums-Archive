---
title: "Key Error update Mongo dB 3.6"
date: 2023-12-18
forum: Installation &amp; Upgrades
---

### Post by mhojonz on 2023-12-18
Attempting to sudo apt update and receive the following error.
Ign:10 [https://repo.mongodb.org/apt/ubuntu](https://repo.mongodb.org/apt/ubuntu) bionic/mongodb-org/3.6 Release.gpg
Reading package lists... Done
W: GPG error: [https://repo.mongodb.org/apt/ubuntu](https://repo.mongodb.org/apt/ubuntu) bionic/mongodb-org/3.6 Release: The following signatures were invalid: EXPKEYSIG 58712A2291FA4AD5 MongoDB 3.6 Release Signing Key <packaging@mongodb.com>
E: The repository 'https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/3.6 Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Tried a couple of thngs but no sucess. 

```
                         wget -qO- https://www.mongodb.org/static/pgp/server-3.6.asc  | sudo tee /etc/apt/trusted.gpg.d/ server-3.6.asc
  
```

and


```
sudo apt-key adv --keyserver hkps://keyserver.ubuntu.com --refresh-keys
```

Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
Executing: /tmp/apt-key-gpghome.4GSz9uSJGI/gpg.1.sh --keyserver hkps://keyserver.ubuntu.com --refresh-keys
gpg: refreshing 4 keys from hkps://keyserver.ubuntu.com
gpg: key 871920D1991BC93C: "Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>" not changed
gpg: key D94AA3F0EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: key 7721F63BD38B4796: 2 duplicate signatures removed
gpg: key 7721F63BD38B4796: "Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>" 1 new signature
gpg: key 58712A2291FA4AD5: "MongoDB 3.6 Release Signing Key <packaging@mongodb.com>" 1 new signature
gpg: Total number processed: 4
gpg:              unchanged: 2
gpg:         new signatures: 2

---

### Post by mhojonz on 2023-12-18
Looks like the key has expired..

MongoDB 3.6 Release Signing Key
Email: [email]packaging@mongodb.com[/email]
This key has expired

Public Key
Key ID:    58712A2291FA4AD5
Algorithm:    RSA
Key Size:    4096
Created:    14/12/16
Expiry:    09/12/23
Capabilities:    Sign&#8232;Certify
Owner trust:    Unknown
Fingerprint:    29 30 AD AE 8C AF 50 59 EE 73 BB 4B 58 71 2A 22 91 FA 4A D5
User ID
Name:    MongoDB 3.6 Release Signing Key
Email:    [email]packaging@mongodb.com[/email]
Created:    10/12/18

---

### Post by MAFoElffen on 2023-12-18
Since You are running 18.04, which reached end-of life on May 31, 2023, and running MongoDB 3.6 was released back in 2017, and reached it's end of life back in April 2021... MongoDB current is 7.0... 

Yes. Good luck with that. I would think that that signing key would not be getting updated.

---

### Post by mhojonz on 2023-12-19
This is required for running Unifi. I have since learned current version of Unifi will run on MongodB 4.4 so have upgraded to this.

---

### Post by MAFoElffen on 2023-12-19
In their own community... Installing Unifi onto Ubuntu 22.04 with Current MongoDB: [https://community.ui.com/questions/Installing-UNIFI-network-controller-on-ubuntu-22-04/91356229-4ef2-4b2c-951f-cb39c35a8519](https://community.ui.com/questions/Installing-UNIFI-network-controller-on-ubuntu-22-04/91356229-4ef2-4b2c-951f-cb39c35a8519)

---

