---
title: "/lib/modules/2.6.22-14-server/build is missing, please set KERNELPATH."
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by wvsint on 2007-10-22
I update from 7.04 server to 7.10 using the normal update procedure via up-date managerf.
Besides the normal up-dates no 7.10 message popped up.
After that I typed:

sudo apt-get install update-manager-core
and
sudo do-release-upgrade

after final installation, the system restarted.

Now I tried to install MADWIFI and HPLIP.
Both times I received the message: 
/lib/modules/2.6.22-14-server/build is missing, please set KERNELPATH.  Stop.

Is this normal, or is this a bug.
I 've googled this issue and came up with nothing. I cannot believe that I am the only one

Must I do a complete new install of 7.10 server ?

Thank you

WVSINT


ANSWER, I missed the command:

$ sudo apt-get install linux-headers-$(uname -r)



And now it works.

Thank you

---

