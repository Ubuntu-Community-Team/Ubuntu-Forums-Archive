---
title: "Ubuntu 22.04 to 24.04 Upgrade - Interrupted"
date: 2024-09-04
forum: Installation &amp; Upgrades
---

### Post by 13l-jason on 2024-09-04
I went to upgrade my system over the weekend as I do every time a new LTS version is available. Go figure, we had a brief power outage in the middle of it. System boots, and brings me to the desktop, but doesn't allow me to log in. I get an error stating "Something went wrong" and tells me I must log out. I can login to bash though (alternate tty), no issues there. Once in there, when attempting to continue the update (apt upgrade), it tells me I have broken packages. I attempt the fix (apt --fix-broken install), it lists all the stuff it can't do and doesn't seem to actually do anything. Networking isn't working. When running ifconfig, I get the loopback, but no other interfaces. I suspect that if I can get networking back online, I can probably get the packages fixed. Recovery mode doesn't seem to help.

Any thoughts where to go from here?

BTW, I've been running this installation since 14.04, upgrading with each new LTS. I'd hate to have to reinstall now.


Thank you

Edit:  Some additional info.  It appears the network interface name has changed.  The command ifup seems to want to bring up the original interface (en0pxxxxx).  Using "ip link eno1 up" allows me to bring up the interface with a new name, but ipv4 doesn't seem to start.

---

### Post by sloancli on 2024-09-08
Definitely in dangerous territory, so make sure to pull a backup before starting these steps.

Switch to another TTY just as before. 

First, try letting the system run the upgrades again: ```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Reboot, and if still not working, let's get dpkg involved.

Create a list of all packages on the system: ```
dpkg --get-selections | awk '{print $1}' > list_packages
```

Tell dpkg to reconfigure all of them: ```
sudo dpkg -c list_packages
```

If there are any errors or problems during the process, they'll be logged in `/var/log/dpkg.log`. Check these logs for a detailed understanding of what went wrong.

Give it a try and let me know.

---

### Post by ajgreeny on 2024-09-08
This may now be too late to help you enough but very recently the LTS to LTS upgrade path was withdrawn due to some critical bugs.
I regret I don't know how to help you more as I never version upgrade but perform a clean install every time.

See [https://www.omgubuntu.co.uk/2024/09/canonical-halts-ubuntu-24-04-lts-upgrades-again](https://www.omgubuntu.co.uk/2024/09/canonical-halts-ubuntu-24-04-lts-upgrades-again) for more information which I hope explains all even if it does not solve your current problem.

---

### Post by s-witzel on 2024-09-14
I'm in a very similar situation as the OP. There is no hope for the apt commands as the network is down. The dpkg command is not what it's supposed to be: "-c" lists the contents of a deb-package. Like the OP I think the main challenge is to get the network back up. Does anyone have suggestions on how to do that or on how to track down the problem?

---

