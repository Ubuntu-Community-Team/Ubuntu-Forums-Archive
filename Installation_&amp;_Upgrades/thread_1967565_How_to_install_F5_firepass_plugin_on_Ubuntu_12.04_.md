---
title: "How to install F5 firepass plugin on Ubuntu 12.04 (precise pangolin)"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by timcredible on 2012-04-28
Just installed 12.04 (64 bit), had a difficult time getting the F5 firepass SSL VPN plugin working, thought I'd share this info so others could get it working also. 

First, you have to get the files.  The F5 website has instructions on that, but they're for the old firepass version (<=6.0) and old firefox (<=3.6).  They don't have anything for the new firepass (7.0) or new firefox (>=4.0).  So, if I find out how to get these files easily, I'll update this, but this is what I did since I knew it would work:

1 - Install firefox 3.6 (or temporarily run an older version of Ubuntu that has 3.6 by default, like 10.04, just to get the files you need)
2 - Run firefox 3.6 as root (on Ubuntu, open terminal and 'sudo su root', the 'firefox'
3 - Login to firepass and try to connect, this will automatically install the files you need
4 - The files you need are in /usr/local/lib/F5Networks (make sure if you copy from one system to another you copy all subdirectories and keep file permissions) and np_F5_SSL_VPN_x86_64.so (found under /root/.mozilla/firefox/<some unique string>/extensions/<some weird unique string in brackets>/plugins, which you should move to /usr/lib/mozilla/plugins so all users can use it and not just root.  If you're using a 32 bit system, you need np_F5_SSL_VPN_i386.so, which is in the same place.

Then you're done.  Also, another little note on the F5 firepass client, it doesn't work properly in a vm client system.  It's always best to run it on the host system and then NAT the client vm system.

---

### Post by timcredible on 2012-07-25
It was pointed out that I didn't specify, but you can go back to using the newest firefox after installing the plugin, you don't have to keep using 3.6.  3.6 is just used to get the plugin from the F5 firepass.

---

