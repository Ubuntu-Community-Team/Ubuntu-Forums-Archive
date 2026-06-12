---
title: "Update manager hangs"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by drkeuk on 2007-04-28
I'm trying to upgrade from edgy to feisty using update manager as explained here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

All went well until 5 minutes before the end of "fetching and installing the upgrades" when, apparently, the system is configuring mysql-server-5.0. The upgrading hangs now and the update manager is unresponsive. What can I do? Interrupt the process? But how? And what's next?

---

### Post by az on 2007-04-28
Stop the upgrade manager and run

sudo apt-get dist-upgrade in a terminal and post the output.

It may ask you to run

sudo apt-get -f install

or 
sudo dpkg --configure -a

If so, post the output of those commands.

---

### Post by drkeuk on 2007-04-28
How can I stop the update manager? It is unresponsive. 

When I sudo apt-get dist-upgrade in a terminal (while update manager is still open but unresponsive) the response is:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by drkeuk on 2007-04-28
I finally decided to xkill the update manager window and started the update again. It resumed and finished the upgrade with some scary errors. When I finally restarted the computer, it booted into a 7.04 feisty system. Thanks for the help, az.

---

### Post by az on 2007-04-28
Be sure to run synaptic again and fix any broken packages (or run sudo apt-get -f install from the command line) just in case there are any packages that have not finised their installation.

---

