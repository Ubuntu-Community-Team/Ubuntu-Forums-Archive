---
title: "Java and Logmein"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by drmbogo on 2007-05-09
Hello all,
Following the suggestions in this post:
[http://ubuntuforums.org/showthread.php?t=436933](http://ubuntuforums.org/showthread.php?t=436933)
..I've *almost* got java/Logmein working.

I can login to the remote computer, but when I attempt to use Remote Control, I get this error:

java.security.AccessControlException: access denied (SocketPermission fred-bzoieorums.app14.logmein.com:443 connect,resolve)  :mad: 

Also, when I try to use File Manager, a dialog pops up that prints the logmein file manager client version # and copyright info, but seems to hang; i.e. I can't see or otherwise manipulate any files.

Incidentally,  if I close file manager, and try to restart it, Firefox crashes, that is, it just shuts down unexpectedly.

I realize this may not be a java problem, or even a linux issue, as other folks have gotten it to work, but i figured what the heck, this is easily the most helpful and cordial of any forum, so why not start here!

Thanks in advance for all your help.
dB

---

### Post by us3rQUE on 2007-05-12
I was killing my self on this one tooo. 

This is how i fixed it.
Installed Java 1.5 JRE manually. / kept messing w/ 
copying shortcuts in /usr/lib/firefox/plugins - until It just stopped working.


1. export your bookmarks.
2. sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gappletviewer-4.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox firefox-gnome-support gcjwebplugin-4.1 gnome-user-guide
  j2re1.4-mozilla-plugin java-gcj-compat-plugin mozilla-beagle mozilla-mplayer
  sun-java5-plugin sun-java6-plugin ubuntu-desktop ubuntu-docs yelp
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 85.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119010 files and directories currently installed.)
[B]Removing sun-java6-plugin ...
Removing sun-java5-plugin ...[/B]
Removing mozilla-mplayer ...
**Removing j2re1.4-mozilla-plugin ...**
Removing mozilla-beagle ...
Removing java-gcj-compat-plugin ...
Removing gcjwebplugin-4.1 ...
Removing ubuntu-docs ...
Removing ubuntu-desktop ...
Removing gnome-user-guide ...
Removing yelp ...
Removing firefox-gnome-support ...
Removing firefox ...


3.) [COLOR="Red"]sudo apt-get install firefox[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
[B]  gappletviewer-4.1
Use 'apt-get autoremove' to remove them.[/B]
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9227kB of archives.
After unpacking 29.3MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main firefox 2.0.0.3+1-0ubuntu2 [9227kB]
Fetched 9227kB in 21s (433kB/s)                                                
Selecting previously deselected package firefox.
(Reading database ... 114792 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.3+1-0ubuntu2_i386.deb) ...
Setting up firefox (2.0.0.3+1-0ubuntu2) ...
Please restart any running Firefoxes, or you will experience problems.
4) [COLOR="Red"] sudo apt-get autoremove[/COLOR]



After doing this I got LogMeIn working in Feisty. :) 

/ If anyone can explain what happened here please do. :confused: :confused: 
I hope this helps.

---

### Post by us3rQUE on 2007-05-12
check your Java version at: [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

My result:
Oops! You don't have the recommended Java installed.
**Your Java version is Version 5.0 Update 6**. Please click the button below to get the recommended Java for your computer.

So It looks like JRE 5 works for LogMeIn.

My /usr/lib/firefox/plugins dir
drwxr-xr-x 2 root root  4096 2007-05-12 21:02 .
drwxr-xr-x 5 root root  4096 2007-05-12 21:02 ..
lrwxrwxrwx 1 root root    41 2007-04-27 22:31 flashplayer.xpt -> ../../flashplugin-nonfree/flashplayer.xpt
lrwxrwxrwx 1 root root    43 2007-04-27 22:31 libflashplayer.so -> ../../flashplugin-nonfree/libflashplayer.so
[B]lrwxrwxrwx 1 root root    39 2007-05-12 21:00 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root    63 2007-05-12 20:51 libjavaplugin.soexit -> /usr/local/j2re-1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so[/B]
lrwxrwxrwx 1 root root    36 2007-04-27 21:43 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-04-27 21:43 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-04-27 21:43 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-04-27 21:43 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-04-27 21:43 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-04-27 21:43 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-04-27 21:43 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-04-27 21:43 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root  8936 2007-04-03 11:44 libunixprintplugin.so
-rw-r--r-- 1 root root 58656 2007-01-24 07:11 nphelix.so
-rwxr-xr-x 1 root root  5086 2007-01-24 07:11 nphelix.xpt

---

### Post by daniel_szollosi-nagy on 2007-05-14
I can confirm, upgrading Java to the latest version fixed this exact same problem for me, thanks us3rQUE!

---

