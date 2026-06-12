---
title: "Lowercase &quot;w&quot; not working after Ubuntu 14.04.1 LTS upgrade"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by Stephen_Kennedy on 2014-11-10
After upgrading to Ubuntu 14.04.1 LTS, the lowercase "w" letter isn't working, sounding an error bell.  I'm unable to type it on the keyboard, nor through a SSH session, nor paste it in an SSH session.  UPPERcase "W" **does **work however, and Ctrl+w does work at the command-line (to delete a word at a time backwards).  I've tried:

sudo dpkg-reconfigure console-data
sudo dpkg-reconfigure keyboard-configuration

...but that didn't resolve it.  Considering reinstalling from scratch.  All ideas welcome, please and thanks.

EDIT:  I tested a boot disk, and the w key works in a live ditribution.
EDIT:  I just discovered the lowercase "w" key does work in the Login prompt at command line, but after logging in successfully, it doesn't work, so it must be user account level problem.  Still, ideas are most welcome.  Thanks.

---

