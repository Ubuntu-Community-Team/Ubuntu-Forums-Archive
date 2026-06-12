---
title: "MythTV install error!"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by Donshyoku on 2005-06-20
I have just recently gotten a TV tuner and booted up Ubuntu to try it out.  I searched the web and found that MythTV is housed on the Ubuntu multiverse repository.  So I added the repository, and went into Synaptic to install the program.  Then, I got an error, so I went to the terminal to install it and it resulted in the same error (who would have guessed!? :razz:).  I am fairly new to Linux, and most of all to Ubuntu.  The bulk of what I know is what I have learned from the Ubuntu documentation.  

Can someone decifer this error and propose a solution?

----------
Setting up mythtv-database (0.17-3) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.17-3); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------

Thanks in advance! :)

---

