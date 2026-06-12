---
title: "no keyserver"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2011-04-19
Hi. Along with many others, I have found it impossible to get a response from the keyserver. Having googled about, I am now using the old method of getting a ppa. 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9CB8DB0

This has worked once, and I have managed to install libre office. However, now I am trying to install wine 1.3 and nothing works, not even other keyservers.

sudo apt-key adv --recv-keys --keyserver hkp://subkeys.pgp.net F9CB8DB0
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver hkp://subkeys.pgp.net F9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

 sudo apt-key adv --recv-keys --keyserver hkp://pgp.mit.edu F9CB8DB0Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver hkp://pgp.mit.edu F9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

I'm out of ideas. Can anyone help please.

---

### Post by plucky on 2011-04-19
Never mind missed **not even other keyservers.**

Although ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9CB8DB0
``` just worked for me.

---

### Post by triplemaya on 2011-04-19
Well, thanks for that, but this does not help me! I have just tried them all again, and each one times out. So, my request is, could someone please help me to get it to work for me!

---

