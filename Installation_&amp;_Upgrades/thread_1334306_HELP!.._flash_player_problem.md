---
title: "HELP!.. flash player problem"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by abhishekdagr8 on 2009-11-22
HELPP!!!... I cant stream videos..
there is some problem with my flash player.. it doesn't seem to reinstall..
it can't find some chache for it.. i don't know what that means but please.. some one help me.. i can't do anything without my flashplayer

---

### Post by slakkie on 2009-11-22
See the link in my sig :)

---

### Post by ghostborg on 2009-11-22
Let people know which version of Ubuntu you are running 32/64, Flash in 64bit is not straight forward.
I can't remember but I think you uninstall the flash-non-free and have to copy the adobe beta flash 10 version to a plugin directory.
Search in ubuntu forums if that is your case. 
Good Luck.

---

### Post by darkod on 2009-11-22
I am new to Ubuntu and not specialist, but no problems here. I am running desktop 64bit 9.10 and I only have installed flashplugin-nonfree with no special commands, just:
sudo apt-get install flashplugin-nonfree

Unless you are trying to access some specific content.

PS. There have been reports of not working properly if conflicting plugins are installed, do not install all of them. If I understood correctly you have to remove swfdec-mozilla and gnash (not sure how the package is called exactly).

---

### Post by highkftj on 2009-11-29
Hello,

I have just installed ubunto 9.1 desktop (last version) and I cannot figure out how to install the flash plugin. I went to adobe website, download the deb package and follow the instructions. what I get is the following from update manager:

gdebi-gtk

could not open 'install_flash_player_10_linux.deb'

the package might be corrupted or you are not allowed to open the file. check the permissions of the file


I changed the permissions setting rxw for uga but noghing also with the manual installation with sudo

I tried to follow the instruction on this post

[http://ubuntuforums.org/showthread.php?t=636397&page=16](http://ubuntuforums.org/showthread.php?t=636397&page=16)

but it didn't change anything.. for some reasons I cannot post my problem there so here I posted. the error I get is

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

any time I am trying to install or uninstall the flushplugin-nonfree

please help!!!

---

### Post by slakkie on 2009-11-29
Have a look in my sig, as stated earlier in this thread.

---

### Post by highkftj on 2009-11-29
Perfect, it worked for me... don't know why those two rows were commented out on that file...

I couldn't actually install many pachages deb

thanks

---

