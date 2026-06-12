---
title: "Update-manager bug"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by homeriq5 on 2009-03-23
I was wondering if anyone was getting this error with update manager after you open it:

```

'E:Problem parsing dependency Depends, 
E:Error occurred while processing konqueror-plugin-adblock (NewVersion1), 
E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-amd64_Packages, 
E:The package lists or status file could not be parsed or opened.'

```

I updated at some point yesterday, and I got this when I tried updating again today.  As a result I cant update my system anymore, which makes me nervous.  I've posted this on launchpad at [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/347233](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/347233)

---

### Post by homeriq5 on 2009-03-23
no one?

---

### Post by exploder on 2009-03-23
Looks like you are running Kubuntu. I am not getting any errors in Ubuntu. Sorry I can't be of any more help...

Try sudo apt-get update
sudo apt-get upgrade

---

### Post by paul_in_london on 2009-03-23
Try these commands:

sudo rm -vf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo aptitude update && sudo aptitude upgrade

---

