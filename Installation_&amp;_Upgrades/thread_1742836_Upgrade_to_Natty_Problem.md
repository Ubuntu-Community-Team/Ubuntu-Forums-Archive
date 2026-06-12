---
title: "Upgrade to Natty Problem"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by tICT on 2011-04-29
Problem upgrading (possibly) to Natty

I've tried to upgrade my laptop, but get the error below.

> Could not determine the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
Can not mark 'xubuntu-desktop' for upgrade 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 

I think maybe I am on a pre-release, but get mixed messages; About Ubuntu reports:

> You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.

/etc/apt/sources.list indicates Maverick
/etc/issue indicates Ubuntu 10.10

If I am on a pre-release how can I change to stable/production?

I do have Chrome 12.0.742.9 dev from a Google repository and Firefox 4 from the Mozilla repositories. Are either of these likely to be the cause of the error? Which one?

Cheers

---

### Post by dino99 on 2011-04-29
> **tICT said:**
> Problem upgrading (possibly) to Natty


/etc/apt/sources.list indicates Maverick
/etc/issue indicates Ubuntu 10.10

Cheers

so : sudo gedit /etc/apt/sources.list
then:
- comment all third parties repo if any
- change "maverick" by "natty"
- save it

into a terminal:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

note: the servers are very busy right now, so better to wait for next week

---

### Post by pathennessy on 2011-05-13
I experienced this same issue.  The problem was because I had originally installed ubuntu-desktop and then used apt-get to install xubuntu-desktop later.  The upgrade won't proceed with two -desktop packages.  Removing the ubuntu-desktop package allowed the upgrade to proceed.

---

### Post by kn0w-b1nary on 2011-05-13
I did this:

sudo apt-get remove xubuntu-desktop

Then proceeded to upgrade.

---

