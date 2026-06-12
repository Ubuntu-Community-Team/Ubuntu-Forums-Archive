---
title: "help please I'm not quite sure what to do"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by teaker1s on 2006-06-03
part way through the update manager installing dapper power cut, now I have a system that boots old kubuntu/ubuntu screen shows loading modules then a new kubuntu screen appears and nothing more.

cant apt-get in recovery mode as I'm told sources unavaliable need to dpkg-- configure -a  which I tried and get comand not found and that's about it.
can I just burn an iso cd and sort this mess with the cd as a source and dist upgrade?

 

        sudo apt-cdrom add
     

        sudo apt-get update && sudo apt-get dist-upgrade
       

with the alternate 386 iso?

---

### Post by Patrick-Ruff on 2006-06-03
I'm thinking clean install, I mean, the OS is partway corrupted. have you tried recovery mode? I suggest you do that, backup all your files, then do a clean install.

---

### Post by teaker1s on 2006-06-03
recovery boot kernel works so I was hoping an apt-get install F or similar would solve my problem. a formatted disk and new install not a tempting option!!!

---

### Post by teaker1s on 2006-06-04
used apt get to install ubuntu desktop and all appears to be working;-) to the point I can see GUI and  run post fix in synaptic, no printer or scanner working but will see if this fixes it or wether config file needs altering again

---

### Post by ubuntu_demon on 2006-06-04
This is how it should be written :
$sudo dpkg --configure -a

---

### Post by teaker1s on 2006-06-04
okay, either way now I have a working system and needed an updated epson driver-which has sorted the scanner. I have no dpkg problems and synaptic is working only issue now is

E: samba: subprocess post-installation script returned error exit status 102

which i'm not sure if the script has a problem or something I need to fix?

---

### Post by ubuntu_demon on 2006-06-04
purge samba and reinstall it :
$sudo apt-get remove samba --purge
$sudo apt-get install samba

---

### Post by teaker1s on 2006-06-04
still got problems

daniel@ubuntu:~$ sudo apt-get remove samba --purge
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  samba*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 244350 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
daniel@ubuntu:~$

---

### Post by ubuntu_demon on 2006-06-04
$sudo update-rc.d -f samba remove
$sudo apt-get remove samba --purge

Let me know if it worked.

after that continue with this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by teaker1s on 2006-06-04
thanks for your assistance, still having problems with it 
daniel@ubuntu:~$ sudo update-rc.d -f samba remove
Password:
 Removing any system startup links for /etc/init.d/samba ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
   /etc/rc2.d/K09samba is not a link to ../init.d/samba; not removing
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
   /etc/rc3.d/K09samba is not a link to ../init.d/samba; not removing
daniel@ubuntu:~$ sudo apt-get remove samba --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  samba*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 244042 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rcarring on 2006-06-04
Run synaptic.

It should say that samba is broken, so you should run the fix broken packages option.

Next perform a complete removal of samba and samba-server -- this will delete conf files as well as the samba installation itself.

Next mark samba for install

Apply

This should reinstall samba for you.

---

### Post by ubuntu_demon on 2006-06-04
another possibility is removing the symlinks by hand.
To find them :

to update the slocate database (the package slocate needs to be installed) :

$sudo updatedb

to find the symlinks :
$locate samba | grep /etc/rc
you should get a result similar to :
```

/etc/rc0.d/K19samba
/etc/rc1.d/K19samba
/etc/rc2.d/S20samba
/etc/rc3.d/S20samba
/etc/rc4.d/S20samba
/etc/rc5.d/S20samba
/etc/rc6.d/K19samba

```

remove all those files by :
$sudo rm *filename*

for example :
$sudo rm /etc/rc6.d/K19samba

And after you have removed them all try to purge samba once more :
$sudo apt-get remove samba --purge

---

### Post by teaker1s on 2006-06-04
doesn't say samba is broken, infact 0 packages broken
can't perform a complete removal of samba and samba-server
returns 102 script error code as previous post and anything that relates to desktop just installed xfce desktop and synaptic returns E:not locked

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=teaker1s]doesn't say samba is broken, infact 0 packages broken
can't perform a complete removal of samba and samba-server
returns 102 script error code as previous post and anything that relates to desktop just installed xfce desktop and synaptic returns E:not locked[/QUOTE]
Try my answer above. IMHO it should probably work in your case.

---

### Post by teaker1s on 2006-06-04
ubuntu_demon 
thank you for your assistance and everyones suggestions, just so I know for future reference  the proceedure you suggested, does that basically un register the package so it can just be deleted or does something more technical occur? either way it's fixed I believe.

regards
Daniel

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=teaker1s]ubuntu_demon 
thank you for your assistance and everyones suggestions, just so I know for future reference  the proceedure you suggested, does that basically un register the package so it can just be deleted or does something more technical occur?
[/QUOTE]

Something more technical. In short : those files are needed to start and stop samba at the right time. 

For some reason the script couldn't handle the removing of these symlinks so we had to do it by hand.


[QUOTE=teaker1s]
 either way it's fixed I believe.

regards
Daniel[/QUOTE]

Everything is probably fixed but let's make sure.

Please do this to make sure every packages is configured properly :
$sudo dpkg --configure -a

Do this to ensure there are no broken dependencies :
$sudo apt-get remove -f

If there are any broken dependencies please make sure to read,understand and follow my guide here :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

also make sure to do this (even if there are no more broken dependencies) :
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop

---

### Post by teaker1s on 2006-06-04
yes I now remember update rc.d I've used it to load a custom keyboard mapping. I will have checked as you said and will read your dependencie's article. Guess I've found ubuntu so reliable that for months I've forgoton what I've learned-will have to play more under the hood.

thank you for all your help

regards Daniel

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=teaker1s]yes I now remember update rc.d I've used it to load a custom keyboard mapping. I will have checked as you said and will read your dependencie's article. Guess I've found ubuntu so reliable that for months I've forgoton what I've learned-will have to play more under the hood.

thank you for all your help

regards Daniel[/QUOTE]
no problem, good luck and have fun! :)

---

