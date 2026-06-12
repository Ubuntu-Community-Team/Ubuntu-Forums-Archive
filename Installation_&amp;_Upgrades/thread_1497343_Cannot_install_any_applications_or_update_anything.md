---
title: "Cannot install any applications or update anything."
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by djswartz on 2010-05-30
I've been a long time user of Gnome and a few weeks ago I decided to give KDE a whirl.

Kubuntu **10.04** was running smoothly for a while, but now all of a sudden I get this error message in KPackageKit ```
Waiting for package manager to lock
```

When I try apt-get I get this message ```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'
 to correct the problem.
```

After I run dpkg --configure -a I get these errors:

```
dpkg: error processing mysql-server-5.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
```

So obviously there is somthing wrong with my MySql installation, but I don't know how to fix it as I cannot install anything.

Any help would be appreciated.

Thanks,
-Dylan

---

### Post by dino99 on 2010-05-30
remove/purge mysql-server-5.1 

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update

then reinstall it

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by djswartz on 2010-05-30
Thanks man,

It works now. =]

---

### Post by Kanedagr on 2010-06-26
Thanks to both of you! In my case though i simply have to run "sudo dpkg --configure -a" and everything went back to normal.

---

### Post by AreaEuropa on 2010-08-13
Didn't directly work for me:

```
sudo apt-get autoremove                                                                                                                                                  
Reading package lists... Done                                                                                                                                                           
Building dependency tree                                                                                                                                                                
Reading state information... Done                                                                                                                                                       
The following packages will be REMOVED:                                                                                                                                                 
  mysql-server-5.1                                                                                                                                                                      
0 upgraded, 0 newly installed, 1 to remove and 20 not upgraded.                                                                                                                         
1 not fully installed or removed.                                                                                                                                                       
After this operation, 15.0MB disk space will be freed.                                                                                                                                  
Do you want to continue [Y/n]? Y                                                                                                                                                        
dpkg: error processing mysql-server-5.1 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

But this fixed it:
```
sudo aptitude install mysql-server-5.1
```

After which I could do a:
```
sudo aptitude safe-upgrade
```

And back to normal again.

Thanks !!

---

