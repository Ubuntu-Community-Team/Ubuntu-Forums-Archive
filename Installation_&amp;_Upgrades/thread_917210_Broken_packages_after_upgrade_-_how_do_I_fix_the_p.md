---
title: "Broken packages after upgrade - how do I fix the problems?"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by jhhoward on 2008-09-11
Since upgrading to Hardy I've had several package problems. When I run the update manager I get the following message:

"Not all updates can be installed
Run a partial upgrade, to install as many updates as possible"

If I choose to do a partial upgrade, I get the following error:

"Can't install 'ubuntu-desktop'
It was impossible to install a required package. Please report this as a bug"

The updates on the list in the update manager are unselectable and include:
* apturl
* brasero
* libgimp2.0
* orage
* tzdata

Even more frustratingly, the last update I did uninstalled Pidgin and it refuses to re-install. I get the following error when I try to install via the synaptic package manager:

pidgin:
  Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed

I really don't want to do a complete OS re-install but I don't have any ideas of how to fix the broken packages. Is there any way to fix these problems?

---

### Post by Pumalite on 2008-09-11
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by jhhoward on 2008-09-11
Thanks pumalite, that fixed the partial-upgrade nagging problem but I'm still having the dependency errors when trying to install pidgin.

Any ideas?

---

### Post by Pumalite on 2008-09-11
Post the outputs

---

### Post by jhhoward on 2008-09-11
james@znote:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  pidgin: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages

---

### Post by Pumalite on 2008-09-11
Go to Synaptic and 'Fix Broken Packages'. Then see if you can install Pidgin through Synaptic

---

### Post by jhhoward on 2008-09-12
I tried opening synaptic package manager and selecting edit -> fix broken packages but it didn't seem to do much. The status bar at the bottom reads "Successfully fixed dependency problems" but I still have exactly the same problem when I select pidgin to install.

I tried reinstalling the libpango package too, but this made no difference.

EDIT:
It seems that at some time during the update the 'hardy-backports' repositories got enabled (I'm not sure how, I don't remember ever enabling it) and this was causing the dependency problems. When I was trying to install pidgin it was trying to install from the backports repo but the libpango library was not available.

For anyone reading this post who needs a solution, I opened Synaptic Package Manager, and went to settings -> repositories and then went to the 'updates' tab and unselected 'Unsupported updates (hardy-backports)'

---

### Post by rainyu_2002 on 2008-11-23
Hi,

I have the same problem and solved by the following way,may be not best,but working way,

1.download pidgin from the following website,
[http://www.getdeb.net/release/3289](http://www.getdeb.net/release/3289)

2.install it with command,
dpkg -i --force-depends pidgin_2.5.2-1~getdeb1_i386.deb

3.working,enjoying.

Thanks for everyone.

---

