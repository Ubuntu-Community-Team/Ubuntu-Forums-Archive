---
title: "No Flash in 10.10?"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by Maybach on 2010-11-30
Hi, I've just upgraded to 10.10 and Flash doesn't work. I've tried following the thread re Flash installation off Adobe website and ended up with this message:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

What is this? The vlc is already installed.

Thanks.

---

### Post by bobyl573 on 2010-11-30
common error,

Originally Posted by sikander3786 
Add the missing GPG key by

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
And then,

Code:
sudo apt-get update

goodluck

---

