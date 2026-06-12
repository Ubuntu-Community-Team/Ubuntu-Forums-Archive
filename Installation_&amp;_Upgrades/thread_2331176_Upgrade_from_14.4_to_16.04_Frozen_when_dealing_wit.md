---
title: "Upgrade from 14.4 to 16.04: Frozen when dealing with apparmor profile for cupsd"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by federicodemaria on 2016-07-19
[NB Since I was not getting any response, and I needed to quickly solve this some how. I kept trying different things, until I messed it up completely (black screen). Therefore, I decided to re-install Ubuntu 16.04 from scratch. I didn't format /Home, and I anyway had a back up. I'm not sure what the forum protocol is, but I would leave this threat open for the moment, in case it gets some responses that can be of any help for somebody else. Thank you!]  

Hi all,
I decided to upgrade, and I now wonder whether it was a good idea. I'm a normal user, bot an expert.

I run: do-release-upgrade, and it got frozen here:

```
Setting up openssl (1.0.2g-1ubuntu4.1) ...
Setting up ssl-cert (1.0.37) ...
Setting up bc (1.06.95-9build1) ...
Setting up cups-daemon (2.1.3-4) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.cupsd ...
Installing new version of config file /etc/cups/cups-files.conf ...
Installing new version of config file /etc/init.d/cups ...
Installing new version of config file /etc/logrotate.d/cups-daemon ...

```

I've googled it, and found it might be a bug ("[do-release-upgrade stuck when dealing with apparmor profile for cupsd]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1592917")"). It looks like it's a problem related to mysql-server, but I don't really understand what they say.

I open another Terminal, tried to stop my mysql server (although I don't know what it's), but it didn't work. Here what I got:

```
jhonny@jhonny-ubuntu:~$ sudo /etc/init.d/mysql stop
[sudo] password for jhonny:
sudo: /etc/init.d/mysql: command not found
jhonny@jhonny-ubuntu:~$ sudo
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
jhonny@jhonny-ubuntu:~$ sudo stop mysql
stop: Unknown job: mysql
jhonny@jhonny-ubuntu:~$ sudo service mysql stop
mysql: unrecognized service
jhonny@jhonny-ubuntu:~$

```

It would be really great if you could help.

In case you think I'll get into trouble, please let me know if I can just stop the upgrade process and restore Ubuntu 14. It might be too early for me to safely upgrade.

Thank you

Ok, one more information. 

The process in the Terminal is still stuck. However, apparently, the upgrade process has been successfully completed, because it's already install on my machine. 
For example, I now got Libre Office 5, different from the one I had on Ubuntu 14.04

```

jhonny@jhonny-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial
jhonny@jhonny-ubuntu:~$ 

```

Now, I'm afraid that if I reboot, I might get some problems. What would you suggest? 

Assuming that I ignore the fact the process got stuck, online I have found three options:

1) ```
apt-get autoremove
apt-get clean 
``` [http://askubuntu.com/questions/776024/unable-to-update-xubuntu-from-14-04-to-16-04-using-update-manager](http://askubuntu.com/questions/776024/unable-to-update-xubuntu-from-14-04-to-16-04-using-update-manager)
or
2) ```
 apt-get autoremove --purge -y;apt-get clean 
``` ([http://askubuntu.com/questions/760347/how-to-upgrade-from-14-04-lts-or-15-10-to-16-04-from-terminal/760402](http://askubuntu.com/questions/760347/how-to-upgrade-from-14-04-lts-or-15-10-to-16-04-from-terminal/760402))
or 
3) ```
 sudo init 6 
``` ([http://www.tecmint.com/upgrade-ubuntu-14-04-to-16-04/](http://www.tecmint.com/upgrade-ubuntu-14-04-to-16-04/))

Please, help

Thanks

More, now the Terminal from stuck to the point, got frozen. 

In another Terminal, I tried to run apt-get install --fix-missing; apt-get install --fix-missing ([http://askubuntu.com/questions/462690/what-does-apt-get-fix-missing-do-and-when-is-it-useful/462751](http://askubuntu.com/questions/462690/what-does-apt-get-fix-missing-do-and-when-is-it-useful/462751)), but it says: 

```

jhonny@jhonny-ubuntu:~$ sudo apt-get update
Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                    
Hit:3 http://es.archive.ubuntu.com/ubuntu xenial InRelease               
Hit:4 http://archive.canonical.com xenial InRelease                      
Hit:5 http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease       
Hit:6 http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease
W: No sandbox user '_apt' on the system, can not drop privileges
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jhonny@jhonny-ubuntu:~$ sudo apt-get install --fix-missing
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jhonny@jhonny-ubuntu:~$ 

```

I'm unlucky today, I run sudo rm /var/lib/apt/lists/lock ([http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)) but still get the same message: 

```

jhonny@jhonny-ubuntu:~$ sudo rm /var/lib/apt/lists/lock
jhonny@jhonny-ubuntu:~$ sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease             
Hit:3 http://archive.canonical.com xenial InRelease                           
Hit:4 http://es.archive.ubuntu.com/ubuntu xenial InRelease               
Hit:5 http://es.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:6 http://es.archive.ubuntu.com/ubuntu xenial-backports InRelease
W: No sandbox user '_apt' on the system, can not drop privileges
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jhonny@jhonny-ubuntu:~$ sudo apt-get install --fix-missing
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jhonny@jhonny-ubuntu:~$ 

```

---

### Post by mandevirus2 on 2016-07-31
good afternoon.

i solved with theese comand.

sudo /etc/init.d/cups stop

---

### Post by federicodemaria on 2016-08-12
Thanks a lot, although it is too late for myself, I hope it can be of help to anyone else.

---

