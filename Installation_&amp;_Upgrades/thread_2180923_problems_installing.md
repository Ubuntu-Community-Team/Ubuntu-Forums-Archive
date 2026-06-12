---
title: "problems installing"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by 4dr14n on 2013-10-15
Hello everyone, sorry but I have some noob's doubts... Actually I've 3 of them...
first of all... using the cromium browser that comes with the distro I can't upgrade the adobe flash (actually, I can't click on the downloading button and I don't know how to do it from the console...)
second... I can't install skype either... I've read that is a normal problem to not to be able to do that but I can't do it following those instructions either.
And finally, when I try to install some software (firefox, thunderbird...) from the repositories it appears a dialogue saying that I need to install "unsafe" packets and it doesnt go on...


Maybe I should have done it separately, but I thought that probably, you will be able to answer all of them.

Thank you so much!!

---

### Post by sudodus on 2013-10-15
This command installs flash for Firefox.

```
sudo apt-get install flashplugin-installer
```

I'm not sure about Chromium-Browser, but I think Chrome comes with Flash built-in.

I don't bother with the latest and greatest Skype, but use the version in the Ubuntu repositories

```
sudo apt-get install skype
```

Firefox and Thunderbird should install without unsafe packages. Please try with the following commands

```
sudo apt-get install firefox
sudo apt-get install thunderbird

```

and report back whatever output you get in the terminal (copy and paste and put within code tags (the # icon at the top of the editing window)).

---

### Post by 4dr14n on 2013-10-15
adrian@adrian-Latitude-D531:~$ sudo apt-get install flashplugin-installer[sudo] password for adrian: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
flashplugin-installer ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 163 no actualizados.


adrian@adrian-Latitude-D531:~$ sudo apt-get install skype
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete skype

adrian@adrian-Latitude-D531:~$ sudo apt-get firefox
E: Operación inválida: firefox 

adrian@adrian-Latitude-D531:~$ sudo apt-get thunderbird
E: Operación inválida: thunderbird
adrian@adrian-Latitude-D531:~$ ^C
adrian@adrian-Latitude-D531:~$ 


It didn't work, it's Spanish, so I'll translate, but it said that it couldnt find skype, that flash is already on its lastest version and that there is an invalid operation both with thunderbird and firefox...

---

### Post by sudodus on 2013-10-15
0. I'm not sure about the first output '163 no actualizados'.

try these commands to get 'standard English output'
```
LC_ALL=C
LANG=C
```

Maybe you should make the installation up to date with

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade     # if some packages were held back by upgrade
```

1. You need to activate the repository with Skype. *Edit*: I don't remember, maybe it is '***Canonical Partners***', that you can find with ***Synaptic***.

2. Sorry I forgot ***install*** in the last two commands, so try

```
sudo apt-get install firefox
sudo apt-get install thunderbird
```

---

### Post by fantab on 2013-10-15
To install Skype you have to enable "Canonical Partners" Repository. You can do so with Software-Center->Edit->Software Sources. While you are at it also enable 'Independent' Repository.

For flash-player install 'lubuntu-restricted-extras', it will install flash as well as certain restricted codecs for popular formats like mp3 etc.
```
sudo apt-get install lubuntu-restricted-extras
```

Edit: I don't think Chromium comes with flash enabled. Its Google-Chrome that does.

---

### Post by 4dr14n on 2013-10-15
Sorry if I don't put the outputs in English, but I am who is learning and prefer to maintain it like they are. 
Ok, I did what you (all) said, I upgraded, updated and activated the "canonical" partners.

Ok, now, it's in Spanish but when I try to install skype 
> sudo apt-get install skype

the message is the next one.

> adrian@adrian-Latitude-D531:~$ sudo apt-get install skype 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete skype


Basicaly, it hasn't been possible to locate the packet....



Thank you guys one more time!

---

### Post by sudodus on 2013-10-15
You need to update ***after*** adding the new repository (canonical partners).

```
 sudo apt-get update
```

Then the skype package should be found.

---

### Post by 4dr14n on 2013-10-15
I can't update, look what appears...

> adrian@adrian-Latitude-D531:~$ sudo apt-get update[sudo] password for adrian: 
E: No se pudo encontrar el método /usr/lib/apt/methods/httep.


sorry and thanks!!

---

### Post by fantab on 2013-10-16
[QUOTE=4dr14n (google translate)]adrian @ adrian-Latitude-D531: ~ $ sudo apt-get update 
E: Could not find the method / usr / lib / apt / methods / **httep**.[/QUOTE]

The problem is "httep", when it should be "http". 

Read carefully and Post the output of:
```
$ cat /etc/apt/sources.list
```

If you see any 'httep' in there correct it to 'http', you can use gedit to do so:
```
$ sudo gedit /etc/apt/sources.list
```

Then run 'sudo apt-get update' again.

---

### Post by mastablasta on 2013-10-16
gksu gedit

use gksu instead of sudo for graphical applicaitons.
or 
sudo nano

nano is cli editor

---

### Post by 4dr14n on 2013-10-16
> adrian@adrian-Latitude-D531:~$ cat /etc/apt/sources.listç# deb cdrom:[Lubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)]/ raring main multiverse restricted universe


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring restricted multiverse main universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates restricted multiverse main universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security restricted multiverse main universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
**deb httep://archive.canonical.com/ raring partner**
**deb-src httep://archive.canonical.com/ raring partn**er
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main




I found them but I don't know how to change them sorry....
Thank you again!!

---

### Post by fantab on 2013-10-16
I told you how to in my previous post...

Open the file in Gedit as root and change it:
```
$ gksu gedit /etc/apt/sources.list
```

---

### Post by 4dr14n on 2013-10-16
ufff.... I wrote what you said, but, aparently, it happened nothing...
But I think I don't follow you... I don't know what is Gedit, or how to set is as root... 
and, when I wrote "sudo apt-get update", the same error message appeared...

We can say that I'm blocked....

sorry for my ignorance, and thank you one more time

---

### Post by sudodus on 2013-10-16
gedit is a text editor with a graphical user interface. sudo/gksu are the commands to run as root (to get superuser privileges).

So use the following command line in a ***terminal window***. You get such a window with the hotkey combination ***ctrl + alt + t***

```
gksu gedit /etc/apt/sources.list
```

*Edit*: you can copy and paste the command line from your browser to your terminal window. Enter your password when asked for it and finally: remove the [SIZE=4][COLOR=#ff0000]**e**[/COLOR][/SIZE]s to get http instead of httep, save and exit from the editor.

*Edit2*: If you have a pure Lubuntu, you should use leafpad instead of gedit, so

```
gksu leafpad /etc/apt/sources.list
```

---

### Post by fantab on 2013-10-16
Gedit is Text-editor like Notepad in Windows. We open it as root because the file 'sources.list' can only be edited as root.

---

### Post by sudodus on 2013-10-16
If you have no gedit program installed, use ***leafpad*** (see my previous post).

---

### Post by 4dr14n on 2013-10-16
that was the point!! when I put leafpad it worked, and, now I understand what you meant =). 
I deleted the extra "e"s and updated, and I'm already able to install skype, thanks a lot!!!

---

### Post by sudodus on 2013-10-16
Congratulations :KS

When all your problems in the first post are solved, please click on **Thread Tools** and mark this thread as SOLVED :-)

---

