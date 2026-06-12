---
title: "Bug during installation of LinuxMCE"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by davila4 on 2009-11-21
Hi,
I am new to Linux and have installed kubuntu some weeks ago.
So far all OK.
I wanted now to discover LinuxMCE and I have troubles, while following the wiki

 [http://wiki.linuxmce.com/index.php/Installation_Guide](http://wiki.linuxmce.com/index.php/Installation_Guide)


1st:
Could not get the MCE installer onto the desktop 
2nd
I could find the file in the root directory
usr/share/mce-installer/
and used the command
sudo ./mce-installer.sh
the first steps when ok, I indicated the location of the ISO's of CD1 and CD2 as well as the one of kubuntu 9.10.
After a while I got the following message:
Installation Failed:
Could not cache LMCE CD 1.
I have cheched the md5sum of the ISO they are ok.

Any clue on what to do.
I have read about the solution on installing from a DVD but it will erase everythin, and I having both linux and XP on my PC.

Thanks for any help


Thierry

---

### Post by Nathan.Flow on 2010-08-13
You can't do that. There's something in the LMCE installer, that won't allow you to use different versions. For example, you have to be running the same version of kubuntu as the live cd your using. More specifically kubuntu 7.10 nothing else will work, trust me I've tried. 

Feel free to look at my post concerning this. my user name is tux-box1 on their forms.

---

