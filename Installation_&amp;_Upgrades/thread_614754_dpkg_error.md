---
title: "dpkg: error"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Goldiescorpio on 2007-11-16
Hello,

I have a problem while uninstalling nagios2-common.
The error message is the following:

[I]administrator@s-lam-01:~$ sudo apt-get remove nagios2-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  nagios2-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 414kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109524 files and directories currently installed.)
Removing nagios2-common ...
.: 3: Can't open /usr/share/nagios2/debian/httpd.webapps-common
dpkg: error processing nagios2-common (--remove):
 subprocess pre-removal script returned error exit status 2
/var/lib/dpkg/info/nagios2-common.postinst: line 11: /usr/share/nagios2/debian/httpd.webapps-common: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nagios2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]
administrator@s-lam-01:~$

Can anyone help me please?
Thanks in advance!

Grtz,

Goldie

---

### Post by ddrichardson on 2007-11-17
Have you manually tried to delete this folder:```
*/usr/share/nagios2/debian/httpd.webapps-common
```*

---

### Post by zvacet on 2007-11-17
```
sudo dpkg --configure -a
```

---

### Post by Goldiescorpio on 2007-11-18
> **ddrichardson said:**
> Have you manually tried to delete this folder:```
*/usr/share/nagios2/debian/httpd.webapps-common
```*

The problem is that the directory does not exist, so there is no possibility of deleting it. I created the dit and file once and then I even got more errors.
In meanwhile my package manager on my LAMP-server is broken :s

---

### Post by ddrichardson on 2007-11-18
You could always try the --force option.

---

### Post by Pumalite on 2007-11-18
sudo dpkg -i --force-overwrite /usr/share/nagios2/debian/httpd.webapps-common

---

### Post by Goldiescorpio on 2007-11-18
Thx for your answer guys, but I yet tried those options: --force and overwrite and al sort of stuff.
I Want to remove the package, not install it. During removal things went wrong, now the package manager does not work anymore. I did a sudo apt-get remove nagios....then it broke...

None of above replies worked so far, but thx for the effort anyway guys!

Grtz

---

### Post by Kadrus on 2007-11-18
Euuh...were you installing a package from Ubuntu and had Synaptic Package manager opened at the same time..
it so type this 
```
sudo dpkg --configure -a
```
Hope that was helpful :)

---

### Post by Pumalite on 2007-11-18
Have you tried:

sudo apt-get remove --purge <packagename>
sudo apt-get update
sudo apt-get upgrade

---

### Post by Goldiescorpio on 2007-11-20
Hi guys,

thx again for the effort, but none of those things really helped.
When trying sudo dpkg --configure -a I got next error:

[I]administrator@s-lam-01:~$ sudo dpkg --configure -a
Setting up nagios2-common (2.9-1) ...
Not replacing deleted config file /etc/nagios2/apache2.conf
Not replacing deleted config file /etc/nagios2/conf.d/host-gateway_nagios2.cfg
include file /etc/nagios2/apache2.conf does not exist!
dpkg: error processing nagios2-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nagios2-common[/I]

When tryin this one: sudo apt-get remove --purge <packagename>

administrator@s-lam-01:~$ sudo apt-get remove --purge nagios2-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nagios-plugins-basic nagios2-doc
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nagios2-common*
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
Need to get 0B of archives.
After unpacking 414kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110072 files and directories currently installed.)
Removing nagios2-common ...
dpkg: error processing nagios2-common (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 nagios2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hope someone can tell me I don't have to reinstall my server and al my recently configuratad network-monitor-apps :s (was just about to install a backup solution when this error struck on my server)

Grtz

---

### Post by Pumalite on 2007-11-20
You stll have the chance to go to /var/lib/dpkg/status and review that file to see which ones are the offending packages. 'Good Packages' say...installed ok...installed.

---

