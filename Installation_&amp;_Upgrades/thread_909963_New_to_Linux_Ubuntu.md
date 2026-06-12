---
title: "New to Linux Ubuntu"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by Dy-J_athan on 2008-09-04
Hi all. I am a new linux user that needs your help. I have ubuntu 6.06 installed and I need to install pidgin on it. will someone help me how to do this. :confused:

---

### Post by Partyboi2 on 2008-09-04
You could try downloading the deb from [[COLOR=Blue]here[/COLOR]]("http://drsjlazar.blogspot.com/2007/05/pidgin-for-dapper.html") Once you have downloaded the deb package Open a terminal and install these packages
```
sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev libgtkspell-dev
```then double click on the downloaded deb package to install it.
Or change to the directory in the terminal where the downloaded deb is. So if its on your Desktop
```
cd ~/Desktop
```then to install
```
sudo dpkg -i packagename
```(change packagename to actually name)
Or the 2nd option is to  compile it from source following [[COLOR=Blue]these[/COLOR]]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/") instructions.

---

### Post by Bucky Ball on 2008-09-04
Just one question, how come you have 6.06 installed?

Pidgin comes with the Hardy 8.04 installation.

You could also just go** Applications->Add/Remove** and do a search for **pidgin**. Should be there. Tick box and **'Apply'**.

(Partyboi - does 6.06 not have the things you suggest to install which need to be there to run pidgin?)

---

### Post by Dy-J_athan on 2008-09-04
I only have 6.06 here. which my friend gave me to try and spin it.

---

### Post by Dy-J_athan on 2008-09-04
I got the installer from a friend. He has Ubuntu 6.06. Do I need to uninstall the GAIM before installing pidgin??  :confused:

---

### Post by Bucky Ball on 2008-09-04
Cool. :) You will find pidgin in Add/Remove. You may already have it installed, just not ticked in the main menu.

**System->Preferences->Main menu->Internet **and see if it is in the column on the right, just not ticked. :)

---

### Post by Dy-J_athan on 2008-09-04
ok have installed it now. I have pidgin but there is no smiley on it. how do I install smiley and pidgin-music tracker:confused:

---

### Post by pmlxuser on 2008-09-04
you can download or request a more recent version like 7.10 or 8.04

---

### Post by Bucky Ball on 2008-09-04
Sorry, don't use it myself. Any ideas Partyboi? It might be a setting in preferences in the program itself of you may need to update the package or you may need to install the dependencies mentioned earlier by Partyboi (although the program would probably be throwing an error if this was the case). Maybe in a terminal try:

sudo apt-get update

... and that should get you up to speed at least. :)

---

### Post by Partyboi2 on 2008-09-04
> **Bucky Ball said:**
> Just one question, how come you have 6.06 installed?

Pidgin comes with the Hardy 8.04 installation.

You could also just go** Applications->Add/Remove** and do a search for **pidgin**. Should be there. Tick box and **'Apply'**.

(Partyboi - does 6.06 not have the things you suggest to install which need to be there to run pidgin?)

Pidgin is only in the gusty, hardy and intrepid (development) repo's. So to install pidgin for 6.06 you are going to need those dependencies met before installing it.

---

### Post by Dy-J_athan on 2008-09-04
got all the dependencies that is need. have installed pidgin 2.5.1. Is there a plugin that I can download for pidgin music tracker that runs in 6.06
a link maybe. thanks [-o<

---

### Post by Partyboi2 on 2008-09-04
> **Dy-J_athan said:**
> ok have installed it now. I have pidgin but there is no smiley on it. how do I install smiley and pidgin-music tracker:confused:
You can add smiley themes by downloading them and drag and dropping the <theme>.tar.gz file  into Tools>Preferences>Smiley themes.
[[COLOR=Blue]Here[/COLOR]]("http://www.gnome-look.org/content/search.php") is a link to some you can download to install. 

Not sure about the pidgin-music tracker.

Edit: You could try downloading the hardy deb version from [[COLOR=Blue]here[/COLOR]]("http://linux.softpedia.com/progDownload/pidgin-musictracker-Download-40878.html"). But I am not sure if you will be able to successfully met all the dependencies. If not you might need to download and compile the source.

---

### Post by Dy-J_athan on 2008-09-04
k thanks update you when I got it :)

---

### Post by ronnielsen1 on 2008-09-04
> I got the installer from a friend. He has Ubuntu 6.06.
I personally recommend you install Ubuntu 8.04. There is alot of difference  between the two versions. You can get it from the below link or maybe someone can explain how to upgrade.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Dojan5 on 2008-09-04
> **Dy-J_athan said:**
> I got the installer from a friend. He has Ubuntu 6.06. Do I need to uninstall the GAIM before installing pidgin??  :confused:

GAIM was Pidgin, they discontinued it since copyright issues I think.

---

### Post by Partyboi2 on 2008-09-04
If you do decide to upgrade to hardy you can do a network upgrade by following [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS")

---

### Post by Bucky Ball on 2008-09-04
Trouble is, the network upgrade takes forever and a day. Downloading  iso *much* quicker (torrent version fastest and most reliable - [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/) and look for the appropriate flavour that ends in 'iso.torrent').

---

