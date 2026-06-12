---
title: "upgrading to 13.10 and replacing DeepIn"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by jimfl on 2013-10-01
I recently installed DeepIn and don't like it. Can't figure out how to remove it. (No, there is no option to choose 13.04 as opposed to DeepIn on bootup--not on my screen, anyway.)

What I want to know is when I upgrade to 13.10 will that automatically replace DeepIn or will I still be stuck with it?

Thanks,
Jim

---

### Post by Frogs Hair on 2013-10-01
Could you provide some information about how you installed Deepin ? It appears to be a different distribution , but I don't know if you installed it as a desktop environment. It may not be the best idea to upgrade with it installed especially if you can't access the Ubuntu desktop. You could wait until 13.10 is released backup your files and do a clean installation .

---

### Post by jimfl on 2013-10-01
I followed the instructions on this Webpage: [http://www.maketecheasier.com/install-linux-deepin-desktop-on-ubuntu/2013/07/02?utm_source=newsletter&utm_medium=email&utm_campaign=02072013](http://www.maketecheasier.com/install-linux-deepin-desktop-on-ubuntu/2013/07/02?utm_source=newsletter&utm_medium=email&utm_campaign=02072013)

The main one being:  [TABLE="width: 100%"]
[TR]
[TD="class: code, bgcolor: #EEEEEE"][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] dde-meta-core[/TD]
[/TR]
[/TABLE]

So it is installed as my desktop environment. I'm REALLY hoping there's a way other than a clean install because the last time I did that it took a real long time to get everything tweaked  back to the way I had it before the install.

---

### Post by Frogs Hair on 2013-10-02
You could simply do the reverse of what was installed and remove the software source from software & updates > other software. Backup first in-case of problems. I don't like that you can't access Ubuntu from the login selection . I think 13.10 comes with Gnome 3.8 so any tweaking may be overwritten during the upgrade.  


```
sudo apt-get remove package-name
```

---

### Post by jimfl on 2013-10-07
[COLOR=#222222][FONT=Verdana]Frog's Hair, I really appreciate your help.[/FONT][/COLOR]

[SIZE=5][SIZE=4]I tried your suggestion of [/SIZE]
[/SIZE]sudo apt-get remove package-name  
by using
sudo apt-get remove package-dde-meta-core

[COLOR=#222222][FONT=Verdana]After rebooting, the change didn't seem to have any effect.

I went to Software and Updates and found two       pertinent tabs. On the first, Linux Deepin Software, I unchecked       "Deepin-supported Open Source Software." I left the other options       checked (Software restricted by copyright, Community maintained       free and Open Source software, and Source Code--this last one had       a dash rather than a check mark beside it).[/FONT][/COLOR]
     
     [COLOR=#222222][FONT=Verdana]Clicking on the Other Software tab, I couldn't find       the Deepin choices to deselect. I'm attaching two screenshots of       the choices available to me in the hope that you can find what       needs to be unchecked.[/FONT][/COLOR]

---

### Post by mauro-rossi on 2013-10-18
Hi, I had problems too after installing Deepin Desktop Environment on ubuntu 13.04, very bad problems.

DDE messed up with software distribution packages of Ubuntu I had to perform all these tasks:

- uninstalling packages having deepin in the full description of packages
- removing deepin sources from /etc/apt/sources.list
- search for deepin references in /var/lib/dpkg/status and remove + reinstall them

Important - change back the Debian /etc/issue file...

sudo nano /etc/issue

...from 'Linuxdeepin /n /l' to 'Ubuntu 13.04 /n /l' ( CTRL+O to write CTRL+X to exit)

Now to the lsb-release...

sudo nano /etc/lsb-release

...that should look like:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


Because of changed dependencies, I also extracted the packages list (using sudo dpkg) from a brand new Ubuntu 13.04 installation  and reinstalled (--reinstall option) all packages 

[on a different installation]

sudo dpkg --get-selections > packages.txt[on the Deepin DE "sick system", it will take a long time]

cat packages.txt | grep install | awk '{system ("sudo apt-get install -y --reinstall " $1)}'

Mauro

---

### Post by Frogs Hair on 2013-10-18
> **jimfl said:**
> [COLOR=#222222][FONT=Verdana]Frog's Hair, I really appreciate your help.[/FONT][/COLOR]

[SIZE=5][SIZE=4]I tried your suggestion of [/SIZE]
[/SIZE]sudo apt-get remove package-name  
by using
sudo apt-get remove package-dde-meta-core

[COLOR=#222222][FONT=Verdana]After rebooting, the change didn't seem to have any effect.

I went to Software and Updates and found two       pertinent tabs. On the first, Linux Deepin Software, I unchecked       "Deepin-supported Open Source Software." I left the other options       checked (Software restricted by copyright, Community maintained       free and Open Source software, and Source Code--this last one had       a dash rather than a check mark beside it).[/FONT][/COLOR]
     
     [COLOR=#222222][FONT=Verdana]Clicking on the Other Software tab, I couldn't find       the Deepin choices to deselect. I'm attaching two screenshots of       the choices available to me in the hope that you can find what       needs to be unchecked.[/FONT][/COLOR]


If you followed the suggestion to backup then I would save yourself a headache and do a clean installation of 13.10.

---

