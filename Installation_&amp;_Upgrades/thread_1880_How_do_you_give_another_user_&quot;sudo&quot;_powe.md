---
title: "How do you give another user &quot;sudo&quot; powers"
date: 2004-10-23
forum: Installation &amp; Upgrades
---

### Post by emperor on 2004-10-23
When you create a new user, he does not get "sudo" powers. How do I go about giving another user "sudo" powers. I need to sync my UID's to my server which start at 500 (RH9) not 1000. Installing NIS seems like over-kill for a home network! But I will if I have to!

---

### Post by jmings on 2004-10-23
[QUOTE=emperor]When you create a new user, he does not get "sudo" powers. How do I go about giving another user "sudo" powers. I need to sync my UID's to my server which start at 500 (RH9) not 1000. Installing NIS seems like over-kill for a home network! But I will if I have to![/QUOTE]

For the UID problem see [http://www.ubuntuforums.org/showthread.php?t=1874](http://www.ubuntuforums.org/showthread.php?t=1874) .
For the sudo problem:
man sudo

---

### Post by emperor on 2004-10-24
After following the instructions, I could not login to the user account, as Gnome shutsdown with errors. It turns out the the owner of the hidden files in the users directory did not get changed. So, there needs to be an additional step:

chown -R username /home/username/.* 

Thanks for the short-cut method to change the uid!

---

### Post by emperor on 2004-10-25
Here's the answer to my orginal question about giving "sudo" powers to another user. You should use "visudo" to edit the "sudoers" file. The last statement in the file is the key!

root@linXos:/etc # cat sudoers
# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
yourusername    ALL=(ALL) ALL

---

