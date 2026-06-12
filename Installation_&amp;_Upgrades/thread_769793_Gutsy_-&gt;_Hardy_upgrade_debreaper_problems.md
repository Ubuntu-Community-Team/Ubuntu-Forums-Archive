---
title: "Gutsy -&gt; Hardy upgrade: debreaper problems"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by x1a4 on 2008-04-26
Hi,

I just used the Update Manager to upgrade from Gutsy to Hardy and have encountered my first problem.

During the upgrade, a package named **debreaper** either didn't install fully, or wasn't removed fully.  Right now it's half installed and prohibiting me from installing/removing packages.  When I try to install or reinstall it, I receive a message that this package doesn't exist.  When I try to remove it I get the following: 

[size=-1]
Writing extended state information... Done
(Reading database ... 215712 files and directories currently installed.)
Removing debreaper ...
Removing `diversion of /usr/lib/libgnomeui-0/gnome_segv2 to /usr/lib/libgnomeui-0/gnome_segv2.orig by debreaper'
dpkg-divert: error checking `/usr/lib/libgnomeui-0/gnome_segv2': No such file or directory
dpkg: error processing debreaper (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 debreaper
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Exit 255
[/size]

How do I go about fixing this?  Thank you.

---

### Post by x1a4 on 2008-04-26
Nevermind.  I solved it.  I created a directory called /usr/lib/libgnomeui-0/ then created an empty file called gnome_segv2 in it, then I purged debreaper, and dpkg was able to delete the file and the purge progressed well.

---

