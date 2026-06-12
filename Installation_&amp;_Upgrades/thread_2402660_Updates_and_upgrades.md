---
title: "Updates and upgrades"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by aubertinsylvain on 2018-10-03
Hi all ! I should like very much someone explains to me updates and upgrades.I see 2 cases:
 1st deletes the whole old and then installs the new.
 2d handles differences of old to new (probably with reads and writes). Thanks in advance.
For instance I have problem with "bluetooth", entering my photos inside  the PC. On Linux. I should like to do that with the terminal, but where  to find the name for that application(understood by the terminal) ?

---

### Post by oldos2er on 2018-10-03
Are you referring to *sudo apt update* and *sudo apt upgrade*? apt update refreshes your /etc/apt/sources.list and any *.list files in /etc/apt/sources.list.d/. According to the man page apt upgrade 

```
upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages currently installed on the system from the
           sources configured via sources.list(5). New packages will be installed if required to satisfy dependencies,
           but existing packages will never be removed. If an upgrade for a package requires the remove of an installed
           package the upgrade for this package isn't performed.
```

Not sure what this has to do with bluetooth.

---

### Post by TheFu on 2018-10-03
What do you know about updates and upgrades?  

Google found this: [https://wiki.ubuntu.com/SoftwareUpdates](https://wiki.ubuntu.com/SoftwareUpdates) & [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) & [https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/) There is a simplified table in the 3rd link with cmds and what each does.  There are always the manpages for each specific program too.  apt-get manpage is fairly detailed.  

Updating software on Linux works differently than on Windows.

I can't help with bluetooth.  Won't touch that stuff and purge it from all my systems.

---

