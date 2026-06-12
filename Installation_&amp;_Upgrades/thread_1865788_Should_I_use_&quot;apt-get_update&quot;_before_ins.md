---
title: "Should I use &quot;apt-get update&quot; before installing ubuntu-suggested updates?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by newhere_m on 2011-10-20
I use ubuntu 10.04 LTS. Just after installation, I got a message from ubuntu asking me to download and install some packages (security related and others). (These suggestions are also available from system>administration>update manager) I did that but before that I have not used the command "sudo apt-get update". Did I make any mistake? In case I did, is there any way to rectify?

---

### Post by ajgreeny on 2011-10-20
Just to make certain the "sudo apt-get update" command just refreshes the repos in your system to make sure that everything that can be upgraded is included.  The command does exactly the same as hitting the **Refresh** button in synaptic or the **Check** button in the update manager.

If you don't refresh manually that way, the system will check automatically each day, by default and notify you with the update notification, so you will normally only be one day behind at most.

---

