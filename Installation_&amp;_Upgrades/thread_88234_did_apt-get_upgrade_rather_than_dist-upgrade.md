---
title: "did apt-get upgrade rather than dist-upgrade"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by labrador on 2005-11-09
I followed the wiki notes on upgrading from Hoary to Breezy and made
a boo-boo: I used *apt-get upgrade* rather than *apt-get dist-upgrade*  

The first thing I noticed is that a bunch of things didn't get updated.  I saw the common advice about xserver-xorg reconfigure and getting a new xorg-driver-fglrx and did those.  Then today I did the *apt-get dist-upgrade* once I realized my mistake.  It downloaded many more files, but then bombed out when it said there was a conflict with mythtv-database. I uninstalled mythtv-database but couldn't find a way to resume the upgrade in progress.

I've since removed and reinstalled ubuntu-base and ubuntu-desktop, since I was having problems with X running nicely.  There were missing fonts and it wasn't very stable.  I've reconfigured xserver-xorg several times.  Using the fglrx driver, my system freezes hard.  Can't even ssh in sometimes.

I'm looking for a set of switches for apt-get that will just reinstall and reconfigure everything, from the current set up I have running. I played around with --reinstall and -f and that doesn't do what I thought it would.
Are there are any suggestions for repairing this system?

---

### Post by aysiu on 2005-11-09
There may be a way.
If I were in your situation, I'd back up my /home folder (or better yet, recreate it as a separate /home partition) and just reinstall. It's less trouble, I think.

---

### Post by matthew on 2005-11-09
I think you can go ahead and do a ```
sudo apt-get dist-upgrade
```now. If you still have problems with xserver after that then try to reconfigure it again ```
sudo dpkg-reconfigure xserver-xorg
``` 
As a last resort you can reinstall using Breezy.

I am hoping you already backed up all your data before you began the upgrade process so that ayisu's sage advice about backup before reinstalling is moot.

---

### Post by labrador on 2005-11-25
Hi,

I just remembered to follow up with my solution from weeks ago.

I did a forced reinstall of ubuntu meta packages ubuntu-base and ubuntu-desktop

That forced the rest of the packages that had been stalled, to be now updated following
the first conflict that the earlier 'apt-get upgrade' ran into.

Then for sanity sake, I did a reinstall of all packages found on the system.

On other bulletin boards they suggest running this in Debian:
[FONT="Courier New"]dpkg --get-selections | awk '{if ($2 == "install") print $1}' | xargs apt-get -y --reinstall install[/FONT]

However that won't work because of a bug in apt not being able to handle a huge args list like that.

So the workaround mentioned in the Debian bug report is a solution.
Dump the package names to a file, and feed them to apt-get --reinstall install with a shell for loop.

---

### Post by doclivingston on 2005-11-25
[QUOTE=labrador][FONT="Courier New"]dpkg --get-selections | awk '{if ($2 == "install") print $1}' | xargs apt-get -y --reinstall install[/font]

However that won't work because of a bug in apt not being able to handle a huge args list like that.[/quote]

You can pass "-n N" to xargs, where N is the number of arguments to pass. So   [FONT="Courier New"]dpkg --get-selections | awk '{if ($2 == "install") print $1}' | xargs -n 10 apt-get -y --reinstall install[/font]   would reinstall 10 packages, then another 10, and so on until they are all done.

---

### Post by az on 2005-11-25
What non-ubuntu repositories do you have?

First, do

sudo apt-get -f install
to settle any unresolved comflicts.

Then remove any non-ubuntu repositories, update and try the dist-upgrade.

Try putting your non-ubuntu repos back and reinstalling what you need form them.

---

