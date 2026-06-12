---
title: "How to upgrade to Samba 4.3.3"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by Naxxramas on 2016-01-11
Ubuntu 14.04 LTS
Samba version 4.1.6-Ubuntu

Samba team haven't updated their PPA for a long time so I tried it from third parties but it doesn't work. I haven't been updating DLNA as well for over a year. The only option is to install from source. I'm quite confused whether I have to install from scratch or follow upgrade procedures. A detailed guide would be most helpful :D

---

### Post by edmondtherriault on 2016-03-05
I'm also in this boat. windows 10 needs 4.3.5 installed as it has newer packages. I have compiled the newer version but even thou it says it is installed it never does. I downloaded samba 4.3.5 from their site, unzipped it and ran the following to make it:

```

./configure
sudo make
sudo make install

```

Also before you do that run this to install all libraries 
```

sudo apt-get install acl attr autoconf bison build-essential debhelper dnsutils docbook-xml docbook-xsl flex gdb krb5-user libacl1-dev libaio-dev libattr1-dev libblkid-dev libbsd-dev libcap-dev libcups2-dev libgnutls28-dev libjson-perl libldap2-dev libncurses5-dev libpam0g-dev libparse-yapp-perl libpopt-dev libreadline-dev perl perl-modules pkg-config python-all-dev python-dev python-dnspython python-crypto xsltproc zlib1g-dev

```

---

### Post by Trismegister on 2016-08-18
Now Ubuntu 16.04 installs Samba Version 4.3.9 by default.

---

