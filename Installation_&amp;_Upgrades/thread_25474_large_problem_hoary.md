---
title: "large problem hoary"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by lizardking on 2005-04-10
Large problem when I upgrade to hoary from warty. Xserver is not perfectly configured so Nvidia driver not work well without accelleration.**I run dpkg-reconfigure xserver-xorg** but nothing. NOw i have Xserver set without accelleration
xmms and tux racer goes in **segmentation falut** 
The update system **Ubuntu Update Manager** says that I cannot do update beacuse I must take a apt-get dist-upgrade but when I do this in terminal syas that there is **0**  packets to update.

I have read all [this advertisment](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes/view?searchterm=upgrade%20hoary) but nothing....
some help before return to warty?
 ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Buffalo Soldier on 2005-04-10
Whenever my Update Manager acts weird, this is what I usually do:```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get check
```What were the changes that you've made after running **dpkg-reconfigure xserver-xorg**?

---

### Post by cdhotfire on 2005-04-10
[QUOTE=lizardking]Large problem when I upgrade to hoary from warty. Xserver is not perfectly configured so Nvidia driver not work well without accelleration.**I run dpkg-reconfigure xserver-xorg** but nothing. NOw i have Xserver set without accelleration
xmms and tux racer goes in **segmentation falut** 
The update system **Ubuntu Update Manager** says that I cannot do update beacuse I must take a apt-get dist-upgrade but when I do this in terminal syas that there is **0**  packets to update.

I have read all [this advertisment]("http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes/view?searchterm=upgrade%20hoary") but nothing....
some help before return to warty?
 ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]

for dpkg-reconfigure xserver-xorg, work u must not be in X, this is why u should do:
```

sudo /etc/init.d/gdm stop

```
then do dpkg-reconfigure xserver-xorg.  :)

---

### Post by lizardking on 2005-04-10
[QUOTE=Buffalo Soldier]Whenever my Update Manager acts weird, this is what I usually do:```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get check
```What were the changes that you've made after running **dpkg-reconfigure xserver-xorg**?[/QUOTE]
at the beginning Xserver do not start: so i read the howto and run dpkg-reconfigure etc... I do the automatic searching of hardwer video adn set nvidia to main driver...
**This is my result** 
lizardking@iac:~ $ sudo apt-get clean
Password:
lizardking@iac:~ $ sudo apt-get clean
lizardking@iac:~ $ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Scaricato 2B in 1s (1B/s)
Lettura della lista dei pacchetti in corso... Fatto
lizardking@iac:~ $ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Scaricato 2B in 1s (1B/s)
Lettura della lista dei pacchetti in corso... Fatto
lizardking@iac:~ $ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Scaricato 2B in 1s (1B/s)
Lettura della lista dei pacchetti in corso... Fatto
lizardking@iac:~ $ sudo apt-get upgrade
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
lizardking@iac:~ $ sudo apt-get dist-upgrade
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
Calcolo dell'aggiornamento in corso... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
lizardking@iac:~ $ sudo apt-get check
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
lizardking@iac:~ $

---

### Post by lizardking on 2005-04-10
[QUOTE=cdhotfire]for dpkg-reconfigure xserver-xorg, work u must not be in X, this is why u should do:
```

sudo /etc/init.d/gdm stop

```
then do dpkg-reconfigure xserver-xorg.  :)[/QUOTE]
I do this..serverX at the beginnig not work! ;)

what about segmantation falut???  ](*,)
I think all application that need acceleration goes in segmentation fault also 3ddesk...

---

### Post by cdhotfire on 2005-04-10
Ubuntu's new nvidia-glx is kind of buggy i think, everyone is having problems with it, so i just switched to nv instead of nvidia. For some weird reason i can still play 3d games, and they are not slow. :)

---

### Post by lizardking on 2005-04-10
[QUOTE=cdhotfire]Ubuntu's new nvidia-glx is kind of buggy i think[/QUOTE]
GOOD so what can I do?
return to warty?
install hoary from CD?

---

### Post by wxm505 on 2005-04-10
I suffered from the same problem.
Is there any better way to fix the problems after updrade
from warty to hoary by Synaptic??

---

### Post by cdhotfire on 2005-04-10
[QUOTE=lizardking]GOOD so what can I do?
return to warty?
install hoary from CD?[/QUOTE]

You can try compiling the one from their site.  I heard alot of success from that.:-)

---

### Post by c_dog on 2005-04-10
The new Hoary nvidia-glx & nvidia-kernel-common (with the final release) is 1.0.7174, the same module as the one you'd get currently get with the script from the Nvidia site. It's been working great in either form. 6629 had problems. 6629 was in nvidia-glx until almost the last release candidates were out the door.

---

