---
title: "caribou upgrade issue (caribou_0.3.92-0ubuntu1_all.deb)"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by danielkraaij on 2011-10-19
A couple of days ago i upgraded from 11.04 to 11.10. My previous installed gnome-shell was unfortunately removed but this was easily reinstalled.

The online problem i came across is that everytime i run sudo apt-get upgrade it comes with the following.
  ```

daniel@workstation1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gnome-shell : Depends: caribou but it is not installed
E: Unmet dependencies. Try using -f.

```I tried to solve this as suggested

```
daniel@workstation1:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  caribou
The following NEW packages will be installed:
  caribou
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
1 not fully installed or removed.
Need to get 0 B/75.5 kB of archives.
After this operation, 1,126 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 181900 files and directories currently installed.)
Unpacking caribou (from .../caribou_0.3.92-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/caribou_0.3.92-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/caribou/layouts/scan/us.xml', which is also in package libcaribou-common 0.4.0-0ubuntu1~11.04~ricotz0
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 /var/cache/apt/archives/caribou_0.3.92-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone have an idea on how to resolve this issue?

---

### Post by garvinrick4 on 2011-10-19
> dpkg: error processing /var/cache/apt/archives/caribou_0.3.92-0ubuntu1_all.deb (--unpack):  trying to overwrite '/usr/share/caribou/layouts/scan/us.xml', which is also in package libcaribou-common 0.4.0-0ubuntu1~11.04~ricotz0
You still have some leftover of ricotz ppa you had installed or still have I do not know. 
Open synaptic and type in libcaribou and see if 0.4.0 is installed. Should be 0.3.92 is what I have. (ricotz ppa is more of the bleeding edge)

---

### Post by garvinrick4 on 2011-10-19
This screenshot in synaptic is what I have installed. (click on it)
Here are ppa's do you have one installed still in Software Sources?
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

---

### Post by danielkraaij on 2011-10-19
removing the libcaribou packages through synaptic seem to solve the problem. :) Thank you very much for helping me on this.

---

