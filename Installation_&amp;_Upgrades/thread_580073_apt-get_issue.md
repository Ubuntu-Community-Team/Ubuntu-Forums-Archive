---
title: "apt-get issue"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by wombatsix on 2007-10-18
Just installed GG Server version - I'd like to get KDE running as opposed to the cmd line interface.

My first roadblock occurs here:

I'm logged in using the default account created during installation....

I use "sudo apt-get install x-window-system-core"  (since I understood that KDE needs this when installing into a server load)

I get the error  "  my-acct is not in the sudoers file.... this incident will be reported..."

What have I missed?

Thanks.

---

### Post by mattpker on 2007-10-18
It is teling you the issue...

my-acct is not in the sudoers file.... this incident will be reported...

This means that the user you are logged into it not aloud to use the sudo command.  Please su to another user that can our just log on as root. Don't use the default user for the instalation.

---

