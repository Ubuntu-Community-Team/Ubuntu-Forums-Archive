---
title: "partial upgrade trouble"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by speadskater on 2007-10-19
Ok, so i was upgrading to gusty at school and I made the stupid decision to let my friend connect to a virtual desktop while i was upgrading.  Long story short the installation ended up being canceled.  Now when i try to update it tells me to do a partial upgrade.  I click ok and it gets frozen reading the cache and i have to force quit it.


Is there anyway to undo the upgrade and allow me to do the installation from the beginning?  I just don't want to spend the time getting the iso for the alternate install.

---

### Post by Pumalite on 2007-10-19
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update

---

### Post by Atolla on 2007-10-19
I have about the same issue. My upgrade from feisty to gutsy froze at some point during installation, the last line being "Stopping MySQL database server mysqld"
After restart, Ubuntu fails to run after loggin in I just get a screen without anything on it.
After trying to do dpkg --configure -a after starting in recovery mode, I get the following error: "chown: cannot access `var/run/mysqld': no such file or directory" and the process stops there.

Can you help me out?

---

### Post by speadskater on 2007-10-19
> **Pumalite said:**
> Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update

i did that... but it still wants to partial upgrade (there's like 1480 programs that need to be upgraded)

lets see if i can terminal upgrade it

would the script be:
sudo apt-get upgrade

?

---

### Post by Pumalite on 2007-10-19
See the 'sticky' on upgrades.

---

### Post by speadskater on 2007-10-19
see... i would... and i did do that code... but it gets stuck at the very last part of reading cache

---

### Post by botheredbybees on 2007-11-01
I ran the 3 commands listed above and returned to the update manager, which still said: "Not all updates can be installed. Run a partial upgrade."

I click on the Partial Upgrade button and the Distribution Upgrade window is displayed, which runs through a couple of tasks and then hangs on 'Reading cache' - any idea what to do next?

---

### Post by Pumalite on 2007-11-01
Try this:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by John_T on 2007-11-01
I have a similar problem to **speadskater** and **botheredbybees**.


I'm currently running 7.04, looking to upgrade to 7.10

Once I get to the partial upgrades, it's almost complete, but hangs at the "Distribution Upgrade".  I've left it to tick away for ages, but all useful information disappears from the dialog once the screens saver has gone away.

The system otherwise seems to be functioning normally.  Network is OK, media playing is OK, my VMware machine plays OK.  I just can't do anything in regard to package/distribution upgrade without getting stuck at this point.


I'd much appreciate any pointers.  I've gone from an expert Windows user to a Linux newb in next to no time.  I do however, know to ask the experts before tinkering at complete random!

---

### Post by botheredbybees on 2007-11-03
thanks Pumalite, but they were the 3 commands I already tried:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

still getting the partial upgrade notice and a hang on the distribution upgrade

---

### Post by botheredbybees on 2007-12-12
I finally got this one sorted out by clicking on the 'Mark all upgrades' button in the System->Admin->synaptic package manager

---

