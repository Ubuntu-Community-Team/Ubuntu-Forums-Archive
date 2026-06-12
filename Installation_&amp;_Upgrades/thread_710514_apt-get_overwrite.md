---
title: "apt-get overwrite"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by Peter LaValle on 2008-02-28
Is there a way to make apt-get overwrite existing files? Like pretend that a package has never been installed?

I installed apache2 awhile ago, mucked it up, and removed it but now I want to use it again; unfortunately I deleted most of the apache2 files and folders and can't get apt-get to recreate them from scratch.

I can't find instructions on how to make apt-get do this, but I remember hearing it somewhere so I think it is possible; am I mistaken?

---

### Post by Pumalite on 2008-02-28
Post the output of:
sudo dpkg --configure -a

---

### Post by TheWizzard on 2008-02-28
wouldn't the -f (force) option do the trick?

---

### Post by Pumalite on 2008-02-28
Yes. I was just starting.

---

### Post by TheWizzard on 2008-02-28
> **Pumalite said:**
> Yes. I was just starting.

ok, sorry dude

---

### Post by Pumalite on 2008-02-28
No prob. I wonder where is the O.P.

---

### Post by Peter LaValle on 2008-02-29
> **Pumalite said:**
> No prob. I wonder where is the O.P.

There ... umm ... is no output from either. It just kind of executes.

I have the binaries installed I need to reinstall the default configuration files.

"Dear apt-get, I know you understand that I have already installed this package, but I want you to ignore that and just overwrite the config files."

---

### Post by TheWizzard on 2008-02-29
> **Peter LaValle said:**
> 
"Dear apt-get, I know you understand that I have already installed this package, but I want you to ignore that and just overwrite the config files."

use the "-f" option to do that. if this doesn't work please post the command and the output here.

---

### Post by Peter LaValle on 2008-03-01
It seems that my stuff was slightly less cryptic that I thought, but it still doesn't work, and I still don't know how to get it to recreate the original configuration files. I am starting to wonder if it is possible to get apt-get to do this thing.

```

peter@arthur:~$ sudo apt-get -f install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/42.2kB of archives.
After unpacking 94.2kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 18441 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.4-3ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.4-3ubuntu0.1) ...
peter@arthur:~$ /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                       install: cannot change owner and/or group of `/var/lock/apache2': Operation not                                                      permitted
apache2: Could not open configuration file /etc/apache2/apache2.conf: No such fi                                                     le or directory
                                                                         [fail]
peter@arthur:~$

```

---

### Post by TheWizzard on 2008-03-02
don't you have a backup of /etc? please make sure you always regularry backup both /home and /etc. 

check /usr/share/doc

---

### Post by Peter LaValle on 2008-03-02
No, I do not have a backup.

---

### Post by TheWizzard on 2008-03-03
> **Peter LaValle said:**
> No, I do not have a backup.

did you find anything in /usr/share/doc? 

i'm affraid you'll have to start googleing

---

### Post by Peter LaValle on 2008-03-03
Well I think I have an idea. If the configuration files are all in /etc/apache2 can't I just install an identical version of Ubuntu and copy the /etc/apache2 folder?

---

### Post by julian67 on 2008-03-03
why not use ```
sudo apt-get install --reinstall apache2
``` it should reinstall all the missing files. Alternatively purge the package (i.e uninstall it and all its config files) ```
sudo apt-get remove --purge apache2
``` and then install it again the usual way

---

### Post by Peter LaValle on 2008-03-03
Those don't work; the configuration is still missing.

```

peter@arthur:~$ sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
Need to get 0B of archives.
After unpacking 94.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 18506 files and directories currently installed.)
Removing apache2 ...
peter@arthur:~$ sudo apt-get install --reinstall
Reading package lists... Done
Building dependency tree
Reading state information... Done
^X0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
peter@arthur:~$ sudo apt-get install --reinstall apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/42.2kB of archives.
After unpacking 94.2kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 18501 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.4-3ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.4-3ubuntu0.1) ...
peter@arthur:~$ /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                                install: cannot change owner and/or group of `/var/lock/apache2': Operation not                                                                               permitted
apache2: Could not open configuration file /etc/apache2/apache2.conf: No such fi                                                                              le or directory

```

---

### Post by Peter LaValle on 2008-03-03
Replacing the config folder with one copied from a virtual machine worked!

---

