---
title: "Flashplayer-Nonfree - C'ant install updates anymore ????"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by artish on 2007-09-15
I recently installed Flashplayer 9 by removing the /home/flo/.mozilla/plugins/  files (all flash) and installing the tar.gz file from the Adobe Site ( [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) )

But now i can't install anything anymore. Updating and uninstalling also fails.
When I try to update/install it says:
```
The Package Flashplayer-Nonfree has to be reinstalled, but I can't find the archive. 
```


Please help, I couldn't find any solutions by searching!

Peace.

---

### Post by Gremlinzzz on 2007-09-15
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by artish on 2007-09-15
Doesn't help at all.

1) Install using Synaptic Package Manager or apt-get
Doesn't work, as I said I get this error:

```
The Package Flashplayer-Nonfree has to be reinstalled, but I can't find the archive.
```

2) Install from Firefox (method 2)
Doesn't help

3) Install from tarball (method 3)
Now i got a "usr/lib/flash-plugin" folder with the flash files.
Doesn't help




Please help me, I'm desperate :(

---

### Post by Gremlinzzz on 2007-09-15
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

---

### Post by artish on 2007-09-15
Yeah, I already did that.
But 
```
sudo apt-get remove flashplugin-nonfree
```
doesn't work 
```
The Package Flashplayer-Nonfree has to be reinstalled, but I can't find the archive.
```

:(

---

### Post by Gremlinzzz on 2007-09-15
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.1_i386.deb&md5sum=5b95c44aee4f6bb0b95aea49f3cf12fe&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Ff%2Fflashplugin-nonfree%2Fflashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.1_i386.deb&md5sum=5b95c44aee4f6bb0b95aea49f3cf12fe&arch=i386&type=security)
click security.ubuntu.com/ubuntu to get package

---

### Post by artish on 2007-09-15
man, still nothing...


allways this stupid error...

I can install the deb package but nothing really changes..

is there somthing like timemachine for ubuntu ? 
This started just yesterday..

---

### Post by Gremlinzzz on 2007-09-15
Is your computers processor AMD64?
if so 
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by Gremlinzzz on 2007-09-15
If its not 64 i have 1 idea left. go to home folder click show hidden files go to Mozilla folder check if theres a plugin folder there if not create 1. then install manualy.
download the flash to your desktop extract there .then open flash folder and copy the plugins to mozilla plugin folder. or drag and drop them.good luck

---

### Post by artish on 2007-09-15
> **Gremlinzzz said:**
> Is your computers processor AMD64?
if so 
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

Noo, i got Intel Pentium x86i 



:frown:

---

### Post by artish on 2007-09-15
> **Gremlinzzz said:**
> If its not 64 i have 1 idea left. go to home folder click show hidden files go to Mozilla folder check if theres a plugin folder there if not create 1. then install manualy.
download the flash to your desktop extract there .then open flash folder and copy the plugins to mozilla plugin folder. or drag and drop them.good luck

I did that so often :frown:

---

### Post by Gremlinzzz on 2007-09-15
whats in the mozilla folder  theres two folders  a firefox folder and a plugins folder .if ones missing create its names are === firefox====plugins===hope it helps

---

