---
title: "Cloned Linux Partition Alongside Windows"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by gmjs on 2012-02-04
Hello,

Does any one know of a good way to clone a Linux partition over a network to machines that already contain a Windows partition and set up GRUB or LiLo to be able to boot either OS?  Easily? :)

Clonezilla appears to do this, but I've yet to find a way to customize it so that I can set the boot menu up exactly as I would like (can you add custom commands after clonezilla has finished?)

```


Grub
---------------------------------
|                               |
|  1. Windows 7                 |
|                               |
|  2. Ubuntu 10.04              |
|                               |
---------------------------------

```

plus, compared to Windows Deployment Services, it's not that automated.

If anyone administers a production, dual-booting software lab, it'd be great to hear how you clone your machines.

I'm interested in free (cost) software utilities only and in using an existing Linux partition image (and not reinstalling the Linux OS).

Many thanks for any suggestions.

---

### Post by oldfred on 2012-02-06
I have not done any of this, but saved these links.

Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

Document system backup or multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

Multiple installs with rsync.
[http://askubuntu.com/questions/5938/how-can-i-do-mass-installs-on-multiple-computers](http://askubuntu.com/questions/5938/how-can-i-do-mass-installs-on-multiple-computers)

---

