---
title: "facing problem with upgrades"
date: 2014-07-05
forum: Installation &amp; Upgrades
---

### Post by Salman_Khan on 2014-07-05
hi...i am a noob and would like your help with the following:

While trying to manually install squidguard, something went wrong and now i cannot uninstall squidguard. 

It usually starts with dpkg being locked:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
 and then i pskill it. then, for apt-get update the following error is shown:

```

root@ns1:/home/salman# apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

then when i run 'sudo dpkg --configure -a' i get:
```
root@ns1:/home/salman# sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on openssh-client (= 1:5.9p1-5ubuntu1.3); however:
  Version of openssh-client on system is 1:5.9p1-5ubuntu1.4.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
Setting up squidguard (1.4-4build1) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing squidguard (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-server
 squidguard
 ssh
``` 

Please help me as i cannot get any system updates due to this.

---

### Post by deadflowr on 2014-07-05
Did you run 
```
sudo apt-get update
```
you only posted the borked upgrade command, and dpkg --configure -a
It's good practice to run the above command before attempting the install new packages or upgrade existing packages.
You might also try
```
sudo apt-get install -f
```
For the record, since you are already running as root, there is no need to add sudo.
(Why you are running as root, I have no idea.)

---

### Post by Salman_Khan on 2014-07-05
sudo apt-get update gives the following error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
sudo apt-get install -f also gives same error:
```
root@ns1:/home/salman# sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

---

### Post by Salman_Khan on 2014-07-05
when i try to remove squidguard:
```
salman@ns1:~$ apt-get remove squidguardE: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
salman@ns1:~$ sudo apt-get remove squidguard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:5.9p1-5ubuntu1.3)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

then i try to 'sudo apt-get -f install' and get this:
```
salman@ns1:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openssh-server
Suggested packages:
  ssh-askpass rssh molly-guard openssh-blacklist openssh-blacklist-extra monkeysphere
The following packages will be upgraded:
  openssh-server
1 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.
3 not fully installed or removed.
Need to get 0 B/339 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 33, in <module>
    from ALChacks import *
  File "/usr/share/apt-listchanges/ALChacks.py", line 32, in <module>
    sys.stderr.write(_("Can't set locale; make sure $LC_* and $LANG are correct!\n"))
NameError: name '_' is not defined
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LC_CTYPE = "UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on openssh-client (= 1:5.9p1-5ubuntu1.3); however:
  Version of openssh-client on system is 1:5.9p1-5ubuntu1.4.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
Setting up squidguard (1.4-4build1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing squidguard (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 openssh-server
 squidguard
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by rahul4557 on 2014-07-05
1) restart your system
2) run > sudo apt-get update
3) run > sudo apt-get install synaptic
4) run > sudo synaptic
5) that should open "Synaptic Package Manager" where you can search and remove the specific package you want.

---

### Post by ajgreeny on 2014-07-05
**No, no, no!!**

Never use **sudo synaptic**.
Use either **gksudo synaptic** or in more recent Ubuntu versions **synaptic-pkexec** or use the menu system.

Using sudo for GUI applications can cause big problems occasionally, and may lock you out of your user account, See RootSudo in my signature.

---

### Post by Salman_Khan on 2014-07-05
SOLVED

Used dpkg --purge to remove the faulty package installations, reinstalled them and all works!

---

