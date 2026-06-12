---
title: "Installing Flashplayer 11 issues tar.gz"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by jukingeo on 2015-11-01
Hello All,

I been trying to update my flashplayer to Flash 11 and I had chosen to download the tar.gz file as normally I can click on the file and it would automatically install.

Well the file I downloaded will not install automatically.  I unpacked the file and read a readme in there.

Here is what the file says:

Adobe Systems Incorporated
Flash Player 11 for Linux
Version 11.2.202.540
2015

Adobe recommends that all users upgrade to the latest version of Adobe Flash 
Player for the most recent features, bug fixes, and security fixes.  For 
more information on the new features in Flash Player 9, please visit 
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/).  For more information on system 
requirements, fixed issues, and known issues, see the release notes at 
[http://www.adobe.com/go/flashplayer_releasenotes](http://www.adobe.com/go/flashplayer_releasenotes).

To confirm which version of Flash Player you have currently installed, see 
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/). Users should only install 
Players that have been downloaded from trusted sources, such as 
[http://www.adobe.com/](http://www.adobe.com/).

Your use of this player is governed by the Adobe End User License Agreement 
found at [http://www.adobe.com/products/eulas/players/flash/](http://www.adobe.com/products/eulas/players/flash/).


Privacy
-------

Adobe is committed to preserving the privacy of end users. For more 
information on configuring Client-side privacy visit the Settings Manager 
Documentation: [http://www.adobe.com/go/flashplayerhelp](http://www.adobe.com/go/flashplayerhelp).


Installation instructions
-------------------------

Installing using the plugin tar.gz:
	o Unpack the plugin tar.gz and copy the files to the appropriate location.  
	o Save the plugin tar.gz locally and note the location the file was saved to.
	o Launch terminal and change directories to the location the file was saved to.
	o Unpack the tar.gz file.  Once unpacked you will see the following:
		+ libflashplayer.so
		+ /usr
	o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
	o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
		+ cp libflashlayer.so <BrowserPluginsLocation>
	o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
		+ sudo cp -r usr/* /usr

Installing the plugin using RPM:
   o As root, enter in terminal:
          + # rpm -Uvh <rpm_package_file>
          + Click Enter key and follow prompts

Installing the standalone player:
   o Unpack the tar.gz file
   o To execute the standalone player,
          + Double-click, or 
          + Enter in terminal: ./flashplayer


Uninstallation instructions
---------------------------

Manual uninstallation (for users who installed the plugin via Install script):
   o Delete libflashplayer.so binary and flashplayer.xpt file in 
   directory /home/<user>/.mozilla/plugins/

RPM uninstallation:
   o As root, enter in terminal:
          + # rpm -e flash-plugin
          + Click Enter key and follow prompts


Technical Issues and Reporting Bugs
-----------------------------------
 
The Adobe Flash Player Support Center at 
[http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/) is a free online resource for 
support and troubleshooting information. Bug reports may be submitted at 
[http://www.adobe.com/go/wish](http://www.adobe.com/go/wish). To allow us to investigate reported bugs, 
please include the following information:
 
1) Platform and version
2) Browser version
3) Reproducible steps including a URL to the web site where the problem 
   was encountered.
 
If we need further information about a bug, you will be contacted. An 
automated reply will be sent to assure you that we have received your 
bug report. Due to the volume of mail received, we are not able to 
individually respond to each report.

Use the following commands to generate dependency lists for Flash Player or the Local Setting Manager:
 
Flash Player:
ldd <BrowserPluginsLocation>/libflashplayer.so
 
Gnome Local Setting Manager:
ldd /usr/lib/kcm_adobe_flash_player.so (for 32-bit systems)
ldd /usr/lib64/kcm_adobe_flash_player.so (for 64-bit systems)
 
KDE Local Settings Manager:
ldd /usr/bin/flash-player-properties


Legal
-----

Adobe(R) Flash(R) Player. Copyright (C) 1996 - 2015 Adobe Systems 
Incorporated. All Rights Reserved. Adobe and Flash  are either 
trademarks or registered trademarks in the United States and/or 
other countries.



Now my question is this:

Is there an easier way to install this?  There seems like a good potential to mess things up doing this manually.

Please help as I cannot use a couple of my Linux programs if I do not upgrade to version 11.2

Thank You.

Geo

---

### Post by qamelian on 2015-11-01
No need to download the installer from Adobe. Just install flashplugin-installer from Software Center / Synaptic / whatever package manager frontend is used by Ubuntustudio.
Or open a terminal and use the command:
```
sudo apt-get install flashplugin-installer
```

This will allow you to also receive automatic updates to Flash.

---

### Post by kurt18947 on 2015-11-01
> **qamelian said:**
> No need to download the installer from Adobe. Just install flashplugin-installer from Software Center / Synaptic / whatever package manager frontend is used by Ubuntustudio.
Or open a terminal and use the command:
```
sudo apt-get install flashplugin-installer
```

This will allow you to also receive automatic updates to Flash.

Absolutely!! Avoid 'Windows style' software installs if possible. Repositories or PPAs are much easier and less likely to give you more than you were expecting (malware etc.) I've had no problems with Flash 11.2.xxxx. It is kept up-to-date for security fixes. 

Pepperflash installer (Google's version of Adobe's flash) is available in the repositories. I've installed Chromium and it sees and uses Pepperflash. There is a developmental project called freshplayer that enables Pepperflash on Firefox . I have it running on one machine and it seems pretty stable. It would certainly be nice if Flash would disappear  but I don't see that happening anytime soon.

---

### Post by jukingeo on 2015-11-29
> **kurt18947 said:**
> Absolutely!! Avoid 'Windows style' software installs if possible. Repositories or PPAs are much easier and less likely to give you more than you were expecting (malware etc.) I've had no problems with Flash 11.2.xxxx. It is kept up-to-date for security fixes. 

I actually never had a malware or spyware issue with Linux.  But Windows...sheesh, don't get me started on that.

> 
Pepperflash installer (Google's version of Adobe's flash) is available in the repositories. I've installed Chromium and it sees and uses Pepperflash. There is a developmental project called freshplayer that enables Pepperflash on Firefox . I have it running on one machine and it seems pretty stable. It would certainly be nice if Flash would disappear  but I don't see that happening anytime soon.

> **qamelian said:**
> No need to download the installer from Adobe. Just install flashplugin-installer from Software Center / Synaptic / whatever package manager frontend is used by Ubuntustudio.
Or open a terminal and use the command:
```
sudo apt-get install flashplugin-installer
```

This will allow you to also receive automatic updates to Flash.


Thanks for the info, but I recently upgraded to Ubuntu Studio 14.04 LTS and the problem went away with the upgrade.

Geo

---

