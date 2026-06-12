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

---

### Post by EndPerform on 2007-06-09
> 
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
Could not connect to au.archive.ubuntu.com:80 (211.29.132.173), connection timed out
etc...
etc...
W: Some index files failed to download, they may have been ignored, or old ones used instead.


This means that apt cannot connect to the repository, it's timing out, so it can't perform an update since it can't get to the repository.  That may also be causing your original issue.

---

### Post by moore.bryan on 2007-06-09
[I]try taking off the "au" from the repo address; that should fix things.
;-)
[/I]

---

### Post by Scroopy on 2007-06-09
Thanks for the suggestions guys,,, but it didn't work

---

### Post by moore.bryan on 2007-06-11
*was there an error after removing the "au?"*

---

### Post by madmetal on 2007-06-11
> **moore.bryan said:**
> [I]try taking off the "au" from the repo address; that should fix things.
;-)
[/I]

au means that he is using the australian (?) mirror of repos..
like i do with greek mirror and got a gr. ;)
if you want to change server go to synaptic and from menu settings >> repos 
change the option at "Download from : "

---

### Post by moore.bryan on 2007-06-11
*yeah, i know... that's why i suggested dropping the "au," so you wouldn't use one of the mirrors.*

---

