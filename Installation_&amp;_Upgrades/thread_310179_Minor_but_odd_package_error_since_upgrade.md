---
title: "Minor but odd package error since upgrade"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by BorgHunter on 2006-11-30
Ever since I upgraded to Edgy, I have had this error. It doesn't prevent the normal function of Ubuntu for me, so it's not pressing, but it's puzzling nonetheless. Here's the output of apt-get upgrade:
```
borghunter@ares:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  hpijs python-adns python-clientcookie python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-gadfly python-htmlgen python-htmltmpl python-jabber python-kjbuckets
  python-ldap python-mysqldb python-osd python-pam python-pexpect python-pgsql
  python-pylibacl python-pymad python-pyopenssl python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-syck
  python-xmpp ubuntu-minimal
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                               [ ok ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gnome-session (>= 2.14.2); however:
  Package gnome-session is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.14.2.1ubuntu1); however:
  Package gnome-core is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-office:
 gnome-office depends on gnome-core (= 1:2.14.2.1ubuntu1); however:
  Package gnome-core is not configured yet.
dpkg: error processing gnome-office (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome:
 gnome depends on gnome-desktop-environment (= 1:2.14.2.1ubuntu1); however:
  Package gnome-desktop-environment is not configured yet.
 gnome depends on gnome-office (= 1:2.14.2.1ubuntu1); however:
  Package gnome-office is not configured yet.
dpkg: error processing gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 gnome-power-manager
 gnome-session
 gnome-core
 gnome-desktop-environment
 gnome-office
 gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Also, when I log in to Ubuntu, it pops up an error saying "GConf schema installer error, battery_low_percentage cannot be zero". Everything I need *works*, but it's driving me nuts that I keep getting this error and I can't do anything about it. Any thoughts?

---

### Post by nixlude98 on 2007-01-08
I am receiving the same battery error.

Power Manager
Gconf scheme installer error, battery_low_percentage cannot be zero

I am new to Linux and recently just install Ubuntu 6.10 on my HP TC4200. Everything seems to work fine, except I seem to receive this message every time I boot up. Any help would be greatly appreciated.

---

### Post by Jim Rockford on 2007-01-18
> **nixlude98 said:**
> I am receiving the same battery error.

Power Manager
Gconf scheme installer error, battery_low_percentage cannot be zero

I am new to Linux and recently just install Ubuntu 6.10 on my HP TC4200. Everything seems to work fine, except I seem to receive this message every time I boot up. Any help would be greatly appreciated.
------------------------------------------------------------------------------

I just wanted to chime in that I'm currently using Gnome with Fedora Core 6 and am getting the same exact error message, and none of the Fedora guys seem to know how to deal with it either (I didn't get any useful replies to a thread I initiated about this, in any case).  

Jim

---

### Post by BorgHunter on 2007-01-28
I found the solution. It was on the simple side, too. Apparently all that had to be done was stop acpid:

sudo /etc/init.d/acpid stop

Then running apt-get upgrade solves the problem.

---

### Post by JayTheHun on 2007-04-03
> **BorgHunter said:**
> I found the solution. It was on the simple side, too. Apparently all that had to be done was stop acpid:

sudo /etc/init.d/acpid stop

Then running apt-get upgrade solves the problem.

Sweet!  This worked perfectly for me as well.  I'd been messing with this myself for quite a while.  

Thanks for the post.

---

### Post by bigboi on 2007-04-29
I am having the same problem and that fix did not help. I had been running my machine for about 3 weeks now and had no problems with it, and now it suddenly after a reboot it is giving me "GConf schema installer error, battery_low_percentage cannot be zero".

The only thing that I did differently the last time my machine was working is that I set up the remote desktop preferences so that I could VNC into it. It worked fine, and I don't think that it is related to my problems.

If anybody has any other ideas as to other troubleshooting ideas it would be greatly appreciated. Thanks

---

