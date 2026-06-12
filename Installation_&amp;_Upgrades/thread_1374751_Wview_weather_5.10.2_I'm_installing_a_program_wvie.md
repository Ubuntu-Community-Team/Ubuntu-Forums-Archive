---
title: "Wview weather 5.10.2 I'm installing a program wview weather 5.10.installation problem"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by jarimo on 2010-01-07
Hello !
I'm installing a program wview weather 5.10.2.
Installation instructions can be found here:
[http://www.wviewweather.com/release-notes/wview-User-Manual.html#Installation-debian](http://www.wviewweather.com/release-notes/wview-User-Manual.html#Installation-debian)
But the installer does not create / etc / init.d / wiew folders.
code installation.=>

root @ putte-desktop: / home / Jassu # sudo apt-get install wview 
Reading package lists ... Ready 
To form a dependency tree 
Read status information ... Ready 
The following NEW packages will be installed: 
  wview 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
Download archive 0t / 1 238kt. 
Function is then used for 4 s 796k more disk space. 
WARNING: The following troubleshooting package origin can not be authenticated! 
  wview 
Install these packages without authentication [y / N]? y 
Selected previously, select the carpet package wview. 
(Reading database ... 166,056 files and directories currently installed.) 
Deregulation of the package wview (.../ wview_5.10.3-1_amd64.deb) ... 
Carry out the item man-db trigger ... 
Carry out the item ureadahead the trigger ... 
ureadahead will be reprofiled is next reboot 
Make the settings: wview (5.10.3-1) ... 
==> / Var / lib / wview has been created with distro examples 
==> / Etc / wview has been created with distro examples 

If this is a first time install, type the station will be set to "simulator". 
To change the station type, run "wviewconfig" wviewmgmt or use the web interface to change it. 
If this is a first time install, the generation templates will be set to "chrome-standard U.S. units." 
To change this run "wviewhtmlconfig" to configure the template directory. 

Starting wview Daemons: 

root @ putte-desktop: / home / Jassu # sudo / etc / init.d / start wview 
Starting wview Daemons: 
radlib router pid file / var / lib / wview / radmrouted.pid exists - killing existing process 
wviewd pid file / var / lib / wview / wviewd.pid exists - killing existing process 
/ etc / init.d / wview: line 67: kill: (3080) - The process is not 
htmlgend pid file / var / lib / wview / htmlgend.pid exists - killing existing process 
wviewftpd pid file / var / lib / wview / wviewftpd.pid exists - killing existing process 
wviewsshd pid file / var / lib / wview / wviewsshd.pid exists - killing existing process 
wvalarmd pid file / var / lib / wview / wvalarmd.pid exists - killing existing process 
wvcwopd pid file / var / lib / wview / wvcwopd.pid exists - killing existing process 
wvhttpd pid file / var / lib / wview / wvhttpd.pid exists - killing existing process 
wvpmond pid file / var / lib / wview / wvpmond.pid exists - killing existing process 
root @ putte-desktop: / home / Jassu # 
Can someone advise the program installation
thanks!

---

