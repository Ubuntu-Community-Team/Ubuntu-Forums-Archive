---
title: "How to make Apt prefer a more recent virtual package over a real one"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2016-05-05
Hello guys,

I've recently built a package which provides multiple virtual ones, more specifically snmp which provides libsnmp-base, libsnmp30 and so on...
It is installed on my system & provided on my online PPA.
When I try to install another package (php7.0-snmp) which depends on libsnmp30 & libsnmp-base, Synaptics offers me to uninstall snmp in order to install the required dependencies.
It seems that Apt always prefers real packages over virtual ones, despite the facts that:
[LIST]
[*]the virtual ones have a more recent version
[*]they are already installed
[/LIST]

How can I install php7.0-snmp without having to uninstall snmp?

---

### Post by actionmystique on 2016-05-05
**Aptitude** offers more solutions, but none involves the preferred & most logical one: keep snmp because it already offers the most recent needed dependencies.
```
sudo aptitude install php7.0-snmpThe following NEW packages will be installed:
  libsnmp30{a} php7.0-snmp 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 832 kB of archives. After unpacking 3,382 kB will be used.
The following packages have unmet dependencies:
 snmp : Conflicts: libsnmp30 but 5.7.3+dfsg-1ubuntu4 is to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:               
1)     snmp                                       

     Install the following packages:              
2)     libsnmp-base [5.7.3+dfsg-1ubuntu4 (xenial)]

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libsnmp30 [Not Installed]                          
2)     php7.0-snmp [Not Installed]                        

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Install the following packages:                                           
1)     libsnmp-base [5.7.3+dfsg-1ubuntu4 (xenial)]                             

     Downgrade the following packages:                                         
2)     snmp [5.8~git20160427.8d07349f-14 (now) -> 5.7.3+dfsg-1ubuntu4 (xenial)]

Accept this solution? [Y/n/q/?] n

*** No more solutions available ***
```

---

### Post by actionmystique on 2016-05-06
The explanation lies into a very strange [debian policy]("https://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual") [COLOR=#111111][FONT=Ubuntu]which does not make sense and should be changed[/FONT][/COLOR]
"...[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]the version number of the concrete package which provides a particular virtual package will not be considered when considering a dependency on or conflict with the virtual package name.".[/COLOR][/FONT]
[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]One workaround is to offer **transitional packages** for all the virtual ones.[/COLOR][/FONT]

---

