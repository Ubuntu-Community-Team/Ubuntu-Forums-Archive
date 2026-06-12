---
title: "Cannot add PUBKEY"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2012-08-15
Good morning to you,


I tried to add a pubkey, but it fails many times, connection is good, but cannot connect to the server:

PS: I am using Ubuntu Desktop 10.04

> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1DB8ADC1CFCA9579  $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1DB8ADC1CFCA9579 Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 1DB8ADC1CFCA9579 gpg: requesting key CFCA9579 from hkp server keyserver.ubuntu.com gpgkeys: HTTP fetch error 7: couldn't connect to host gpg: no valid OpenPGP data found. gpg: Total number processed: 0


Thanks for your help

---

