---
title: "Automatically Configure Grub on apt-get upgrade outdated"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by brendan6 on 2013-01-16
I have a script that I run to setup a new machine to host Ruby on Rails applications.  The script is as follows:

```

#!/usr/bin/env bash
apt-get update
apt-get -y upgrade outdated
apt-get -y install build-essential zlib1g-dev libssl-dev libreadline6-dev libyaml-dev
cd /tmp
wget ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p125.tar.gz
tar -xvzf ruby-1.9.3-p125.tar.gz
cd ruby-1.9.3-p125/
./configure --prefix=/usr/local
make
make install
gem install chef ruby-shadow --no-ri --no-rdoc
mkdir /var/chef
reboot

```

This has worked perfectly in the past, however I am now getting a Configuring grub-pc dialog that I manually have to go through and select the valid options.  I was wondering if anyone knew of a way to set the necessary options via command line arguments so this dialog does not appear.  These machines get provisioned regularly and are run with ```
ssh root@165.225.145.74 'bash -s' < bootstrap.sh
``` so this dialog causes me to manually have to ssh in an run this script.

---

