---
title: "I can't install any sotware after partial upgrade"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by abdullah12 on 2010-06-24
Hi

I did partial upgrade lately and now I can't install any software.

the message I got is

software index is broken
it is impossible to install or remove any software. please use the package manager "synaptic
or run sudo apt-get install -f

if I follow the messages i receive from the system i will end up
with the system hanging when trying to replace mysql-server-5.1

```

reconfiguring packages ...
(reading databse ... 199488 files and directories currently installed.)
preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_i386.deb) ...

```

any idea?

thanks

---

### Post by wilee-nilee on 2010-06-24
> **abdullah12 said:**
> Hi

I did partial upgrade lately and now I can't install any software.

the message I got is

software index is broken
it is impossible to install or remove any software. please use the package manager "synaptic
or run sudo apt-get install -f

if I follow the messages i receive from the system i will end up
with the system hanging when trying to replace mysql-server-5.1

```

reconfiguring packages ...
(reading databse ... 199488 files and directories currently installed.)
preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_i386.deb) ...

```

any idea?

thanks

In the terminal run,
```
sudo dpkg --configure -a
```
then run
```
sudo apt-get install -f 
``` 

Then read up on partial upgrades don't do them in other words. There are ways around this for experienced users, who have there systems backed up and know how to fix things.

The best thing to do when given a partial upgrade is to wait and see if the missing packages are put in the repositories. 

So if this doesn't clean stuff up go to synaptic and look in custom-broken packages for any broken packages.

If this doesn't work reboot the computer click on the shift button on the reboot and use the second line recovery in the kernel list, you will get to a screen that has a fix broken pkgs line click on that, you have to be on the net and let it run and accept any changes. You will then be returned to the screen choose normal boot which will take you to a command line login, login then type startx and you should be back in.

If you try these methods and they don't work when you post again itemize what you did and in what order and 
what happened. 

You wont be able to add or remove any packages unless you fix this so if you default to trying to do this describe again the processes that led you to doing so.

---

### Post by abdullah12 on 2010-06-24
thaks wilee-nilee

here the errors I got when i run the code you provide

sudo dpkg --configure -a

```

abdullah@virtual-desktop:~$ sudo dpkg --configure -a
[sudo] password for abdullah: 
Sorry, try again.
[sudo] password for abdullah: 
dpkg: error processing mysql-server-5.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 mysql-server-5.1

```

sudo apt-get install -f

```

abdullah@virtual-desktop:~$ sudo dpkg --configure -a
[sudo] password for abdullah: 
Sorry, try again.
[sudo] password for abdullah: 
dpkg: error processing mysql-server-5.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 mysql-server-5.1
abdullah@virtual-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxvidcore4 libaio1 seabios vgabios libxml++2.6-2 qemu-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.1
Suggested packages:
  tinyca mailx
The following packages will be upgraded:
  mysql-server-5.1
1 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.
1 not fully installed or removed.
Need to get 0B/7,008kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 199488 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_i386.deb) ...

```

and it will stay forever like this

I tried to reinstall mysql but no success. and if I try to remove it will tell it is not installed !!

any clue?

to reboot in recovery, I press the shift key but nothing happaen :confused:

if I am not mistaken other distribution we should press escape key to go to recovery mode

thanks

---

### Post by wilee-nilee on 2010-06-24
Run in the terminal ```
sudo apt-get purge (package name)
```

Then reinstall it, if it is broken trying to reinstall it without getting rid of the broken stuff does not work with some programs. 

Go to synaptic as I suggested as well after running the purge and look in custom-broken and see whats there fix those by removing if needed, then reinstall with the main package install.

The recovery method I suggested is accessed with the 2nd line of the kernel list, so you have to be able to get grub to show the kernel list. **This alone is a basic skill** need to figure out as without this choice you can be dead in the water and waiting for instructions that may be confusing.

---

### Post by abdullah12 on 2010-06-24
I run the command, and the result

```

abdullah@virtual-desktop:~$ sudo apt-get purge mysql-server
[sudo] password for abdullah: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

then I run the suggested command

```


abdullah@virtual-desktop:~$ sudo sdpkg --configure -a
sudo: sdpkg: command not found
abdullah@virtual-desktop:~$ sudo dpkg --configure -a
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

and re-run the first command

```


abdullah@virtual-desktop:~$ sudo apt-get purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxvidcore4 libaio1 seabios vgabios libxml++2.6-2 qemu-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.1
Suggested packages:
  tinyca mailx
The following packages will be REMOVED:
  mysql-server*
The following packages will be upgraded:
  mysql-server-5.1
1 upgraded, 0 newly installed, 1 to remove and 105 not upgraded.
2 not fully installed or removed.
Need to get 0B/7,008kB of archives.
After this operation, 131kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 199491 files and directories currently installed.)
Removing mysql-server ...
(Reading database ... 199488 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.1 (using .../mysql-server-5.1_5.1.41-3ubuntu12.3_i386.deb) ...

```

and I reach to the same result.

I ll search tommorow how can I access the kernel list through grub. I am using ubuntu 10.04 . I think it was comming by default If I press escape in the old versions of ubuntu. And in fedroa, it is coming automatically every time I reboot. I don't now why it is difficult for me to reach there :(

thanks

---

### Post by abdullah12 on 2010-06-28
Hi wilee-nilee

well I manage to get the Grub list.
There are 6 entries in the list:
```

UBUNTU, with Linux 2.6.32-22-generic-pae
UBUNTU, with Linux 2.6.32-22-generic-pae (recovery mode)
UBUNTU, with Linux 2.6.32-21-generic-pae
UBUNTU, with Linux 2.6.32-21-generic-pae (recovery mode)
UBUNTU, with Linux 2.6.32-20-generic-pae
UBUNTU, with Linux 2.6.32-20-generic-pae  (recovery mode)

```
if I choose Linux 2.6.32.[COLOR="Blue"]22[/COLOR] recovery mode the system hangs.
And if I choose any of the other recover modes it will get the same result trying to replace mysql server and hangs.

any other help.

Regards

---

