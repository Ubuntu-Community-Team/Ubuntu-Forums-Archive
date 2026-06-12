---
title: "where is inetd.conf in ubuntu-server 5.10?"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by luxxing2000 on 2005-10-18
Hi all
After I install the ubuntu-server 5.10 in a new machine,I can't find inetd.conf and xinetd.conf in /etc,how can I get them back?
I only download the ubunut-server CDimage.

---

### Post by adwait on 2005-10-18
There is a direcotry /etc/init.d/ which has symlinks to all the commands run on boot, if that's what you are looking for. I am not really sure what inetd.conf does.

Anyway, on my machine the inetd.conf sure is there in the /etc/ directory.

---

### Post by luxxing2000 on 2005-10-19
resolved!
inetd.conf is not installed by default.

use this command:
sudo apt-get install netkit-inetd

---

