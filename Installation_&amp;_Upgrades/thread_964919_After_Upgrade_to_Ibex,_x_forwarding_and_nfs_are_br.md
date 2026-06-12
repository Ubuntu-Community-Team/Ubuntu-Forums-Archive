---
title: "After Upgrade to Ibex, x forwarding and nfs are broken"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by ooshlablu on 2008-10-31
After i upgraded from hardy to Ibex on several of my servers, nfs and x forwarding over ssh stopped working. When i log into the server and try to run any x command (gedit, nautilus, etc) it gives me this garbage:

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-7k5gB0Xxal: Connection refused

I have no idea what to do about that, i've looked everywhere.

NFS is also acting weird on all of the servers that received the upgrade:
All machines that did not receive the upgrade and are still hardy can mount the shares fine, all the machines that are Ibex, which give me the error above, all of them, give nfs.internal error with no output no many how -vvvvvvvvvvvvvvvvv's you throw after mount.

I don't know what to do, and I am very disappointed with ibex so far. All of the ibex machines have the exact same errors listed above.

Any help is appreciated.

---

### Post by ooshlablu on 2008-11-01
hate to bump, but anybody got any ideas?

---

### Post by ooshlablu on 2008-11-01
NFS problems are solved, but I'm still having problems with the gconf orbit error, any ideas?

I've noticed that some people on the forums are having the same errors on boot with nm applet and nautilus, so I'm wondering if anyone knows if this is an official bug or not.

---

### Post by ooshlablu on 2008-11-04
still no ideas?

---

### Post by psquared89 on 2008-11-07
Had the same problem here.  Found the solution here ( [http://ubuntuforums.org/showthread.php?t=933181](http://ubuntuforums.org/showthread.php?t=933181) ), look at the edit to the post - not intuitive.

The problem is the permission of the ~/.dbus directory, it's owned by root, not the current user (not sure if there's good reason for that, but nothing seems to be broken by changing it, and if the directory is in your home directory, you were probably meant to own it).

Solution:

sudo chown -R <user>:<user> ~/.dbus

You may also want to file a bug report on this, probably against dbus.

---

### Post by ooshlablu on 2008-11-08
Thanks for pointing me in the right direction. Chowning was the first step, and chmod jackpot was the second. Thanks for the help.

To sum up for anyone who's browsing and might have the same errors listed above:

The problem has to do with the ownership and permissions of the .dbus folder in your home folder.

Crack open a fresh terminal and set ownership of .dbus to your username:

sudo chown -R <username>:<username> ~/.dbus


Try the broken app, and see if it works. If it doesn's, then allow complete global permissions to the folder:

sudo chmod 777 ~/.dbus

Everything *should* now work.


Feel free to post if anyone has more issues or input.

---

