---
title: "Unifi-beta 4.6.3 and Ubuntu 15.04 fails install - has anyone made it work?"
date: 2015-07-02
forum: Installation &amp; Upgrades
---

### Post by Aero_Nexcom on 2015-07-02
[COLOR=#333333][FONT=Helvetica Neue]I recently upgraded to 15.04 on ubuntu from 14.10. Unifi-beta was working on Ubuntu 14.10 on my machine.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]I have discovered that the Unifi software will no longer start. It turns out it failed on install.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]when trying service unifi restart the response is[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]"Failed to restart unifi.service: Unit unifi.service failed to load: No such file or directory."[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]On attempting to uninstall Unifi-beta, it wont let me do it no matter how I force it. The only method I found was to delete all the unifi directories in /var & /usr and the files in the /etc/init.d & rc directories. Then run apt-get autoremove to clean up the system.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]I reinstalled from the repositories on and got the same answer.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]ran [/FONT][/COLOR]
```
[COLOR=#333333][FONT=Helvetica Neue]apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up unifi-beta (4.6.3-4850) ...
Failed to start unifi.service: Unit unifi.service failed to load: No such file or directory.
dpkg: error processing package unifi-beta (--configure):
subprocess installed post-installation script returned error exit status 6
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]


```[COLOR=#333333][FONT=Helvetica Neue]has any had success installing Unifi-beta (4.6.3) on Ubuntu 15.04?[/FONT][/COLOR]

---

