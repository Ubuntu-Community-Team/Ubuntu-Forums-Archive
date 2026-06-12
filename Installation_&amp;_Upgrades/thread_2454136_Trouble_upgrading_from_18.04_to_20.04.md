---
title: "Trouble upgrading from 18.04 to 20.04"
date: 2020-11-23
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2020-11-23
Upgrading my current 18.04 installation to 20.04 fails.

The log file is here: [https://pastebin.com/BNDbJNyD](https://pastebin.com/BNDbJNyD)

Suggestions on what the problem could be and what I can do is appreciated.

Thanks!

---

### Post by CelticWarrior on 2020-11-23
You have lots of PPAs. Try disabling them all first.

---

### Post by michael351 on 2020-11-23
Unable to disable using software updater GUI (permission denied). what is the command line syntax to disable all PPA's?

---

### Post by CelticWarrior on 2020-11-23
Again, open Software & Updates > Other software and remove or deselect them there. This should be enough.
The command to remove PPAs is the some as to add them but with --remove argument.

---

### Post by michael351 on 2020-11-23
O.k. - I used synaptic and was able to uncheck all of the PPA's.

Upgrade still failed:

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

I'll paste the logs to pastebin shortly

---

### Post by ajgreeny on 2020-11-23
Thanks for creating this new thread; it will make life a lot less confusing for all of us.
Please note also, that I have attempted to clean up the older thread that was hijacked and many posts from that are now jailed and out of public view.

I suspect that as well as disabling all the PPAs you had in 18.04 that you  ay also need to uninstall the packages that were added by those PPAs as the packages pulled in by them may still be interfering with your upgrade.

I suggest you install ppa-purge in your 18.04 system and use that to clean up the OS before attempting the upgrade again.

---

### Post by michael351 on 2020-11-23
It would be good to "learn" what the upgrade process didn't like about my existing 18.04 system.

Here is the latest log: [URL="https://pastebin.com/CFXJ908H"]https://pastebin.com/CFXJ908H
libsane seems to be a problem, but removing it 
[/URL]wants to remove ubuntu-desktop as well.

---

### Post by michael351 on 2020-11-24
Here is the main.log from the attempted 20.04 upgrade:
[https://pastebin.com/EYJGFUU2](https://pastebin.com/EYJGFUU2)

I don't know what to try next. Thanks for any help.

---

