---
title: "Authentification failure at Booting"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by laodan on 2006-06-13
I upgraded from Breezy Badger 5.10 to Dapper Drake 6.06. After a successful upgrade I worked a few hours on my newly installed 6.06 and was very satisfied I must say. Then I closed and re-opened the system. Everything was still working fine. 
An hour later I closed again and restarted and that is when I got stuck in a boot that landed me in a black screen with some Ubuntu commands (kind of DOS text). The loading of the system appeared normally in its graphical GUI but the usual window with username and password appeared in text. 

After input of my username at Ubuntu login I get the following:
CONFIGURATION ERROR - unknown item 'QUOTAS_ENAB' (notify administrator)
CONFIGURATION ERROR - unknown item 'NOLOGIN_STR' (notify administrator)
CONFIGURATION ERROR - unknown item 'ENV_HZ' (notify administrator)
CONFIGURATION ERROR - unknown item 'CHFN_AUTH' (notify administrator)
CONFIGURATION ERROR - unknown item 'CLOSE_SESSION' (notify administrator)

Then comes Password: I input my pass and I get the following:
"Last login: Tue 13 June ... on tty1
Linux Ubuntu 2.6.15.23.386 # PREEMT Tue May 23.. , 686 GNU/Linux"

Then comes the command line:
laodan@ubuntu:~$

I tried everything I could come up with as command but to no avail. 

Typing the command: 
laodan@ubuntu:~$ sudo apt-get -f install
I get the following message:
Password: I input my pass and then get:
Reading packege list... done
Building dependancy tree... done
o upgrade, 0 newly installed, 0 to remove, o not upgraded

Typing the command: 
laodan@ubuntu:~$ sudo dpkg -reconfigure xserver -xorg
I get the following message:
dpkg: conflicting actions --control and --remove

Typing the command:
laodan@ubuntu:~$ su
I get the following message:
su: Authentification failure
CONFIGURATION ERROR - unknown item 'QUOTAS_ENAB' (notify administrator)
CONFIGURATION ERROR - unknown item 'NOLOGIN_STR' (notify administrator)
CONFIGURATION ERROR - unknown item 'ENV_HZ' (notify administrator)
CONFIGURATION ERROR - unknown item 'CHFN_AUTH' (notify administrator)
CONFIGURATION ERROR - unknown item 'CLOSE_SESSION' (notify administrator)

What should I input as command to open my system?
And if that works where do I need to go to change the configuration?

Thanks in advance.

---

### Post by nanotube on 2006-06-13
[QUOTE=laodan]I upgraded from Breezy Badger 5.10 to Dapper Drake 6.06. After a successful upgrade I worked a few hours on my newly installed 6.06 and was very satisfied I must say. Then I closed and re-opened the system. Everything was still working fine. 
An hour later I closed again and restarted and that is when I got stuck in a boot that landed me in a black screen with some Ubuntu commands (kind of DOS text). The loading of the system appeared normally in its graphical GUI but the usual window with username and password appeared in text. 

After input of my username at Ubuntu login I get the following:
CONFIGURATION ERROR - unknown item 'QUOTAS_ENAB' (notify administrator)
CONFIGURATION ERROR - unknown item 'NOLOGIN_STR' (notify administrator)
CONFIGURATION ERROR - unknown item 'ENV_HZ' (notify administrator)
CONFIGURATION ERROR - unknown item 'CHFN_AUTH' (notify administrator)
CONFIGURATION ERROR - unknown item 'CLOSE_SESSION' (notify administrator)

Then comes Password: I input my pass and I get the following:
"Last login: Tue 13 June ... on tty1
Linux Ubuntu 2.6.15.23.386 # PREEMT Tue May 23.. , 686 GNU/Linux"

Then comes the command line:
laodan@ubuntu:~$

I tried everything I could come up with as command but to no avail. 

Typing the command: 
laodan@ubuntu:~$ sudo apt-get -f install
I get the following message:
Password: I input my pass and then get:
Reading packege list... done
Building dependancy tree... done
o upgrade, 0 newly installed, 0 to remove, o not upgraded

Typing the command: 
laodan@ubuntu:~$ sudo dpkg -reconfigure xserver -xorg
I get the following message:
dpkg: conflicting actions --control and --remove

Typing the command:
laodan@ubuntu:~$ su
I get the following message:
su: Authentification failure
CONFIGURATION ERROR - unknown item 'QUOTAS_ENAB' (notify administrator)
CONFIGURATION ERROR - unknown item 'NOLOGIN_STR' (notify administrator)
CONFIGURATION ERROR - unknown item 'ENV_HZ' (notify administrator)
CONFIGURATION ERROR - unknown item 'CHFN_AUTH' (notify administrator)
CONFIGURATION ERROR - unknown item 'CLOSE_SESSION' (notify administrator)

What should I input as command to open my system?
And if that works where do I need to go to change the configuration?

Thanks in advance.[/QUOTE]
try command "startx" and see if any errors occur.
if they do, try
```
sudo dpkg-reconfigure xserver-xorg
```
(you had extra spaces in the command you tried)

---

### Post by laodan on 2006-06-14
[QUOTE=nanotube]try command "startx" and see if any errors occur.
if they do, try
```
sudo dpkg-reconfigure xserver-xorg
```
(you had extra spaces in the command you tried)[/QUOTE]

Thanks for the advise.
Here's how I fare.

[COLOR="Red"]laodan@ubuntu:~$ startx[/COLOR]
Gives:
EE XF860 pen serial: cannot open device /dev/wacon   No such file or directory.
Error opening /dev/wacon. No such fule or directory
/usr/share/x11/fonts/misc refcount is 2, should be 1
waiting for xsever to shut down
laodan@ubuntu:~$
[COLOR="Red"]laodan@ubuntu:~$ sudo dpkg -reconfigure xserver-xorg[/COLOR]
The window configure xserver xorg opens:
I go through different windows and land finally in "Select your color depth in bits. When clicking enter I get the following message in text in the Ubuntu commands:
xserver-xorg postint warning: overwriting possibly -customized configuration file, backup in /etc/x11/xorg.config.2006061330448
laodan@ubuntu:~$

Thanks for the help.

---

### Post by laodan on 2006-06-14
I just solved my problem. It was related to the xserver and I found the solution in a sticky thread [Dealing with problems with the Xserver]("http://www.ubuntuforums.org/showthread.php?t=187177")

Seems quite many people have encountered this problem.
Thanks tseliot for the "how to" solve this frustrating bug.

---

