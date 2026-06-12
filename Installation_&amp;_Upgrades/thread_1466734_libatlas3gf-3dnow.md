---
title: "libatlas3gf-3dnow"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by sibyphilips on 2010-04-30
HI,
I upgraded to Lucid this morning, however there were some problems saying that libatlas3gf-3dnow was not installed. But to my surprise the system is working fine...it seems to be a crash of the update manager. 
My problem is that...

1) when I log in to UBUNTU now it shows warnings and a lot of messages on the screen before getting into the splash screen....

2) when I try to uninstall some programs from the UBUNTU software center it shows the following message (pasted at the end of the message) and exits...without completing the process...it seems the libatlas is a big problem...

3) in the synaptic when i checked the 'libatlas3gf-3dnow' is installed...

so what really is the problem...I think you guys out there can help me...

thanks in advance.

siby



installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 360277 files and directories currently installed.) 
Removing aisleriot ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Processing triggers for python-support ... 
Setting up libatlas3gf-3dnow (3.6.0-24ubuntu1) ... 
dpkg: error processing libatlas3gf-3dnow (--configure): 
 subprocess installed post-installation script returned error exit status 30 
dpkg: dependency problems prevent configuration of libatlas-3dnow-dev: 
 libatlas-3dnow-dev depends on libatlas3gf-3dnow; however: 
  Package libatlas3gf-3dnow is not configured yet. 
dpkg: error processing libatlas-3dnow-dev (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 libatlas3gf-3dnow 
 libatlas-3dnow-dev 
Setting up libatlas3gf-3dnow (3.6.0-24ubuntu1) ... 
dpkg: error processing libatlas3gf-3dnow (--configure): 
 subprocess installed post-installation script returned error exit status 30 
dpkg: dependency problems prevent configuration of libatlas-3dnow-dev: 
 libatlas-3dnow-dev depends on libatlas3gf-3dnow; however: 
  Package libatlas3gf-3dnow is not configured yet. 
dpkg: error processing libatlas-3dnow-dev (--configure): 
 dependency problems - leaving unconfigured

---

### Post by stckfrm on 2010-09-05
I'm running Lucid as well and I've been having exactly the same problem. I'm getting a little desperate.

The official bug report is here: [https://bugs.launchpad.net/ubuntu/+source/atlas/+bug/613338](https://bugs.launchpad.net/ubuntu/+source/atlas/+bug/613338)

..which redirects to this bug: [https://bugs.launchpad.net/ubuntu/+source/atlas/+bug/505339](https://bugs.launchpad.net/ubuntu/+source/atlas/+bug/505339)

..which provides no help or solution whatsoever.

Has anyone come up with some way to fix this? It's causing all kinds of problems.

---

### Post by winglog on 2012-09-17
I upgraded from Ubuntu 9.10 to Ubuntu 10.04 (Lucid Lynx) and then again upgraded to Ubuntu 12.04 LTS (Precise Pangolin).
Afterwards, I ran into the same problem when I was trying to install packages like octave etc.
Then, I took a look into the file "/etc/apt/sources.list" and saw that there were still some lines containing the word "Lucid". I commented out all these lines such that only lines containing "Precise" remained. Afterwards, I ran 

sudo apt-get clean
sudo apt-get update

and "libatlas3gf-3dnow" was not even there anymore in my package list of the synaptic manager. Nor does any other package miss it so far! This solved my problem.

---

