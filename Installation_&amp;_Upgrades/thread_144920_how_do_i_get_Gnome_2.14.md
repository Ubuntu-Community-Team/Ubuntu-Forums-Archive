---
title: "how do i get Gnome 2.14?"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by risknothin on 2006-03-15
Will it be updated soon? will the update manager take care of it?

---

### Post by John.Michael.Kane on 2006-03-15
Upgrade to dapper if your looking for gnome 2.14.

---

### Post by SpEcIeS on 2006-03-15
Look at the Dapper testing area. This will provide Gnome 2.14, which has some really nice improvements. Good luck :)

---

### Post by risknothin on 2006-03-15
its not available for breezy?

---

### Post by SpEcIeS on 2006-03-15
No. Comment out the Breezy lines and add Dapper lines to you apt repo.

Here..   

In terminal:

1) sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak

2) sudo gedit /etc/apt/sources.list

3) Comment out all breezy lines, if not sure comment them all out

4) add the below lines to the sources.list
[b]# Dapper testing
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse[/b]

5) Exit gedit and use sudo apt-get dist-upgrade and find something to do for a while

6) Once complete.   reboot

Everything should be fine. :D


Dapper Drake time :)

---

### Post by Klaidas on 2006-03-15
would that make ubuntu unstable as dapper is now?

---

### Post by Xian on 2006-03-15
[QUOTE=risknothin]its not available for breezy?[/QUOTE]

No, unless you want to compile the envrionment locally. The official Ubuntu Gnome 2.14 packages are in the Dapper repos. If you include those repos in your source list and upgrade you will be running Dapper.

---

### Post by risknothin on 2006-03-15
i dont understand why gnome 2.14 is not available for the current ubuntu.

Can someone explain?

---

### Post by calimarno on 2006-03-15
That's the same reasons because you can't run Firefox 1.5 on Breezy : after a release, the Ubuntu version is frozen except for security bugs (that's also why a backport team exists)

---

### Post by Xian on 2006-03-15
[QUOTE=risknothin]i dont understand why gnome 2.14 is not available for the current ubuntu.
[/QUOTE]

It is available for the current Ubuntu, which is Dapper. However, it is not officially available for Breezy since that would introduce a level of uncertainty and instability to that particular release. It is not simply a matter of installing a suite of newer versioned Gnome packages on top of an already existing desktop environment. It also requires a newer set of many libraries and runtime files, which could in turn could impact many system underpinnings.

---

### Post by SpEcIeS on 2006-03-15
This is the nature of Ubuntu. Every version change reflects the Gnome release. Just do yourself a favor and do a dist-upgrade if you are wanting to use Gnome 2.14. 


If you can wait until April then do so, but I could not. :)

---

### Post by Xian on 2006-03-15
Unless there is something specific you need in 2.14 don't even worry about it. It is ridiculous to just upgrade versions when things are working fine and there is no other compelling reason. People get too apt-happy about these types of things.

---

### Post by SpEcIeS on 2006-03-15
That is sort of true, but Gnome 2.14 does have some really good improvements. GSlice, which seems to improve overall performence..  well for the apps that use it. :)

Also, Firefox 1.5.0.1 is a nice improvement... :) Many others too..  go on give it a go, but remember to back up your personal data first..  just in case. ;)

---

### Post by JayMan8081 on 2006-03-17
If it's possible for someone to build KDE packages whenever a new KDE is released why is it not possible to do the same thing for Gnome?  I don't want to have the instability of using Dapper yet, but would like the Gnome update.

---

### Post by SpEcIeS on 2006-03-17
Why not just try and build it yourself. Use this garnome package, but read the instructions first. DO NOT install it over the previouse installation, ie /usr

**[http://ftp.gnome.org/pub/GNOME/sources/garnome/2.14/garnome-2.14.0.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/garnome/2.14/garnome-2.14.0.tar.bz2)**

To try out the latest KDE, 3.5.1, I am building it and installing in the /opt directory.

---

### Post by Slurm on 2006-03-17
Yes but rumor has it (as of either slashdot or madpenguin) that Dapper is going to be delayed by 6 weeks from its original release.  I have not been able to confirm this on ubuntu's homepage, but Shuttleworth gave some valid points in its delay.  So now we are looking at June 1st. 

Can anyone confirm or deny this??

Slurm

---

### Post by SpEcIeS on 2006-03-17
This is apparently true, but I cannot point you to the article that indicated it. However, I did read something with regards to the tardy nature of dapper. I am not really clear on what the major hang-ups are? 

On my box the, using dapper, I cannot seem to use the automount feature in nautilus. Prior to thursdays update it was working fine, but no one seems to know why. <???> Also, I have been trying to install KDE 3.5.1 using konstruct, but it seems to error off at xine-libs, and all of the dependancies are installed. I even used alternate compilers, but no go. Perhaps there is an error in the devs? 

I have consulted a very knowledgeable individual that is very familiar with compiling source and in particular xine, but he did not seem to know what to do either.

Well this is what you get when you use an unstable release. :-D

_Edit_
Figured out the automount issue :)

---

