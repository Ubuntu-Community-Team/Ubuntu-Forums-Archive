---
title: "Gnome-shell removed by accident, need help reinstalling"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2010-08-04
i had an earlier issue with a bad dependency, I clicked the red icon and it said to fix the problem it will remove the bad .deb and also update any programs. I saw my chrome had to be updated so I ok'd. As I watched it saw gnome-shell was removed. Now I know it's very important & if I logoff I am probably screwed but whenever I try to reinstall it the system won't let me. I am told this:

Quote:

$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages
Tried building the dependency & got this

Quote:
sudo apt-get build-dep gnome-shell 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages have unmet dependencies:
libgjs-dev: Depends: libgjs0 (= 0.5-1ubuntu2.2) but it is not going to be installed
Depends: xulrunner-dev (< 1.9.2.9~) but 1.9.2.9~hg20100803r34485+nobinonly-0ubuntu1~umd1~lucid is to be installed
E: Build-dependencies for gnome-shell could not be satisfied.
wordsmith@Ecanus:~$ sudo apt-get installgnome-shell 
E: Invalid operation installgnome-shell
wordsmith@Ecanus:~$ sudo apt-get install gnome-shell 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages

How can I fix this please?

---

### Post by akester on 2010-08-04
I found some information [here]("http://www.linux.com/archive/articles/48910").  Hopefully this info helps out.

---

### Post by maddbaron on 2010-08-04
> **akester said:**
> I found some information [here]("http://www.linux.com/archive/articles/48910").  Hopefully this info helps out.

did a google search and found this gnome-shell
[http://shibuvarkala.blogspot.com/2010/01/how-to-install-gnome-3-gnome-shell-in.html](http://shibuvarkala.blogspot.com/2010/01/how-to-install-gnome-3-gnome-shell-in.html) and added the ppa for it.

then i read the link u sent me and ran the commands and it said try aptitude force so i did and now it's installing the gnome-shell from the link above, I hope this helps me...

my concern is having to reboot and being unable too...

---

### Post by akester on 2010-08-04
gnome-shell is part of the gui so it no matter what you should be able to start.  If you need to drop the desktop the keys are Ctrl+alt+shift+F12 to go into a normal shell.

---

### Post by maddbaron on 2010-08-05
thanks for your help, i was able to reboot and everything seems fine. Thanks again!

---

