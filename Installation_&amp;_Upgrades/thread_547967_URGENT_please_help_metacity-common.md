---
title: "URGENT please help metacity-common"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by Ripfox on 2007-09-10
error processing /var/cache/apt/archives/metacity-common
file list file for package 'gnome-panel' contains empty filename

This happened when an upgrade was interupted by a power failure...

any ideas? This is quite desperate due to time constraints.

---

### Post by Ripfox on 2007-09-10
dpkg: error processing metacity-common (--configure):
package is in a very bad inconsistent state - you should reinstall it before attempting configuration.

---

### Post by Pumalite on 2007-09-10
Have you attempted: sudo dpkg --configure -a
Synaptic>Edit>Fix Broken Packages
sudo dpkg --remove --force-remove-<packagename>

---

### Post by Ripfox on 2007-09-10
I did sudo dpkg --configure -a
but it gives me the error from my second post.

I will try the force remove on metacity-common

---

### Post by Ripfox on 2007-09-10
no go...

Any ideas?

---

### Post by Pumalite on 2007-09-10
You might try the following:
To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".
__________________

---

### Post by Ripfox on 2007-09-10
When I log into x, I get 

there was a problem registering the panel with bonobo-activation server
the error code is 3
the panel will now exit

AND

nautilus can't be used now, due to an unexpected error

bonobo canot register the file manager to view server

I don't want to reinstall!!:)

---

### Post by Ripfox on 2007-09-10
No time to search through it...thanks for the help.

Must reinstall I fear.

:(

---

### Post by Pumalite on 2007-09-10
It looks like your system is hosed my friend. Sorry.
Don't forget to backup home or use in new install if you have it in it's own partition.

---

