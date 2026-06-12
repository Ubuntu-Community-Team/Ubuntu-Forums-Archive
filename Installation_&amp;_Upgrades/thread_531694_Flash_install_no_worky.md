---
title: "Flash install no worky"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by Devile on 2007-08-21
> Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~dapper1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bumps-multimedia:
 bumps-multimedia depends on flashplugin-nonfree; however:
  Package flashplugin-nonfree is not configured yet.
dpkg: error processing bumps-multimedia (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree
 bumps-multimedia
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@matt-laptop:~$ sudo apt-get install gsfonts gsfonts-x11
Reading package lists... Done
Building dependency tree... Done
gsfonts is already the newest version.
gsfonts-x11 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~dapper1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bumps-multimedia:
 bumps-multimedia depends on flashplugin-nonfree; however:
  Package flashplugin-nonfree is not configured yet.
dpkg: error processing bumps-multimedia (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree
 bumps-multimedia
E: Sub-process /usr/bin/dpkg returned an error code (1)


all that from trying to install bumps, or flash....  PLEASE HELP

---

### Post by Gremlinzzz on 2007-08-21
irst remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.
unless you have 64amd for that 
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by Devile on 2007-08-22
THanks that worked...

---

