---
title: "Upgrading to firefox 3.6 on ubuntu 8.10"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by ownsuall on 2010-02-02
I'm trying to upgrade to firefox on ubuntu 8.10 but I'm having bad luck and my packages keep getting "broken" so I need some help. how do I upgrade to firefox 3.6?

---

### Post by ownsuall on 2010-02-02
> **ownsuall said:**
> I'm trying to upgrade to firefox on ubuntu 8.10 but I'm having bad luck and my packages keep getting "broken" so I need some help. how do I upgrade to firefox 3.6?
I installed 3.6 using 
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script)
but I lost all my plug-ins -.-

---

### Post by nanotube on 2010-02-03
> **ownsuall said:**
> I installed 3.6 using 
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script)
but I lost all my plug-ins -.-

question 1: what specific plugins did you lose? do they show up in about:plugins? 

question 2: any particular reason you're using the old installer script, instead of the new repository?

---

### Post by Zifnab06 on 2010-02-03
First of all I'm amazed I remembered my login.....

Second of all, to install ff 3.6 on 8.10:

sudo apt-get remove firefox ubufox
sudo apt-get autoremove

Download firefox from Mozilla. Extract to /opt/mozilla/firefox. 
ln -s /usr/bin/firefox /opt/mozilla/firefox/firefox

What this does:

Gets rid of apt installation of firefox
Install from Mozilla (firefox will autoupdate now as well). 
Links /usr/bin/firefox to /opt/mozilla/firefox/firefox. So, if you run 'firefox' (minus quotes) in a terminal, you will get firefox. You'll need to create your own menu links using this method though.

---

### Post by ownsuall on 2010-02-03
I have firefox 3.6 installed had to use the old installer script the only way i could get it to install. I don't have ANY plugins.
this is what about:plugins looks like

No plugins are installed
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.

---

### Post by ownsuall on 2010-02-07
I got it fixed by running the commands
ln -s /usr/lib/jvm/ia32-java-6-sun-1.6.0.14/jre/lib/i386/libnpjp2.so /home/owner/.mozilla/plugins/libnpjp2.so

for java plugin and

sudo cp libflashplayer.so /home/owner/.mozilla/plugins/

---

