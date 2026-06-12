---
title: "Upgrade to 24.04 just... doesn't..."
date: 2024-07-17
forum: Installation &amp; Upgrades
---

### Post by mobrien118 on 2024-07-17
I have a system that was originally Ubuntu 8.10 and has been upgraded (hardware and software) through just about every version up through 23.10. This has been my daily use desktop for all that time, although I've added a Windows laptop a few years back and have a Windows VM on this machine that I also use.

I've faced dozens of upgrade issues over time and have managed to successfully navigate them and get back to a working system. Now I'm faced with the strangest I've ever seen.

When I try to perform a "do-release-upgrade" from the command prompt, the upgrade just suddenly stops without any error output...
```
Checking package manager
Reading package lists... Done    
Building dependency tree... Done 
Reading state information... Done

Calculating the changes

Calculating the changes
=== Command detached from window (Thu May 23 21:46:18 2024) ===
=== Command terminated with exit status 1 (Thu May 23 21:46:18 2024) ===
```

After that, the apt repos (.list files) are ***left referring to the new repos*** but no packages are updated, so I roll them back to the backups it made before the upgrade started, manually.

When I try to upgrade via the desktop popup box it simply disappears and does nothing - doesn't even attempt to start the upgrade or check for new repos.

I guess the first thing I need to know is where upgrade logs would be stored for clues. I've never had to dig before because upgrades have always either worked or given a clue as to what the problem might been.

---

### Post by TheFu on 2024-07-17
Logs are under /var/log/.  

I think you've been lucky.  Upgrades from 8.10 over the decades and working. Wow.  I do 1 upgrade LTS-->LTS, then the next LTS release, it is a fresh install to clean out the cruft that gets left behind.  I suspect you have far too much cruft from all those upgrades left.  Lots of subsystems have changed.  Cruft doesn't get removed.  Does the system use resolvconf or manual /etc/resolv.conf file or systemd-resolved at this point?  I wouldn't want to guess.

Didn't the format of the repos change between 22.04 and 24.04?  I'm asking, because I vaguely remember reading about the changes. [https://linuxconfig.org/ubuntus-repository-configuration-ubuntu-sources-have-moved-to-etc-apt-sources-list-d-ubuntu-sources](https://linuxconfig.org/ubuntus-repository-configuration-ubuntu-sources-have-moved-to-etc-apt-sources-list-d-ubuntu-sources) Looks like the file name/location has changed as did the format. It is very different now. Hopefully, they made it backwards compatible for PPAs, but IDK.

---

### Post by Dennis N on 2024-07-17
> When I try to upgrade via the desktop popup box it simply disappears and does nothing
This could mean that the 23.10 system was not fully upgraded before starting the upgrade to 24.04. 
Upgrading 23.10 is still possible, so check that it is fully upgraded.  I just checked with a 2310 VM I have installed and it updated (using the United States Server on Jul 17. 2024). On conpletion, I get an offer to upgrade to 24.04. I did not use the terminal for any of this.

_Update:_
If you get as far as the screenshot, your upgrade should go through should you continue. I backed out here (I don't need another 24.04).

---

