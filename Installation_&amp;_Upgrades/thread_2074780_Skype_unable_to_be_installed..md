---
title: "Skype unable to be installed."
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by jyphpps on 2012-10-22
Sorry I'm new to Ubuntu and this forum so do forgive me if I seem like I don't know what I'm doing. 

I have tried to install Skype for the past few days and have been receiving this error: 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

I have read that uninstalling purging skype-bin should do the trick but when i try purging it, i get a message saying that it does not exist. 

How should i go about installing skype?

Thanks in advance :)

---

### Post by aabed91 on 2012-10-22
First type this command

```
sudo apt-get -f install
```

Then type

```
sudo apt-get install skype
```

and it will be installed.

i hope these commands help you :)

---

### Post by jyphpps on 2012-10-24
I've tried those commands but they still return with the error: 

The following packages have unmet dependencies:

skype: Depends: skype-bin but it is not going to be installed

---

### Post by aabed91 on 2012-10-25
When i face this problem i type

```
sudo apt-get -f install
```

this command solve your problem

---

### Post by Lemagex on 2012-10-25
[http://www.skype.com/intl/en/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/)

Download the .deb for your system. And then go on terminal, 
```
sudo apt-get purge skype skype-bin
```
Regardless of it that finds it or not, install the Deb, I had to do that the other day and it worked for me, annoying though.

---

### Post by jyphpps on 2012-11-01
junyuan@ubuntu:~/Downloads$ sudo dpkg -i skype-ubuntu_4.0.0.8-1_amd64.deb
Selecting previously unselected package skype.
(Reading database ... 151037 files and directories currently installed.)
Unpacking skype (from skype-ubuntu_4.0.0.8-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on ia32-libs; however:
  Package ia32-libs is not installed.

dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 skype

I still get this error message when i purge. Is there a bug on this?

---

### Post by jyphpps on 2012-11-01
And how do y'all type code in these replies...

---

### Post by Lemagex on 2012-12-11
Do this completely fresh. Firstly, open your terminal, ```
sudo thunar /etc/apt/
```
look in the lists folder, and delete all "Skype" entries. Then proceed with the purge I suggested in the last post. then install the skype deb NOT USING terminal, but using a deb installer like gdebi or just the software center.

---

