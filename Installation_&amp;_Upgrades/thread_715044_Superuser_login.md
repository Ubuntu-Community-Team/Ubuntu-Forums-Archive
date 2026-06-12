---
title: "Superuser login"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Meizulo on 2008-03-04
I just upgraded from 7.04 to 7.10. I have to run: 
"sudo apt-get remove powernowd"

When I try to run this command I get the following:
E: dpkg interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Then I run:
dpkg --configure -a

It then says:
dpkg: requested operation requires superuser privilege

How do I login as a superuser so that I can start to correct the problem?

---

### Post by luisromangz on 2008-03-04
You don't (and shouldn't) log in as root. The sudo command's purpose is to allow you to run a command with superuser privileges (provided you are allowed to do so in the sudoers file). So what you should do is:

sudo dpkg --configure -a

By the way, you used sudo when uninstalling powernowd...

---

