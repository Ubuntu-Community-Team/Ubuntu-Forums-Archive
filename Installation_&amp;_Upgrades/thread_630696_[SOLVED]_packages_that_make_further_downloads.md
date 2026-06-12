---
title: "[SOLVED] packages that make further downloads"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by ruibernardo on 2007-12-03
Hi folks,

I'm trying to set up a website that allows people that don't have an internet connection to install packages in their offline Ubuntu. It's called [nonetdebs]("http://nonetdebs.homeip.net") and basically it's a chroot where the status file (/var/lib/dpkg/status - a file that have the info of all installed packages in the system) of the user is installed and where apt-get is executed. It solves the dependencies problems and saves people time of wondering around [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to download the packages (and their dependencies) they need from the repositories, listing the packages they don't have installed to install the ones they want.

An issue that's happening is that most of the users (offline users) are not used to the debian/ubuntu packaging system and most of them (still) don't understand it very well, which is only natural.

The real question is that some packages want to download other files from the internet. When you install that kind of packages in an offline Ubuntu, the dpkg/apt system fails the download and doesn't install them. To an offline user it is a nightmare, because that leaves broken packages.

I would like to have a list of packages on the website with the name of the packages that do does downloads, so when a user tries to download them, I can issue a warning about that package and, maybe, give him an alternative to install it (downloading it directly from sources, from the software website, etc).

In Gutsy, from my Desktop installation I can list the following packages:

**[SIZE=3]Don't Install the red ones[/SIZE]**:

**[COLOR=Red]ubuntu-restriced extras[/COLOR]**[INDENT]Installs gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse [COLOR=Red]msttcorefonts[/COLOR], [COLOR=Red]flashplugin-nonfree[/COLOR] [COLOR=Red]sun-java6-plugin[/COLOR] unrar gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg liblame0 [COLOR=Red]libdvdread3[/COLOR]

Package dependencies of ubuntu-restricted-extras you can safely install: [COLOR=SeaGreen]gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse unrar gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg liblame0[/COLOR]

Package dependencies of ubuntu-restricted-extras you shouldn't install (they make downloads): [COLOR=Red]msttcorefonts[/COLOR] [COLOR=Red]flashplugin-nonfree[/COLOR] [COLOR=Red]sun-java6-plugin[/COLOR] [COLOR=Red]libdvdread3[/COLOR]
[/INDENT][B][COLOR=Red]msttcorefonts
[/COLOR][/B][INDENT] To install msttcorefonts: [msttcorefonts on standalone machine]("http://ubuntuforums.org/showthread.php?t=203994");
[/INDENT][B][COLOR=Red]flashplugin-nonfree
[/COLOR][/B][INDENT]To install flashplugin-nonfree:  Ubuntugeek: Install Flash Player 9 in Ubuntu; option 2 - install the gnash package - opensource flash;
[/INDENT][B][COLOR=Red]sun-java6-plugin
[/COLOR][/B][INDENT] To install Java (JRE and JDK): [installing SUN's Java6 jdk without internet connection?]("http://ubuntuforums.org/showthread.php?t=459006")
[/INDENT][B][COLOR=Red]libdvdread3[/COLOR]
[/B][INDENT]To install libdvdread3: [COLOR=Red]*need help here...*[/COLOR][/INDENT]**Please help me**. This would help Ubuntu to be also a great offline OS.

TIA

EDIT1: added libdvdread and alternatives
EDIT2: added gnash as an alternative to adobe flash plugin

---

### Post by ruibernardo on 2007-12-06
Up up up :)

Added another one - libdvdread3.

**Please**, if you do know other packages that make downloads from the internet, post them. Thank you.

---

### Post by jenkinbr on 2007-12-21
Having difficulties with the alternate install method of msttcorefonts.

[http://ubuntuforums.org/showthread.php?p=3992124#post3992124](http://ubuntuforums.org/showthread.php?p=3992124#post3992124)

---

### Post by ruibernardo on 2008-03-15
Hi,

I've some news about those packages that you can't install offline. I've created some **dummy packages** to install [COLOR=Red]flashplugin-nonfree[/COLOR], [COLOR=Red]msttcorefonts[/COLOR], [COLOR=Red]libdvdread3[/COLOR] , and [COLOR=Red]sun-java6-plugin[/COLOR]. With them installed, you can install all the other packages that "[COLOR=Red]ubuntu-restricted-extras[/COLOR]" depends and "ubuntu-restricted-extras" itself. You can create dummy packages with the package "equivs".

The process:[INDENT]1 - **Download the** tar archive with the **dummy packages**:
```
wget [http://nonetdebs.unixpod.com/dummies/dummies_gutsy.tar.gz](http://nonetdebs.unixpod.com/dummies/dummies_gutsy.tar.gz)
```[/INDENT][INDENT]2 - **Download all the other packages** that "ubuntu-restricted-extras" depends from [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/) or from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).
[/INDENT][INDENT]3 - **On the offline computer extract** the dummies_gutsy.tar.gz file to a temporary directory **and install the dummy packages** now:
```
tar zxvf dummies_gutsy.tar.gz
dummies/
dummies/flashplugin-nonfree_9.0.115_all.deb
dummies/libdvdread3_0.9.7_all.deb
dummies/msttcorefonts_2.2_all.deb
dummies/sun-java6-plugin_6.03_all.deb
cd dummies/
sudo dpkg -i *.deb
```[/INDENT][INDENT]4 - Now **don't install the packages you downloaded** from the repositories. On the directory where you have them, c**hange their filename extension from** [COLOR=Black]**.deb**[/COLOR]** to [COLOR=Red].deb_not[/COLOR]**, so they don't get installed when we install them with "dpkg -i *.deb":
```
cd where_all_the_ubuntu_restricted_extras_packages_are/
mv flashplugin-nonfree*.deb flashplugin-nonfree*.deb_not
mv libdvdread3*.deb libdvdread3*.deb_not
mv msttcorefonts_2.2*.deb msttcorefonts_2.2*.deb_not
mv sun-java6-plugin_6*.deb sun-java6-plugin_6*.deb_not
```[/INDENT][INDENT]5 - Finally **install the remaining packages** from that directory:
```
sudo dpkg -i *.deb
sudo apt-get install -f
```[/INDENT]In the end you will have "ubuntu-restricted-extras" installed and all its dependencies met. The catch is that you will not have the content of the dummy packages installed. :)

To install the "missing" software you'll have to download the sources of those applications and install them outside the Debian package system. For APT they are already installed anyway. 

More info on "equivs" and the Debian policy: [http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-equivs](http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-equivs)

Just a last note. I've tried it myself on a fresh Gutsy install and it worked just fine. Didn't try in other releases.

---

### Post by gary4gar on 2008-03-30
> **epimeteo said:**
> Hi,

I've some news about those packages that you can't install offline. I've created some **dummy packages** to install [COLOR=Red]flashplugin-nonfree[/COLOR], [COLOR=Red]msttcorefonts[/COLOR], [COLOR=Red]libdvdread3[/COLOR] , and [COLOR=Red]sun-java6-plugin[/COLOR]. With them installed, you can install all the other packages that "[COLOR=Red]ubuntu-restricted-extras[/COLOR]" depends and "ubuntu-restricted-extras" itself. You can create dummy packages with the package "equivs".

The process:[INDENT]1 - **Download the** tar archive with the **dummy packages**:
```
wget [http://nonetdebs.unixpod.com/dummies/dummies_gutsy.tar.gz](http://nonetdebs.unixpod.com/dummies/dummies_gutsy.tar.gz)
```[/INDENT][INDENT]2 - **Download all the other packages** that "ubuntu-restricted-extras" depends from [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/) or from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).
[/INDENT][INDENT]3 - **On the offline computer extract** the dummies_gutsy.tar.gz file to a temporary directory **and install the dummy packages** now:
```
tar zxvf dummies_gutsy.tar.gz
dummies/
dummies/flashplugin-nonfree_9.0.115_all.deb
dummies/libdvdread3_0.9.7_all.deb
dummies/msttcorefonts_2.2_all.deb
dummies/sun-java6-plugin_6.03_all.deb
cd dummies/
sudo dpkg -i *.deb
```[/INDENT][INDENT]4 - Now **don't install the packages you downloaded** from the repositories. On the directory where you have them, c**hange their filename extension from** [COLOR=Black]**.deb**[/COLOR]** to [COLOR=Red].deb_not[/COLOR]**, so they don't get installed when we install them with "dpkg -i *.deb":
```
cd where_all_the_ubuntu_restricted_extras_packages_are/
mv flashplugin-nonfree*.deb flashplugin-nonfree*.deb_not
mv libdvdread3*.deb libdvdread3*.deb_not
mv msttcorefonts_2.2*.deb msttcorefonts_2.2*.deb_not
mv sun-java6-plugin_6*.deb sun-java6-plugin_6*.deb_not
```[/INDENT][INDENT]5 - Finally **install the remaining packages** from that directory:
```
sudo dpkg -i *.deb
sudo apt-get install -f
```[/INDENT]In the end you will have "ubuntu-restricted-extras" installed and all its dependencies met. The catch is that you will not have the content of the dummy packages installed. :)

To install the "missing" software you'll have to download the sources of those applications and install them outside the Debian package system. For APT they are already installed anyway. 

More info on "equivs" and the Debian policy: [http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-equivs](http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-equivs)

Just a last note. I've tried it myself on a fresh Gutsy install and it worked just fine. Didn't try in other releases.


Isn't there a easier way out,
Like Just One click Installs while watching your fav movie:popcorn:

---

### Post by ruibernardo on 2008-03-30
> **gary4gar said:**
> Isn't there a easier way out,
Like Just One click Installs while watching your fav movie:popcorn:

Yes, it's fun... when you're **online**.

This is for those who don't have an Internet connection while installing the "**ubuntu-restricted-extras**". It **will not install *offline***. 

The dummies are needed so all dependencies of "ubuntu-restricted-extras" are satisfied and if, later, the offline user wants to install some other package that needs to have java, or msttcorefonts or ubuntu-restricted-extras to be able to install another new package, he will have them "installed" in apt-get (dummy), but installed from sources in the reality.

It's a workaround to have ubuntu-restricted-extras installed offline.

Did you got ubuntu-restricted-extras installed offline without problems?

---

