---
title: "[SOLVED] Upgrade to Intrepid not completed"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by bo_n_tulsa on 2008-11-03
This is weird.  I used the update manager to upgrade to intrepid.  It never got to the "cleaning" stage.  I'm sorry, I should have tried to copy the error it was giving me.  When I go to System/About Ubuntu, it has this:
```
This section is an introduction to Ubuntu. It explains the Ubuntu philosophy and roots, gives information about how to contribute to Ubuntu, and shows how to get help with Ubuntu.       
    

Thank you for your interest in Ubuntu 
                - the  - released in .
```

Notice it doesn't state the actual version.  
In the upgrade manager, the gnome-user-guide refuses to update with this error:
```
E: /var/cache/apt/archives/gnome-user-guide_2.24.0+svn20080922ubuntu1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/user-guide/C/user-guide.pdf')
```

It _seems_ like everything updated, but I can't be exactly sure.
I'm not sure what to do.  Any way to try again?

---

### Post by Partyboi2 on 2008-11-03
Open a terminal and 
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by bo_n_tulsa on 2008-11-03
Ok, everything went well until the last command, whereupon this occurs:
```
me@me:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-user-guide
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7735kB of archives.
After this operation, 2400kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
(Reading database ... 201576 files and directories currently installed.)
Preparing to replace gnome-user-guide 2.22.0+svn20080407ubuntu1 (using .../gnome-user-guide_2.24.0+svn20080922ubuntu1_all.deb) ...
Unpacking replacement gnome-user-guide ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/gnome-user-guide_2.24.0+svn20080922ubuntu1_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/user-guide/C/user-guide.pdf')
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-user-guide_2.24.0+svn20080922ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Partyboi2 on 2008-11-03
Try reinstalling the package that is causing the problem.
```
 sudo apt-get clean
```
then
```
sudo apt-get --reinstall install gnome-user-guide
```

---

### Post by bo_n_tulsa on 2008-11-03
Thanks.  That seems to have fixed it right up.
The system/about ubuntu still doesn't show the version, but it displays correctly in terminal.

Appreciate your help.

---

