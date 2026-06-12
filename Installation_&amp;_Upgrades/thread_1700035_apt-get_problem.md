---
title: "apt-get problem"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by lecote on 2011-03-04
I posted yesterday, but got no response :( 

I have been battling with apt-get and synaptic: whenever I want to upgrade or install, it seems to get caught on an openoffice.org-emailmerge update. 
If I try to either update or reinstall via synaptic or apt-get, it freezes at the last line:
> sudo apt-get --reinstall install openoffice.org-emailmerge
[sudo] password: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
l@l-Latitude-D620:~$ sudo dpkg --configure -a
l@l-Latitude-D620:~$sudo apt-get --reinstall install openoffice.org-emailmerge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-24-generic linux-headers-2.6.35-24
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  openoffice.org-emailmerge
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0B/6,292B of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 181493 files and directories currently installed.)
Preparing to replace openoffice.org-emailmerge 1:3.2.1-7ubuntu1 (using .../openoffice.org-emailmerge_1%3a3.2.1-7ubuntu1.1_all.deb) ...


I've also tried to remove it via apt-get --remove openoffice.org-emailmerge:
> sudo apt-get remove openoffice.org-emailmerge 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-24-generic linux-headers-2.6.35-24
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openoffice.org-emailmerge
0 upgraded, 0 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing openoffice.org-emailmerge (--remove):
[B] Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/B]
Errors were encountered while processing:
 openoffice.org-emailmerge
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've tried manually removing every file I can find associated with emailmerge, but keep getting the same messages as above. 

It really sucks not being able to install anything...

Do I just need to reinstall Ubuntu???

---

### Post by dabl on 2011-03-04
What does 

```
sudo apt-get -f install
```

return?

---

### Post by lecote on 2011-03-04
>  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I don't have any other package manger open - or at least that I can tell from looking at the processes list. Update notifier is listing as sleeping, so that shouldn't be a problem. 

Anything else to look for that might be using dpkg?

---

### Post by killfall on 2011-03-04
You have closed everything right? 

try ctrl+alt+F1 to put it in terminal only mode and try again from there

---

### Post by dabl on 2011-03-04
> **killfall said:**
> 

try ctrl+alt+F1 to put it in terminal only mode and try again from there

Right. Log in to the tty1 console, and your first command should be

```
sudo service gdm stop
```

then try

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get clean
```

```
sudo service gdm start
```

---

### Post by lecote on 2011-03-04
The only process I have going is firefox. 

I tried it in tty1. sudo dgpk --config -a got an error stating that the database area is locked and asked if another program was using it.

---

### Post by dabl on 2011-03-05
You can remove the lock file.

In the desktop terminal, and with no package manager running

```
cd /var/cache/apt/archives
```

```
sudo mv lock oldlock
```

Then exit the terminal, Ctrl-Alt-F1 to the tty console, and repeat the sequence I listed above.  There should be no error regarding a lock file this time.

---

### Post by lecote on 2011-03-06
Just figured it out. Package was in a "very bad inconsistent state" and thus stalled every attempt to remove/reinstall/update. Managed to get rid of it using


sudo dpkg --purge --force-all package-name from [http://ubuntuforums.org/showthread.php?t=1683293](http://ubuntuforums.org/showthread.php?t=1683293). 

Updates handled just fine now.

---

