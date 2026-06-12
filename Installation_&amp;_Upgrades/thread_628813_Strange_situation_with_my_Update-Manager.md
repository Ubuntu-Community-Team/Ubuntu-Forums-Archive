---
title: "Strange situation with my Update-Manager"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by tranquillo on 2007-12-01
HI! 

Im started with Ubuntu 6.10 and never left it since! :) this also not the first time i Install Ubuntu. but after Installing Ubuntu this time something strange happened - i fixed the Internet Settings (Privat WLAN) connected successfully to the web and waited for the Update Manager to start - witch did not :( so i opened my Terminal "sudo apt-get update" and he did not search the web for it... he just looked inside "D" (CD-ROM) so i opened the Update Manager manually and launched a search.... After notifying me that my System was up-to-date i got suspicious... so i went to my NB (Ubuntu 7.10 up and running!) and i noticed when i launch "sudo apt-get update" at first he searches in "D" then Get:1 [http://archive.ubuntu.com....etc](http://archive.ubuntu.com....etc)... why is my PC not getting the the urls?  i also thought that something could be wrong with my source list but also it was directed to "D"  in consequence i have 2 Hardware parts that the "Restricted Driver Manager" wont install - one of them is my Graphic card - and without that it will mean no Compiz - NOT GOOD. 

I have no idea if this question is already answered in this Forum, so ill just hope somebody will answer me again - or tell me where i can find the answer..

Thanks and Take care
tranquillo

---

### Post by Pumalite on 2007-12-01
Post the output of:
sudo apt-get update

---

### Post by tranquillo on 2007-12-01
and how?

no clue what you mean with " Post the output of: sudo apt-get update "

thanks

tranquillo

---

### Post by Pumalite on 2007-12-01
Applications>Accessories>Terminal
There type: sudo apt-get update
Copy and paste in this forum the output.

---

### Post by tranquillo on 2007-12-02
Sorry...

ok, here is my out-put of sudo apt-get update

tranquillo@tranbuntu:~$ sudo apt-get update 
[sudo] password for tranquillo:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done

see... he just stops there... and does not get all the Url he should.

and the same thing for the "Restricted Drivers Manager" the ERROR he gives for my ATI Driver is 

The software source for the package

   xorg-driver-fglrx

 is not enabled

For my Modem Driver is:

Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/

--> as soon as i do - no results


i think it all has to do that he does not search the inet for the updates... what do you think?


Thanks and hopefully soon

tanquillo

---

### Post by Pumalite on 2007-12-02
Post:
cat /etc/apt/sources.list

---

### Post by tranquillo on 2007-12-02
sudu cat /etc/apt/source.list :

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

so far is see its ok? ??

again thanks

tranquillo

---

### Post by Pumalite on 2007-12-02
Backup first:
sudo cp /etc/apt/sources.list /ets/apt/sources.list.back (copy and paste in your Terminal)
gksudo gedit /etc/apt/sources.list
Uncomment all the lines that start with 'deb' (remove the #)
Save and exit
Reboot
Run again:
sudo apt-get update and post it.

---

### Post by tranquillo on 2007-12-04
Sorry again! sadly no time to try your advice!

FInaly did... the "sudo apt-get update" ran wonderful! i also installed the missing ATI Driver and in this second i am running the "Update Manager"! YEAH! seems like everythings ok..

as soon as i finish all the System Required Updates -  and after the Re-Boot ill Post a end result..

be back in a sec.

tranquillo

---

### Post by tranquillo on 2007-12-04
OK..

- sudo apt-get update works fine.
- ATI Driver Installed
- All Packets Installed fine.

--> good job! i did not know that the "#" has to be removed or better - i did not even realize it! thanks! Do you know why the "#" where there?

what still does not work!

The Restricted Driver Manager still does not Install my Modem... even if im Old-School, who needs a 56K modem? :) so i can live with out it....

when i start my NB the Ubuntu boot-loading screen does not appear, i thought i had something to do with my ATI Driver - but now that its installed i dont see any reason why it should not work. + it took my NB (Centrino 1,8Ghz with 1GB Ram) about 5min to boot - witch cant be right - any ideas?

thanks allot! so far your the man! :) good work! and again THANKS! 

Id be thankful for more support.

tranquillo

---

### Post by Pumalite on 2007-12-04
You might have to configure your xserver.
Ctrl+Alt+F1 to get command line
If it's a login, then: username, password
Sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

