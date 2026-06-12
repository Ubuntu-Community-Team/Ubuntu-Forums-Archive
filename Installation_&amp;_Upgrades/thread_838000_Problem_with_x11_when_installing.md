---
title: "Problem with x11 when installing"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by motapa on 2008-06-23
Hello all. I have recently migrated to Ubuntu from Fedora, trying to run away from its bugs, especially since I am using Linux for office use and not currently developing the platform. But I am experiencing problems with it. Whenever I try to install tar balls (.tar.gz, or .tar.bz2), they all complain about the existence of X11. The following are two of the messages I get;


checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

when installing scribus and kbluetooth.

I have tried to include all X directories in the $PATH variable in my .bashrc file, and have configure the pkg-config variable to: /usr/lib/pkgconfig:/usr/local/lib/pkgconfig but nothing works. What should I do.

By the way when I export the $PKG_CONFIG_PATH variable this is the message I get:

"export $PKG_CONFIG_PATH
bash: export: `:/usr/lib/pkgconfig:/usr/local/lib/pkgconfig': not a valid identifier".

Thank you all in advance. I am using Dapper Ubuntu.

---

