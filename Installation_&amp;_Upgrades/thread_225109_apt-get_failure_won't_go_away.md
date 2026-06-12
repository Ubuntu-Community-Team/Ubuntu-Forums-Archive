---
title: "apt-get failure won't go away"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by NetJumper on 2006-07-29
Hi.  I'm new to Ubuntu and only have some experience with linux. I have installed Ubuntu 6.06 AMD64 and the base install went well as well as such things as getting wine working, getting nvidia in sli working and installing chroot to have 32bit Ubuntu.

Now the problem:
I misstyped during an install of mythtv resulting in failure to setup the database, and now I have that failed install haunting me.  Every apt-get or synaptic operation gives me the following:

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up mythtv-database (0.18.1-5ubuntu3) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have followed every tip to clear a failed install including dpkg-reconfigure --force mythtv-database but this won't go away!  mythtv has been removed and purged and I have run apt-get remove -f but it still won't go away.

HELP!

Any help will be appreciated.

---

### Post by NetJumper on 2006-07-30
Hi all.
Just before I was about to re-install Ubuntu I came across the following thread:

[http://www.ubuntuforums.org/showthread.php?t=39563&highlight=package+install+error](http://www.ubuntuforums.org/showthread.php?t=39563&highlight=package+install+error)

Follwing the advice in that thread from Ramaddan and removing every file and directory containing the name *myth* removed the problem.  Warning - you need root priviledges, and if you're not careful can do major damage.
Rather than keep typing 'sudo' for everything, I entered root user by using 'sudo su'
Afterwards I used 'apt-get clean' and 'apt-get update' to clean things up.
 
(Sorry to all for whom this is old news ...)

---

