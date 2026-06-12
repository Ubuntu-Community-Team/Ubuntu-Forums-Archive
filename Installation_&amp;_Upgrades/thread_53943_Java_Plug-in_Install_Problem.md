---
title: "Java Plug-in Install Problem"
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by HKDan on 2005-08-02
Greetings all!

I'm new to Linux (but an old "DOS prompt" man) and am trying to get Ubuntu configured with all the plug-ins and extras I need.  The only one that won't install is the Java plug-in for Firefox.

I executed the: "apt-get install sun-j2re1.5" command in the root terminal but the system says it "couldn't find the package."

Can anyone direct me to the right syntax/package name?

Thanks so much!

Dan...Hong Kong

---

### Post by Omnios on 2005-08-02
Did you add extra Repositories

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) 

 ALso if you already did the repositories did you sudo apt-get undate to update the lists

 If all else fails you can use add remove programs (Synaptic) and search sun "sun-j2sdk1.5"

---

### Post by sk545 on 2005-08-02
You probably don't have the correct sources.list.  Try mine:

=====================

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted

==============

The sources.list is in /etc/apt/sources.list.  Just back that up, then make a new sources.list and put the above in it.  Then to apt-get update, apt-get install jre-blah.blah.

---

