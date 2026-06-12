---
title: "Setting up language-support -  dpkg --configure -a"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by mkanar on 2008-07-24
I uninstalled KDE packs in my desktop environment as described in 
"Ubuntu 7.10: How to Uninstall KDE" [http://www.tech-recipes.com/rx/2755/ubuntu_7_10_how_to_uninstall_kde](http://www.tech-recipes.com/rx/2755/ubuntu_7_10_how_to_uninstall_kde).

Then check sources list 
  [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy ....

I got this

Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/multiverse Sources
Fetched 4B in 2s (1B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Program aborted due to repository failures.

I dried to fix the problem with 

sudo dpkg --configure -a && sudo apt-get -f
Setting up language-support-ca (1:6.06+20060529) ...
Generating locales...
  ca_AD.UTF-8...             

My filling this that deleted the language support.

Can somebody help my?

---

### Post by Partyboi2 on 2008-07-24
> sudo dpkg --configure -a && sudo apt-get -f
Setting up language-support-ca (1:6.06+20060529) ...
Generating locales...
  ca_AD.UTF-8...              Does this finish generating the locales? It can take a little time.

---

### Post by mkanar on 2008-07-25
No, it stops at this point and doesn't continue onwards.
I let it run for about an hour as I had to go out and pick up some things, and it hadn't moved when I checked on it upon my return.

Obviously Synaptic is frozen.

---

### Post by Partyboi2 on 2008-07-25
You could give post #3 a go in this [[COLOR=Blue]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=865679").

---

