---
title: "Dropbox install error after changing username in ubuntu 14.04"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by lovedynasty on 2015-03-12
Dropbox was working fine until I had to change the ubuntu username and now when I try to start dropbox with dropbox start command in terminal, dropbox says The Dropbox daemon is not installed! However, I have installed the daemon from using the instructions of the Dropbox website.

In any case when I try to install the daemon, with dropbox start -i, - which freezes while unpacking at 20% and gives the following information in an errorbox

Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable in an error box. To this end, the host and hostname had my previous username which I have changed but still no avail. 

I have no proxy set. 

The error in the terminal is:
  *'Starting Dropbox...[Errno 26] Text file busy:  '/home/myusername/.dropbox-dist/dropbox-lnx.x86*64-3.0.5/library.zip''

which is similar to [https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/818014](https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/818014) which seems to have been fixed. Anywork around?

---

