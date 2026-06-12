---
title: "Can't update from 18.04.5 to latest"
date: 2022-02-14
forum: Installation &amp; Upgrades
---

### Post by michael-91 on 2022-02-14
Hi

I have Ubuntu 18.04.5 and I cant update to latest Ubuntu version because Ubuntu software says that I have the latest version and I get these errors: 

[IMG]https://i.ibb.co/k4tNpjK/Screenshot-from-2022-02-14-17-36-41.png[/IMG]
[IMG]https://i.ibb.co/JrXsZHK/Screenshot-from-2022-02-14-17-46-37.png[/IMG]

How can I get the latest version of Ubuntu the fastest way possible now?

[IMG]https://ibb.co/bskcxT1[/IMG][IMG]https://ibb.co/bskcxT1[/IMG]

---

### Post by SeijiSensei on 2022-02-14
Do you get this error while using
```
sudo apt update; sudo apt upgrade
```

If you're asking about where to find ISO images for recent releases, visit [https://cdimage.ubuntu.com/](https://cdimage.ubuntu.com/).

The next LTS release is 22.04 will come out in April. I'm running the early version at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).  The current LTS release, 20.04, is here: [https://ubuntu.com/download/desktop/thank-you?version=20.04.3&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=20.04.3&architecture=amd64).

---

### Post by michael-91 on 2022-02-15
[COLOR=#000000][COLOR=#222222][FONT=Verdana]Hi SeijiSensei[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I have managed to get Ubuntu version 18.04.6 thanks to that "sudo apt upgrade" that I did after the apt update.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]However, now I can't get any newer Ubuntu version anymore by using the terminal. Those errors were showing in "Ubuntu Software" where you can install Gimp very easy for example. It is an program for easy installation of programs for Ubuntu with an orange bag with an A for example as an icon.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I don't think my Ubuntu is so old and it is therefore weird that I can't update it to the latest version instantly.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]What is the best way to get the newest version without backing up and installing the newest Ubuntu version and then moving all the backuped files in again?

[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]P.s. Thank you for answering me.

Edit: When typing in sudo apt-get upgrade I get an error actually, here it is: 

"[/FONT][/COLOR][/COLOR]sudo apt-get updateHit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) bionic InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease                
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease              
Hit:5 [http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu](http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu) bionic InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease               
Err:7 [http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu) bionic InRelease
  403  Forbidden [IP: 91.189.95.85 80]
Ign:8 [http://ppa.launchpad.net/webupd8team/unstable/ubuntu](http://ppa.launchpad.net/webupd8team/unstable/ubuntu) bionic InRelease  
Err:9 [http://ppa.launchpad.net/webupd8team/unstable/ubuntu](http://ppa.launchpad.net/webupd8team/unstable/ubuntu) bionic Release    
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: Failed to fetch [http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu/dists/bionic/InRelease](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu/dists/bionic/InRelease)  403  Forbidden [IP: 91.189.95.85 80]
E: The repository 'http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu bionic InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webupd8team/unstable/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
root@HP-Compaq-6530b-NJ641UC-AK8:/home/michael# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
"

Maybe it helps so I don't need to reinstall.

Edit 2: Okey so I found a Canonical recommendation for reinstalling here so I will try to do it: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by MAFoElffen on 2022-02-15
Stop immediately!

Go to Activities > Start typing "Software & Updates" ... Select that Icon. When Software & Updates starts, select the second tab "Other Software". In the pane, look for and uncheck the checkboxes for 
```

http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu [COLOR=#ff0000]# which the error says it no longer is signed[/COLOR]
http://ppa.launchpad.net/webupd8team/unstable/ubuntu [COLOR=#ff0000]# which the error says no longer has a release file[/COLOR]

```
These are very old PPA's that have not been updated... And besides, if you were going to do a do-release-upgrade to upgrade your release to 20.04.x, you would need to disable all the PPA's beforehand anyways... Right?

Then do 
```

sudo apt update
sudo apt upgrade

```

Read the errors. Please think before you act rashly.

You do not need to reinstall anything.

---

### Post by michael-91 on 2022-02-15
Hi MAFoElffen

I successfully upgraded my Ubuntu to the latest version thanks to your explanation. I also unchecked the PPA's before.

Thank you.

---

### Post by MAFoElffen on 2022-02-15
You are very welcome. Happy that this worked out for you.

Please remember to select the "Thread Tools" link in the upper right of this page, then select "Solved" so that other users with similar problems can find your solution to help them.

---

