---
title: "Gparted won't work !"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-05-12
Machine: Dell inspiron 1440
OS: ubuntu 12.04 64 bit

Problem: i installed gparted. It shows up in bash too. when i try to open it typing ```
sudo gparted
```
i get the following:
```

winuxuser@MagicBox:~$ sudo gparted
/usr/sbin/gpartedbin: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
winuxuser@MagicBox:~$ 

```

any ideas gurus?

---

### Post by wilee-nilee on 2012-05-12
Check to see if this is installed.

libgtkmm-2.4-1c2a

Also gparted is a graphic so use gksudo.

---

### Post by nipunshakya on 2012-05-12
> **wilee-nilee said:**
> Check to see if this is installed.

libgtkmm-2.4-1c2a

This is already installed.

> **wilee-nilee said:**
> Also gparted is a graphic so use gksudo.
```
gksudo gparted
```
would yield me the screen that asks me for password to perform administrative task...and after that, i keep waiting and waiting but gparted doesnt show up...

Thanks for your quick reply.:)

---

### Post by nipunshakya on 2012-05-12
also, the file gpartedbin from the path /usr/sbin is also not available... :(

---

### Post by wilee-nilee on 2012-05-12
> **WinuxUser said:**
> also, the file gpartedbin from the path /usr/sbin is also not available... :(

I would purge it and reinstall if me to see what happens, I see bugs, older ones though in a google search with the error. One solution was also reloading that first post I made.

```
sudo apt-get purge gparted && sudo apt-get install gparted
```

---

### Post by carl4926 on 2012-05-12
working fine here
eeepc running 12.04 x86

---

### Post by nipunshakya on 2012-05-12
> **wilee-nilee said:**
> 
```
sudo apt-get purge gparted && sudo apt-get install gparted
```

i did that....and the output is something like 
```
winuxuser@MagicBox:~$ sudo apt-get purge gparted && sudo apt-get install gparted[sudo] password for winuxuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gparted*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,982 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 212583 files and directories currently installed.)
Removing gparted ...
Purging configuration files for gparted ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for menu ...



```
 and the blinker has been blinking for like more than 20 minutes now.... i don't think it should be that way...is it?

---

### Post by carl4926 on 2012-05-12
Startup synaptic and fix broken packages?!

---

### Post by nipunshakya on 2012-05-12
@wilee..
finally, the process finished...but still, no luck at all...
```
winuxuser@MagicBox:~$ sudo apt-get purge gparted && sudo apt-get install gparted[sudo] password for winuxuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gparted*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,982 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 212583 files and directories currently installed.)
Removing gparted ...
Purging configuration files for gparted ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for menu ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  reiser4progs ntfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/544 kB of archives.
After this operation, 1,982 kB of additional disk space will be used.
Selecting previously unselected package gparted.
(Reading database ... 212494 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.11.0-2_amd64.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up gparted (0.11.0-2) ...
Processing triggers for menu ...
winuxuser@MagicBox:~$ gparted
Root privileges are required for running gparted.
/usr/sbin/gpartedbin: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
winuxuser@MagicBox:~$ gksudo gparted
winuxuser@MagicBox:~$ 

```

nothing happened...

---

### Post by wilee-nilee on 2012-05-12
> **WinuxUser said:**
> i did that....and the output is something like 
```
winuxuser@MagicBox:~$ sudo apt-get purge gparted && sudo apt-get install gparted[sudo] password for winuxuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gparted*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,982 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 212583 files and directories currently installed.)
Removing gparted ...
Purging configuration files for gparted ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for menu ...



``` and the blinker has been blinking for like more than 20 minutes now.... i don't think it should be that way...is it?

No, it should not hang I just ran the command with no problems. Go ahead and shut the terminal and run these two commands to clear and possibly finish the run.

[FONT=Verdana, sans-serif][SIZE=1]```
sudo dpkg --configure -a
``` [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=1]```
sudo apt-get -f install
```[/SIZE][/FONT]

[FONT=Verdana, sans-serif][SIZE=1]After this I would look in synaptic for any broken packages, look in the custom filters.

If all looks good check gparted in synaptic to see if it is marked.

You may need to install synaptic as well.

[/SIZE][/FONT]```
sudo apt-get install gparted
```

---

### Post by nipunshakya on 2012-05-12
> **carl4926 said:**
> Startup synaptic and fix broken packages?!

mate, i did that too... and it gives the same result again...
i ran synaptic package manager, it prompted me for password... i entered...now, nothing seems to pop up...

I guess everything related to administrative task is being forbidden to the only user of this machine.. :(

---

### Post by carl4926 on 2012-05-12
Did you reboot recently?

---

### Post by nipunshakya on 2012-05-12
yepp.... my machine has been acting strangely since installing 12.04. i have to make a hard shutdown everytime i wish to reboot or shutdown...but im sure i did.. :)

---

### Post by carl4926 on 2012-05-12
> **WinuxUser said:**
> yepp.... my machine has been acting strangely since installing 12.04. i have to make a hard shutdown everytime i wish to reboot or shutdown...but im sure i did.. :)

Sounds a bit flaky - was it a clean install or upgrade?

---

### Post by nipunshakya on 2012-05-12
it was a clean install over 11.04. But the installation didnt went fine because i had to report a bug related to software center and ubiquity. I frequently have a message saying "Ubuntu has experienced an internal error" or something like that..

A message popped up few minutes ago saying me to report a bug about synaptic too..... its all messed up here :(

---

### Post by carl4926 on 2012-05-12
Might be worth trying again

Make sure the cd passes the check

---

### Post by nipunshakya on 2012-05-12
u mean i should make a fresh install after checking the USB?

---

### Post by nipunshakya on 2012-05-12
this would be my third time in a row if i do so... with different iso files downloaded at different times...do u think i should do another fresh installation of the OS?

---

### Post by nipunshakya on 2012-05-12
> **carl4926 said:**
> Might be worth trying again

Make sure the cd passes the check

the cd check gave an error with filesystem.squashfs .... is there any way to fix it?

---

### Post by wilee-nilee on 2012-05-12
> **WinuxUser said:**
> the cd check gave an error with filesystem.squashfs .... is there any way to fix it?

No download another and check it as well.

---

### Post by nipunshakya on 2012-05-12
i downloaded it from torrent as well, didnt work out...downloaded directly from official website too..didnt work out...i wonder where i would go looking for a good iso coz it takes almost 5 hrs to complete the download... i dont want to waste my bandwidth downloading a bad iso... mind suggesting me a a place where good iso for 64 bit is?

---

### Post by wilee-nilee on 2012-05-12
> **WinuxUser said:**
> i downloaded it from torrent as well, didnt work out...downloaded directly from official website too..didnt work out...i wonder where i would go looking for a good iso coz it takes almost 5 hrs to complete the download... i dont want to waste my bandwidth downloading a bad iso... mind suggesting me a a place where good iso for 64 bit is?

Really the ubuntu.com website links are what you want, torrent or http.

[FONT=Verdana, sans-serif][SIZE=1]So here is a link for the mini cd this is a netload.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) [/SIZE][/FONT]

---

### Post by nipunshakya on 2012-05-12
Recently, alot of google searches have made me to conclude that current 12.04 is not fully functional to everyone as expected...so maybe its worth a wait till some bugs gets fixed and then download? or ?

---

### Post by nipunshakya on 2012-05-21
Just finished installing 12.04 from newly downloaded .iso.
Guess there was some error with the 12.04 i installed previously. Everything works fine here now...Thank you all for your help and time.

Happy Linuxing. :D

---

