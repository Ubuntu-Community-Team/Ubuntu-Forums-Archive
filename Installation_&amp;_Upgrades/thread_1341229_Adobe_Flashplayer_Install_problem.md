---
title: "Adobe Flashplayer Install problem"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Bluefox79 on 2009-11-29
I'm a noob with ubuntu maybe ya'll can help me out, heres the output on an error box, I tried installing flash through the software manager.
<
installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

dpkg: error processing adobe-flashplugin (--remove):

 Package is in a very bad inconsistent state - you should

 reinstall it before attempting a removal.

Errors were encountered while processing:

 adobe-flashplugin

>?

I downloaded the .deb file and tried to install it, this error appears.
"Could Not Open 'install_flash_player_10_linux.deb'"
The package might be corrupted or you are not allowed to access the file.
Check the permissions of the file.

I checked the file's permissions and its all open, enabled to run as program and readwrite permissions for all.


jaccripper@jaccripper:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
jaccripper@jaccripper:~$ 
Thats the terminal output, I also tried updating the archives per another fix post I read so it might find the archive but it continues to produce the same result.

---

### Post by phillw on 2009-11-29
Hi try this first ..```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
```If that fails, then head over to [http://ubuntuforums.org/showthread.php?t=1305829&page=3](http://ubuntuforums.org/showthread.php?t=1305829&page=3) 
and follow the longer set of instructions.

regards,

Phill.

---

### Post by Bluefox79 on 2009-11-29
The long version fixed it, after all the stuff was done the .deb opened up and installed fine, thank you.

---

