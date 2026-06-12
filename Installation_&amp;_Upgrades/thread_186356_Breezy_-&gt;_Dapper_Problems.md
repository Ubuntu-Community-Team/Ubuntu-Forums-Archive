---
title: "Breezy -&gt; Dapper Problems"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by jhollon on 2006-06-01
I have two computers which were running Breezy well  Now, after upgrading, they aren't running so well  The computers are:

1) desktop (custom)
piii 1ghz, 512ram, 3dfx vd3
and
2) an hp ze4300 laptop. amd athlonxp 1.8, ati vid, 1gb ram

During the upgrade process (during the "installing and downloading files" portion) both systems brought up an error that some (unknown) gnome process had suddenly terminated.  This error caused the installations to pause, but not quit (after clicking 'OK' they simply went on with the upgrade).  After this problem (which seemed to go away) they did the following:

1)  The desktop continued on for awhile, and then with ~8 mins left to go it stopped.  The computer brought up an error saying that some packages could not be found, and then the installation program aborted (just shut down).  I restarted the computer, it seemed to load up OK (a little bit slower than before), and seems to work.  Problems:  the downloaded files, for the upgrade, were not "cleaned up"  (it aborted before that step, so I have ~1.2GB of installation files on here), and at least one program (kdevelop/gcc) no longer is able to compile sources (c++ files for a class I'm in).  Also, when switching to the shell now (ctrl alt f1-6) my monitor says: "out of range".

2)  The laptop went through the entire process-  made it to the cleaning up files section and all.  It asked me to reboot, and I told it to go ahead.  After rebooting it came to the login screen, as expected, however, will not log in.  Others have reported this error too (the xserver crashes, jumps to the shell, and then restarts gdm).  I tried logging into kde, gnome, and xfce-  all do the same action (restart gdm).  As suggested elsewhere, I have also tried changing the xorg.conf driver from "ati" to "vesa" with no luck _and_ have tried to reconfigure gdm and the xserver (also in another post on the boards).

Just putting this up here to let others know they might want to wait a bit until solutions are found.

Jeff Hollon

{UPDATE}
On the desktop, when I try to install/uninstall a program through synaptic I get this:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

---

### Post by llamakc on 2006-06-01
On Debian-based distros you can clean out old downloaded packages with `apt-get clean` and you can always continue the aborted upgrade by repeated the command/action that you were stuck on. 

With the heavy traffic its more likely that the packages just 'timed out'. I'd rerun Synaptic or Update Manager or apt-get from the commandline and let it finish.

The command `apt-get -f install` can be helpful in these sort of situations. Good luck.

---

### Post by jhollon on 2006-06-01
Hey, good news.  I fixed the problem with the xserver crashes.
I started the system, and tried to log in one more time (it restarted as before).  So I tried this:

sudo apt-get upgrade

It said that there were 3 incomplete packages (for installation).  I told it to continue, and it installed them fine.  When I went back to the login screen (ctrl alt f7 and then restarted it with ctrl alt backspace) it allowed me to log in.  So, upgrade and then restart the xserver.

---

### Post by rcarring on 2006-06-01
Just a tip, although it takes longer to download the iso image, you won't have to worry about the network timing out during the install, as you will have all the required files on the cd you burn and use.

Obviously, this comment is pretty meaningless right now if the servers are busy but I expect they will become more reponsive as the hiatus surrounding the new release dies down again.

---

### Post by skylornova on 2006-06-01
Forgive the noob question, but I have not been able to find instructions on how to upgrade from the CD.  I searched the forums and google and didn't come up with anything.  Can someone point me in the right direction?  Thanks in advance :)

---

### Post by llamakc on 2006-06-01
So you are running Breezy and downloaded and burned the Dapper ISO?

run `sudo apt-cdrom add` or something like that and then upgrade with Synaptic.

---

### Post by jhollon on 2006-06-02
This is with regards to my desktop (the laptop is working!).

As I said above, I can not install or uninstall anything from apt-get/synaptic.  Here is the error when I use sudo apt-get upgrade:

:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be appreciated.

---

### Post by ubuntu_demon on 2006-06-02
try this :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by jhollon on 2006-06-02
I tried a lot of the things on that linking site.  I still get the same error (here is what happens when I try to do any of those commands, though this is specifically for the remove command):

:~$ sudo apt-get remove clvm
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 166449 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, regarding the problem with my monitor reporting "out of range" when switching to bash:  My roommate fixed the problem by removing the ubuntu splash/booting up-screen from grub (at least that's what he said he did, he knows a lot more about linux than I do since he built his gentoo system).  I thought it might have been something with my video card, but then realized that the drivers and such aren't even loaded at this point (on bootup or in bash)?  Not a big deal though.

---

### Post by ubuntu_demon on 2006-06-02
Don't remove anything related to LVM if you are using LVM.If you are using it you would know. Otherwise go ahead :

go to ctrl-alt-f1 and remove all packages that give errors and/or dependencies problems. 

Try the -f switch :

$sudo apt-get remove clvm -f

---

### Post by dust0r on 2006-06-02
I was trying to install Sun Java and  received this error:

E: samba: subprocess post-installation script returned error exit status 102
E: samba-dbg: dependency problems - leaving unconfigured

Then I tried to reinstall samba and the same error came up.
The Dependencies are fine, and there are no broken packages listed.

Then I checked my root directory and it reads:

130829 items, totalling 4.7 GB
_(some contents unreadable)_

Reading package lists... Done
Building dependency tree... Done
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3) ...
[B]update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba[/B]
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=dust0r]I was trying to install Sun Java and  received this error:

E: samba: subprocess post-installation script returned error exit status 102
E: samba-dbg: dependency problems - leaving unconfigured

Then I tried to reinstall samba and the same error came up.
The Dependencies are fine, and there are no broken packages listed.

Then I checked my root directory and it reads:

130829 items, totalling 4.7 GB
_(some contents unreadable)_[/QUOTE]
Please post the entire errors.

---

### Post by jhollon on 2006-06-02
As far as I know I am not using the LVM stuff, and here is what I get when I try the command remove -f on it:


:~$ sudo apt-get remove clvm -f
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 166460 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ubuntu_demon on 2006-06-02
clvm,redhat-cluster-suite and redhat-cluster-suite are not installed on my computer. Do you have any idea why these packages are/were installed ? Did you install from a breezy server cd or something ?

---

### Post by jhollon on 2006-06-02
This system has gone through Ubuntu as follows:

1 - Hoary from CD (format, install from scratch), as desktop, no special settings.  Typical install.
2 - From Hoary to Breezy I used sources.list and changed all 'hoary's to 'breezy's.  Did an upgrade and got Breezy.
3 - For the most recent upgrade I did gksudo "update-manager -d"

---

### Post by ubuntu_demon on 2006-06-02
Please post your /etc/apt/sources.list

---

### Post by Lestat1975 on 2006-06-02
I am having the exact same problem as described in this thread.  I have changed all the 'breezy' references to 'dapper' in my sources.list.  Unfortunately the one I messed up on was the CD-ROM (and I didn't have the CD-ROM downloaded), but I have corrected it with apt-cdrom add.  I've tried all the apt-gets that I can think of...upgrade, update, install, dist-upgrade, remove, etc.  Any help would be appreciated.  Been working with Ubuntu recently and am learning a lot but there are still some things that hold me to XP...don't mind dual booting.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Lestat1975]I am having the exact same problem as described in this thread.  I have changed all the 'breezy' references to 'dapper' in my sources.list.  Unfortunately the one I messed up on was the CD-ROM (and I didn't have the CD-ROM downloaded), but I have corrected it with apt-cdrom add.  I've tried all the apt-gets that I can think of...upgrade, update, install, dist-upgrade, remove, etc.  Any help would be appreciated.  Been working with Ubuntu recently and am learning a lot but there are still some things that hold me to XP...don't mind dual booting.[/QUOTE]
start by reading this :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

and create your own thread in which you post your errors. Be elaborate. You may give me the url of the thread and I'll try to help to tomorrow. (I'm currently busy and it's 2:00 am here so I'm hoping to go to bed soon)

---

### Post by jhollon on 2006-06-03
Here is my sources.list file as of right now, before (when I upgraded) it had everything down to cipherfunk

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by ubuntu_demon on 2006-06-03
please comment all non-official repo's such as wine,cipherfunk and kubuntu.

After that follow this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by jhollon on 2006-06-03
I get this error message:

:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, I get the same error when I try sudo apt-get remove clvm

---

### Post by dust0r on 2006-06-03
I have tried searching ways to configure samba and the answer is probably on the tip of my fingers.  I keep getting the same error when I try to install anything.


$ sudo apt-get install bsdgames
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  bsdgames
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 939kB of archives.
After unpacking 2408kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe bsdgames 2.17-7 [939kB]
Fetched 939kB in 2s (327kB/s)
Selecting previously deselected package bsdgames.
(Reading database ... 87638 files and directories currently installed.)
Unpacking bsdgames (from .../bsdgames_2.17-7_i386.deb) ...
[B]Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Setting up bsdgames (2.17-7) ...

Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]


It doesn't matter what I try to install, upgrade, remove.  I get the **bolded** error.
Any suggestions or links to this problem.

Thank you in advance.

---

### Post by ubuntu_demon on 2006-06-03
after you have commented the non-official repos in your sources.list don't forget to run :

$sudo apt-get update


If apt is reporting errors or broken dependencies for packageA then try to remove it including all dependencies and the dependencies of those dependencies.................and the dependencies of those dependencies.........and the dependencies of those dependencies........ 

read my guide and make sure you understand it before doing anything :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

this is also a very good resource:
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

I'm going to sleep now. Try figuring it out for a while and report the latest error messages if you can't get further.

good luck! :)

---

### Post by npcomplete2000 on 2006-06-04
I had the same problem with ubuntu 6.06.

I accidently clicked "clvm" in synaptic when performing update.
It failed installation and caused broken package.

My kernel is 
Linux 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux

One thing I noticed is that "clvm" caused kernel
linux-image-2.6.15-23-server to install on my system. When I want to 
remove  linux-image-2.6.15-23-server, it also prompts to remove "clvm",
"cman", "fence".

I tried to fix the problem with apt-get. Here is the message I got

sudo apt-get install clvm
Password:
Reading package lists... Done
Building dependency tree... Done
clvm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)


sudo apt-get remove clvm -f
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 142469 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ubuntu_demon on 2006-06-04
I've updated my guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

it now also includes a link to this post :
[http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12)

---

### Post by Aielyn on 2006-06-04
[QUOTE=ubuntu_demon]I've updated my guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

it now also includes a link to this post :
[http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12)[/QUOTE]

Thanks,

I was having the same problem as npcomplete2000 and jhollon (clvm had somehow been installed, and had also made dapper server install on the system).

I tried what you suggested in the first link (the apt-get remove ... --purge); specifically:
**sudo apt-get remove clvm -f --purge**
And it worked. clvm is now off my system (finally - I had the same problem in that it refused to remove it). And with that, I was able to uninstall all of the programs that were dependent on it, that I didn't want on my system.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Aielyn]Thanks,

I was having the same problem as npcomplete2000 and jhollon (clvm had somehow been installed, and had also made dapper server install on the system).

I tried what you suggested in the first link (the apt-get remove ... --purge); specifically:
**sudo apt-get remove clvm -f --purge**
And it worked. clvm is now off my system (finally - I had the same problem in that it refused to remove it). And with that, I was able to uninstall all of the programs that were dependent on it, that I didn't want on my system.[/QUOTE]
thnx for the information. I'll add it to these threads :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by dust0r on 2006-06-04
I fixed my errors I over looked the line:
**invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba**

all I did was
$sudo rm /etc/rc2.d/K09samba 

to remove the dangling symlink
usually a mail would be sent to tell me about the error...but oh well all is good.

---

### Post by ariel on 2006-06-04
Hi, I'm also having the "can't get rid of this clvm thing" problem. I installed it by mistake on my brand new fresh 6.06/official install. It keeps complaining to syslog that it can't connect to the cluster, so I want to get rid of the thing. I can not. Last thing I did was actually re-install the package via synaptic, and then:


ariel@ariel-laptop:~$ sudo apt-get remove clvm -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112839 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
ariel@ariel-laptop:~$



it looks like clvm was shipped broken. Can someone help me here remove  this thing without breaking  apt-get?

Thanks!

---

### Post by npcomplete2000 on 2006-06-04
I finally got the problem solved.

But initially  "sudo apt-get remove clvm -f --purge" doesn't work for me and it give the same error.

 sudo apt-get remove clvm -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142463 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Another thing I noticed is that because of the clvm error, every time 
I install a new package, it gives error such as 
sudo apt-get install debfoster
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  debfoster
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 32.9kB of archives.
After unpacking 168kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe debfoster 2.5-5ubuntu1 [32.9k
B]
Fetched 32.9kB in 1s (22.1kB/s)
Selecting previously deselected package debfoster.
(Reading database ... 142464 files and directories currently installed.)
Unpacking debfoster (from .../debfoster_2.5-5ubuntu1_i386.deb) ...
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Setting up debfoster (2.5-5ubuntu1) ...

Seems the error message always complain "clvm" fail to start no matter
what I am doing. Here is what I did.

1. remove "clvm" from /etc/init.d ( so there is no need to start)
2. then try "sudo apt-get remove clvm -f --purge"

Now it works.

sudo apt-get remove clvm -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 142474 files and directories currently installed.)
Removing clvm ...
Purging configuration files for clvm ...


Thanks for the help in the forum.

---

### Post by ariel on 2006-06-04
Confirmed! thanks a bunch

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=npcomplete2000]I finally got the problem solved.

Thanks for the help in the forum.[/QUOTE]

I'm glad that you have solved your problem. Thanks for posting your solution to your problem. This might help others.

---

### Post by jhollon on 2006-06-04
Hey, great news.  It works wonderfully now!  Here is what I had to do:

jeff@ubuntujeff:/etc/init.d$ sudo rm clvm
jeff@ubuntujeff:/etc/init.d$ sudo apt-get remove clvm -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 166690 files and directories currently installed.)
Removing clvm ...
Purging configuration files for clvm ...


Thanks to everyone who helped out!

Jeff

---

### Post by ubuntu_demon on 2006-06-05
I've updated this guide regarding the clvm issue :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

---

### Post by katzman on 2006-06-05
I had this happened but i was still able to log in as root.....turns out my regular user had been removed from the users group

---

### Post by sceptre0 on 2006-07-03
I was getting this error when I tried to install Samba.

E: Sub-process /usr/bin/dpkg returned an error code (1)

This is how I fixed it:

sudo apt-get build-dep samba
sudo apt-get -f install samba

---

### Post by sceptre0 on 2006-07-03
Referring to my post above.  Now I get a new error.

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3_i386.deb:
subprocess new pre-removal script returned error exit status 102

---

### Post by premchapagain on 2006-07-12
> **npcomplete2000 said:**
> I finally got the problem solved.

But initially  "sudo apt-get remove clvm -f --purge" doesn't work for me and it give the same error.

 sudo apt-get remove clvm -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142463 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Another thing I noticed is that because of the clvm error, every time 
I install a new package, it gives error such as 
sudo apt-get install debfoster
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  debfoster
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 32.9kB of archives.
After unpacking 168kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe debfoster 2.5-5ubuntu1 [32.9k
B]
Fetched 32.9kB in 1s (22.1kB/s)
Selecting previously deselected package debfoster.
(Reading database ... 142464 files and directories currently installed.)
Unpacking debfoster (from .../debfoster_2.5-5ubuntu1_i386.deb) ...
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Setting up debfoster (2.5-5ubuntu1) ...

Seems the error message always complain "clvm" fail to start no matter
what I am doing. Here is what I did.

1. remove "clvm" from /etc/init.d ( so there is no need to start)
2. then try "sudo apt-get remove clvm -f --purge"

Now it works.

sudo apt-get remove clvm -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  clvm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 142474 files and directories currently installed.)
Removing clvm ...
Purging configuration files for clvm ...


Thanks for the help in the forum.


Thanks for the help. I was having exactly the same problem. Your suggestion of removing clvm first solved the problem. Two lines of commands does the magic!

Prem

---

### Post by Neverex on 2006-07-13
Thanks for help. Been bugging me for days ](*,)

---

### Post by jeffhollon on 2008-02-29
OFF TOPIC, weirded out.  same first and last name.  odd last name which makes this even weirder.

i am Jeff Hollon as well

---

