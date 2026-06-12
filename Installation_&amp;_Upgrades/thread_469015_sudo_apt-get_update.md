---
title: "sudo apt-get update"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Scroopy on 2007-06-09
Hello

I run the command:

sudo apt-get install traceroute

and I get the following message:

Reading package lists... Done
Package traceroute is not available, but is referrred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package traceroute has no installation candidate

I then run the command:

sudo apt-get update

and I get the following message:

Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
Could not connect to au.archive.ubuntu.com:80 (211.29.132.173), connection timed out
etc...
etc...
W: Some index files failed to download, they may have been ignored, or old ones used instead.


Can someone please help?

It was suggested that I delete the 'au.' in front of the addresses, but this did not work either.  I must add that I am running Ubuntu on VMWare Workstation 6.  I am able to ping to other machines, so I don't think it's a network issue.

---

### Post by zvacet on 2007-06-09
```
sudo aptitude update
```

If still no luck download it from here

[http://packages.ubuntu.com/dapper/net/traceroute]("http://packages.ubuntu.com/dapper/net/traceroute")

install dependecie first(it is mark with red ball)

---

### Post by Scroopy on 2007-06-10
that didn't work.  I'm still getting:

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
   Could not connect to security.ubuntu.com:80 (91.189.88.31), connection timed out
etc...
etc..

---

### Post by eentonig on 2007-06-10
Change the location of your repo's to one closer at where you live.

Either directly via editing the sources.list urls. Or via GUI.

System\Admin\Software Sources
 
On the first tap, you have an option "Download from", select "Other" and choose from the list.

Or let the system pick one for you. But this will take a long time, as it will try everyone of them in the list.
PS. This will only work for official Ubuntu repo's. So not the one you might have added yourself.

---

### Post by Scroopy on 2007-06-10
my menu system is as follows

System/Administration/Software Properties

There is no 'Software Sources" and there is no 'Download from" option either.

---

### Post by zvacet on 2007-06-10
Try to replace your source list with this one

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by Scroopy on 2007-06-11
I replaced sources.list with the suggested info,, but I still get the same error messages.  

I installed Ubuntu on my machine along side XP as a dual boot setup and I had no issues.  It only seems to happen on my virtual machine that I have set up on VMware.  I am able to ping from my virtual Ubuntu machine to other machines, so I don't think its a network issue.  

Any ideas?

---

