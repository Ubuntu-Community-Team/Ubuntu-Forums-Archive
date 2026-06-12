---
title: "Updates"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by tjmoes on 2007-07-26
When trying to install updates I am getting this error msg

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

and when i try to run manully says i need to be super user which i thot i was already
:confused:

---

### Post by davidjmayo on 2007-07-26
```
sudo dpkg --configure -a
```

yuo do this from a terminal (applications==>accessories==>terminal)
sudo is used to run the command as SuperUser hence su
You are not superuser but you have the way to use it - a security feature of ubuntu. If you are superuser all the time it can lead to mistakes
If you want  to run a GUI as superuser then use gksudo : example

```
gksudo gedit /path/to/file
```

---

### Post by tjmoes on 2007-07-26
I never had to do a sudo to download updates and do i have to configure everysingle file that is to be dnloaded

---

### Post by Seisen on 2007-07-26
Do you use Synaptic or the update notification to download your updates ? Also you don't have to configure every file that is download.

---

### Post by davidjmayo on 2007-07-26
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

#1 you need sudo before the error command as above to correct the problem.

> I never had to do a sudo to download updates and do i have to configure everysingle file that is to be dnloaded

No you don't need sudo for updates or confugure every single file -  they should happen automatically when you fix the problem #1

---

### Post by tjmoes on 2007-07-26
i did the dpkg aND IT  wants me to configure something like a help file or something gave me a list of configures

---

### Post by tjmoes on 2007-07-26
> **Seisen said:**
> Do you use Synaptic or the update notification to download your updates ? Also you don't have to configure every file that is download.


i was using the update notification

---

### Post by Seisen on 2007-07-26
> **tjmoes said:**
> i did the dpkg aND IT  wants me to configure something like a help file or something gave me a list of configures

Can you post what it says when you put that in the terminal?

---

### Post by tjmoes on 2007-07-26
ted@ted-ubuntu:~$ sudo dpkg --config -a
Password:
dpkg: unknown option --config

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by Seisen on 2007-07-26
Actually its this 

```
sudo dpkg --configure -a
```

---

### Post by tjmoes on 2007-07-26
well now pkg manager doesnt work 
error in installing virtualbox cant find archive missing reinstall

but it wont install ither  grrrrrrrrrrrrr

this is what i am getting when trying to install
ted@ted-ubuntu:~$ sudo dpkg -i Desktop/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
dpkg-split: error reading Desktop/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb: Is a directory
dpkg: error processing Desktop/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 Desktop/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
 

cant get ither to work updates or virtualbox 
vicous circle of this not here or that not here  nothing updates or installs with any pakage manager or gbed

---

### Post by tjmoes on 2007-07-27
After reinstall v7.04 and trying to update i am getting this error

ted@ted-desktop:~$ sudo dpkg -i Desktop/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
Password:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `' must be followed by colon
ted@ted-desktop:~$ 

and I am not able to edit that file

---

