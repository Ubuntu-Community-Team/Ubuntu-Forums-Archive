---
title: "Install issues.  sources.list error   Please help"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2007-04-20
**SOLVED AT THIS STAGE**


Ok Tired to update using the recommended way, that failed.  Then tried alternate CD, that failed.   Tried the recommended way again and fail.   Nothing I have tried works, the update thingy is totally broken by the looks of it.   I really don't want to clean install and have to re apply all my settings and data.

Package Manager won't run.  Double click and get nothing.  Right click the icon and click 'install all updates' and it comes up with,

 An error occured
The following details are provided:
E: Malformed line 45 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.

I've been into the sources.list and nothing appears wrong but hey I'm no code freak so it could be.

Then I get this error messege:
Could not upgrade the system!
Fix broken packages first.


I also get this when trying to open Synaptic Package Manager and press reload:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preference


I NEED HELP PLEASE


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by sharke on 2007-04-20
It is telling you 2 things one off your repos has a problem try this
Sudo gedit /etc/apt/sources.list
If you do not have line numbers showing edit preferences and select line numbers.
Scroll to line 45 and comment out with # in front of line
For brocken pakages open synaptic select custom filters go up and select broken packages rigkt click and remove packeges.
Now try to upgrade you can only upgrade from edgy with the default way.
Regards
Sharke

---

### Post by slingre87 on 2007-04-21
I'm not quite sure where to post this, but here goes.

[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)

I have no idea if I need to edit the repo settings or what, but could someone please help me
thanx all

---

