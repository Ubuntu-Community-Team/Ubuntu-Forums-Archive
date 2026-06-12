---
title: "Managed to Install Ubuntu fine but no GUI"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by eXSBass on 2005-11-26
Hi! I managed to install Ubuntu fine on my computer. But when it was starting up after installation there was an "X-Server" error. Its not starting up resulting Ubuntu to go into text mode. Can I fix this?

On a positive note i'm pleased to say the installation was quick, probably due to the 64bit instruction set.

Edit: Just saw this on a Googled web page:

"Nevermind, got the fix in another forum. Had to change the driver from 'ati' to 'radeon' in xorg.conf"

I've got a ATI HIS Excalibur x800xl. Is this the problem? Do I need to change the driver to "radeon"?

---

### Post by towsonu2003 on 2005-11-26
try this: sudo dpkg-reconfigure xserver-xorg 

defaults are okay for most of the time...

if it doesn't work, either try this:
sudo dpkg-reconfigure xserver-xfree86

or take a look at output by doing tail /var/log/Xorg.0.log right after the GUI failed to start... It might give u an idea about the error. 

If it is saying something like "xserver-xorg is broken or not fully installed", sudo apt-get install -f  then reconfiguring xserver should fix it... ( [http://ubuntuforums.org/archive/index.php/t-25414.html](http://ubuntuforums.org/archive/index.php/t-25414.html) ). I believe you will need a network connection and/or the installation CD mounted (sudo mount /media/cdrom) to do that... 

PS. if you have network connetion working in ubuntu without GUI, you can use lynx (text based web browser) to google etc... command for that is sudo apt-get lynx . not hard to use once u get sed to it. 
PS2. Are you sure the install cd was not corrupted? checking for md5sum for the iso file and choosing a slower burn speed can help.

---

### Post by eXSBass on 2005-11-27
[QUOTE=towsonu2003]try this: sudo dpkg-reconfigure xserver-xorg 

defaults are okay for most of the time...

if it doesn't work, either try this:
sudo dpkg-reconfigure xserver-xfree86

or take a look at output by doing tail /var/log/Xorg.0.log right after the GUI failed to start... It might give u an idea about the error. 

If it is saying something like "xserver-xorg is broken or not fully installed", sudo apt-get install -f  then reconfiguring xserver should fix it... ( [http://ubuntuforums.org/archive/index.php/t-25414.html](http://ubuntuforums.org/archive/index.php/t-25414.html) ). I believe you will need a network connection and/or the installation CD mounted (sudo mount /media/cdrom) to do that... 

PS. if you have network connetion working in ubuntu without GUI, you can use lynx (text based web browser) to google etc... command for that is sudo apt-get lynx . not hard to use once u get sed to it. 
PS2. Are you sure the install cd was not corrupted? checking for md5sum for the iso file and choosing a slower burn speed can help.[/QUOTE]



yeh, cheers for the reply mate. I managed to get the GUI working in the end by changing the drivers from "ati" to "vesa" in xorg.conf. However, I still haven't put in the native x800xl drivers in yet, i'm going to do it this afternoon and see if everything is hunkydoorey.

---

