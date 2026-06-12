---
title: "Updating a distribution over a remote connection (SSH)"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2008-08-06
Is it possible for a remote SSH user to log into an ubuntu system and upgrade its distribution?  My parents prefer to run Ubuntu on their system instead of Windows but they do not know how to update it when I"m away; I have a sudo-enabled account on it and an easy to remember hostname.

I'm wondering how to upgrade a distribution over the command line (since I've always upgraded using the GUI within X.)

---

### Post by pytheas22 on 2008-08-06
You could edit your /etc/apt/sources.list file to use the repositories of whichever distribution you want to upgrade to.  Then run:
```

sudo apt-get update #to update the package list
sudo apt-get upgrade
```

and it should upgrade you to the latest distribution.  Note that I've never actually done this myself so I can't guarantee that it will work, but in principle it would.

Also, you could always forward a Gnome session over ssh, as long as the machine you're working from is also running Linux (or has X11 installed if it's a Mac or Windows).  You just need to run ssh with the -X flag:
```

ssh -X you@yourparentscomputer
```

Once you log in, type:
```

gnome-session
```

to launch a Gnome session over the remote connection.  Note that it may be quite slow, but as long as you have decent Internet connections on both ends, it should be usable.  If not, look into vnc, which would be faster.

Finally, a warning: I've found (from personal experience and reading the forums) that things tend not to go smoothly when trying to upgrade to the next version of Ubuntu over the Internet.  If you're not there to personally troubleshoot problems that may arise from the upgrade, you may want to not upgrade your parents' system until you're home.  Or you may want to consider keeping their /home directory on a separate partition, and doing a fresh install of Ubuntu each time a new version is released--that's what I do and it works well for me.

---

