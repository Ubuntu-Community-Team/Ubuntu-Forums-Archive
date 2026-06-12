---
title: "(Synaptic Package Manager Error)  E: dpkg was interrupted, you must manually run..."
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Destructo47 on 2010-10-17
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: cache->open()failed, please report

I get this error when I try to run Package Manager.  I have tried going to Terminal and using the suggested command, but then the blockcontrol configure screen appears.  I don't want to install it, I just want to get rid of it.

```
sudo dpkg --configure -a
```That just brings up the blockcontrol config screen.

```
sudo apt-get purge moblock-nfq
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'
to correct the problem.
```Above is the same error from dpkg in the Terminal.

```
nick@Nicks-room:~$ sudo apt-get remove moblock-nfq
[sudo] password for nick: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nick@Nicks-room:~$ sudo rm /var/lib/dpkg/lock
nick@Nicks-room:~$ sudo killall apt-get
apt-get: no process found
nick@Nicks-room:~$ sudo killall dpkg
nick@Nicks-room:~$ sudo apt-get purge moblock-nfq
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nick@Nicks-room:~$ sudo aptitude purge moblock-nfq
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nick@Nicks-room:~$ sudo dpkg --configure -a
[sudo] password for nick: 
Setting up blockcontrol (1.6.12-1~lucid) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing blockcontrol (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mobloquer:
 mobloquer depends on blockcontrol; however:
  Package blockcontrol is not configured yet.
dpkg: error processing mobloquer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 blockcontrol
 mobloquer
```Above is basically all of my attempts to remove it.  I'm assuming at the moment I've done something wrong, due to to error messages at the end.

I have tried going through the blockcontrol configuration, but I had no idea how to configure it.  I didn't finish so I could NOT uninstall it afterwards.  Right now, I cannot install any packages via Synaptic, as it quits after the error message.

So, I ran purge one more time to try and remove it.

```
nick@Nicks-room:~$ sudo apt-get purge blockcontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  blockcontrol* mobloquer*
0 upgraded, 0 newly installed, 2 to remove and 30 not upgraded.
2 not fully installed or removed.
After this operation, 1,036kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 205652 files and directories currently installed.)
Removing mobloquer ...
Purging configuration files for mobloquer ...
Removing blockcontrol ...
 * Stopping IP block daemon moblock                                      [ OK ] 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing blockcontrol (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--purge):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Errors were encountered while processing:
 blockcontrol
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Coincidentally, Update Manager popped up after that and told me to run a "A partial upgrade".  I didn't want to upgrade, so I cancelled and this is what appeared:

[SIZE=3]Software index is broken[/SIZE]

It is impossible to install or remove any software.  Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


```
nick@Nicks-room:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  blockcontrol
0 upgraded, 0 newly installed, 1 to remove and 30 not upgraded.
2 not fully installed or removed.
After this operation, 414kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 205619 files and directories currently installed.)
Removing blockcontrol ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing blockcontrol (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 blockcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Same error as before.  At this point, I have no idea what to do.  Can someone point me in the right direction as to at least enable update again?

---

### Post by jre on 2010-10-20
You've got to solve that problem (the first problem you already solved by issuing "sudo killall dpkg"):
```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
```
According to other threads you may use one of these commands```

lsof /var/cache/debconf/config.dat
fuser -v /var/cache/debconf/config.dat
``` to find out which process is using this file.

Where from did you get moblock-nfq? This is outdated since years.
Today you may simply install moblock+blockcontrol+mobloquer (if you want a GUI) or their successors pgld+pglcmd (if you don't need a GUI).  In the installation you may simply just confirm all questions. See also here: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

PS: You may get your system running again also the Windows way: reboot.

---

### Post by Destructo47 on 2010-10-22
Well, all of my attempts above plus a reboot seemed to get rid of the inability to use Synaptic.  I ran the first two commands you suggested and received no output.  So, using Synaptic, I removed the package "moblock" which was the only remaining trace of that program.  To be honest, I didn't know what the name of the package was.  I don't even remember downloading the package for it.  Removing that seemed to get rid of the whole "Partial Upgrade" message.

During all this I learned that Verizon does **not **throttle torrent traffic.  Basically, when I found that out, I realized that I didn't need Moblock to hide anything.

So, thank you for all your suggestions.

---

