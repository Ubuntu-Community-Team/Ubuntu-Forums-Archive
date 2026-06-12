---
title: "dpkg lock"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by avdiel1946 on 2014-07-28
Recently when I tried to upgrade the Ubuntu 14.04 OS, there appeared the error messages

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I fix this. More importantly, what did I do to create this problem?

thank you....

---

### Post by ian-weisser on 2014-07-28
Only one package manager (Software Center, Synaptic, Update Manager, aptitude, apt-get, dpkg, etc.) application can be in use at a time. You can have lots *open*, but only one can be *in use* and actively downloading/installing/uninstalling.
The system uses a lock file (/var/lib/dpkg/lock) to enforce which application can manage packages right now.

If you get the message, there are three possibilities:

A) Another application has the lock right now. Another package manager is still open or actively working. Wait for it to finish and close it.

B) On rare occasions you might get this message if Ubuntu is doing it's daily/weekly security updates in the background. Simply wait for it to complete. (mine take ~3-4 minutes each week)

C) On very, very rare occasions, your system crashed (or your did an unclean shutdown, or you lost power) while a package manager was operating and had the lock. Youmay need to manually remove the lock, and you may also need to repair your system.


How to fix it:

1) **Waiting** will almost always fix A) and B) without any further action needed.

2) **Close all of your package-managing applications** (Software Center, Synaptic, Update Manager, aptitude, apt-get, dpkg, etc.).
Then check to make sure you *still* don't have a package manager running.

Example:
```
$ ps -e | grep apt
24674 pts/4    00:02:06 apt-get
```
Uh-oh. In this example, apt-get *is* running! I should return to Step 1 and wait for it to finish.

3) If you are *really sure* that no other package manager is running, and that the lock is a mistake, you can remove the lock manually.
WARNING: Doing this while a package manager is trying to download/install/uninstall packages can BREAK YOUR SYSTEM!
```
$ sudo rm /var/lib/dpkg/lock
```

---

### Post by avdiel1946 on 2014-07-28
apt-get is running with time; 107:05:41. Last update was yesterday. Cannot remove /var/lib/dkpg/lock. Same error messages.

---

### Post by ian-weisser on 2014-07-28
The following will try to shut down apt-get gracefully.
```
sudo pkill -1 apt-get
```

Then check the ps command again to see if apt-get is still running.
If it is still running, try again with the -5 flag instead of the -1 flag.
If still running after that, try again with the -9 flag. -9 is the nuclear option - I don't use it lightly. 

Once apt-get has stopped, try running a package manager function check.
```
sudo apt-get update && sudo apt-get upgrade
```
If there are package or system errors, then please post the complete terminal output here.

If you still get a lock error, then remove the lock manually (the previous warnings still apply!)
```
$ sudo rm /var/lib/dpkg/lock
```
And try the package manager function check again.

---

### Post by avdiel1946 on 2014-07-29
still cannot remove /var/lib/dpkg/lock. dpkg --configure -f seems to have fixed the problem. thanks for the help.

---

