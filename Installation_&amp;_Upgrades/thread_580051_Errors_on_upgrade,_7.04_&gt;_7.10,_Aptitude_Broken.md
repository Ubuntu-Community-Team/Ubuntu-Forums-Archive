---
title: "Errors on upgrade, 7.04 &gt; 7.10, Aptitude Broken?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by dinkins on 2007-10-18
I had errors while upgrading, mainly it said it could not install util-linux and many other packages (including language packs), stopped the install and sat there. Upon restart of my computer, all my program settings were at "default" (for example, pidgin had all default IM window settings reverted and audacious was on the default skin and had no playlist loaded).

When I run **sudo apt-get update** and then **sudo apt-get upgrade**, I see this:


> 
myles@myles-laptop:~$ sudo apt-get upgrade
[sudo] password for myles:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 sun-java6-jre
 sun-java6-bin
 util-linux-locales
 ubuntu-minimal
 sun-java6-plugin
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)


What is wrong? How can I fix this? These were all packages that were reported unable to install during the upgrade, also.

---

### Post by Whiffle on 2007-10-18
try

'apt-get -f install'

---

### Post by dinkins on 2007-10-18
Also on a related note: **sudo apt-get autoremove** is also borked :(

> myles@myles-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-compat-howl0 feisty-wallpapers libcairo-ruby libstlport5.1 libatk1-ruby
  libswfdec0.3 libsilc-1.0-2 libflac++5c2 liboggflac3 libtagc0 libglib2-ruby
  libpango1-ruby libgpod1 libavformat0d libgdk-pixbuf2-ruby librexml-ruby
  libxmlsec1-gnutls libslab0 libaudacious4 libnspr-dev liblzo-dev
  feisty-session-splashes libavcodec0d libgs-esp8 libgtk2-ruby libquicktime0 libntfs-3g0
  libgdiplus libberylsettings0-gconf
The following packages will be REMOVED:
  feisty-session-splashes feisty-wallpapers libatk1-ruby libaudacious4
  libavahi-compat-howl0 libavcodec0d libavformat0d libberylsettings0-gconf libcairo-ruby
  libflac++5c2 libgdiplus libgdk-pixbuf2-ruby libglib2-ruby libgpod1 libgs-esp8
  libgtk2-ruby liblzo-dev libnspr-dev libntfs-3g0 liboggflac3 libpango1-ruby
  libquicktime0 librexml-ruby libsilc-1.0-2 libslab0 libstlport5.1 libswfdec0.3 libtagc0
  libxmlsec1-gnutls
0 upgraded, 0 newly installed, 29 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 21.1MB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by dinkins on 2007-10-18
> **Whiffle said:**
> try

'apt-get -f install'

Thank you for the quick reply. I tried it with -f install, and here are the error messages I receieve:


> myles@myles-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-compat-howl0 feisty-wallpapers libcairo-ruby libstlport5.1 libatk1-ruby
  libswfdec0.3 libsilc-1.0-2 libflac++5c2 liboggflac3 libtagc0 libglib2-ruby
  libpango1-ruby libgpod1 libavformat0d libgdk-pixbuf2-ruby librexml-ruby
  libxmlsec1-gnutls libslab0 libaudacious4 libnspr-dev liblzo-dev
  feisty-session-splashes libavcodec0d libgs-esp8 libgtk2-ruby libquicktime0 libntfs-3g0
  libgdiplus libberylsettings0-gconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 sun-java6-jre
 sun-java6-bin
 util-linux-locales
 ubuntu-minimal
 sun-java6-plugin
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)


No luck :(

---

### Post by bapoumba on 2007-10-18
Please try ```
sudo apt-get dist-upgrade
```

---

### Post by dinkins on 2007-10-18
> **bapoumba said:**
> Please try ```
sudo apt-get dist-upgrade
```

Thank you also for the quick reply. However, much the same scenario as the other options. tzdata seems to be the culprit and is causing all these dependency problems, however nothing seems to be able to fix it :(

> 
myles@myles-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 sun-java6-jre
 sun-java6-bin
 util-linux-locales
 ubuntu-minimal
 sun-java6-plugin
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)


tzdata why are you doing this to me :frown:

---

### Post by bapoumba on 2007-10-18
Okay, let's have a look at your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by dinkins on 2007-10-18
> **bapoumba said:**
> Okay, let's have a look at your sources.list:
```
cat /etc/apt/sources.list
```

> myles@myles-laptop:~$ cat /etc/apt/sources.list


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

# deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
#AUTOMATIX REPOS END
# deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
# deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy


It seems after my partial upgrade, all former 3rd party and old sources were automatically commented out.

I looked up tzdata in Synaptic Package Manager and it appears it is installed, abeit perhapse an old version. After selecting "completely remove package", (to reinstall again fresh) I am prompted with this:

[img]http://www.nubkuh.org/summary.png[/img]

Would completely removing the broken old package and reinstalling it through an apt-get upgrade possibly resolve this? Or would removing these (older) packages break and cripple my system further?

---

### Post by bapoumba on 2007-10-18
What is the output to 
```
sudo dpkg-reconfigure tzdata
```

---

### Post by dinkins on 2007-10-18
It appears I'm making some progress. After completely removing the named broken package, **tzdata**, I was greeted with this little guy:

[img]http://www.nubkuh.org/Screenshot-UpdateManager.png[/img]

It upgraded, although I may have seen a small error or two in the terminal below the GUI install.

I moved back to the terminal window, and proceeded to hit **sudo apt-get autoremove** to kill all old and possibly broken packages.

> myles@myles-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-compat-howl0 feisty-wallpapers libcairo-ruby libstlport5.1 libatk1-ruby
  libswfdec0.3 libsilc-1.0-2 libflac++5c2 liboggflac3 libtagc0 sysutils libglib2-ruby
  java-common liblog4j1.2-java libpango1-ruby procinfo libgpod1 tofrodos libavformat0d
  unixodbc libgdk-pixbuf2-ruby librexml-ruby libxmlsec1-gnutls libslab0 odbcinst1debian1
  libaudacious4 libnspr-dev liblzo-dev feisty-session-splashes memtester libavcodec0d
  libgs-esp8 libgtk2-ruby libquicktime0 libntfs-3g0 libgdiplus libberylsettings0-gconf
The following packages will be REMOVED:
  feisty-session-splashes feisty-wallpapers java-common libatk1-ruby libaudacious4
  libavahi-compat-howl0 libavcodec0d libavformat0d libberylsettings0-gconf libcairo-ruby
  libflac++5c2 libgdiplus libgdk-pixbuf2-ruby libglib2-ruby libgpod1 libgs-esp8
  libgtk2-ruby liblog4j1.2-java liblzo-dev libnspr-dev libntfs-3g0 liboggflac3
  libpango1-ruby libquicktime0 librexml-ruby libsilc-1.0-2 libslab0 libstlport5.1
  libswfdec0.3 libtagc0 libxmlsec1-gnutls memtester odbcinst1debian1 procinfo sysutils
  tofrodos unixodbc
0 upgraded, 0 newly installed, 37 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 23.2MB disk space will be freed.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 146402 files and directories currently installed.)
Removing feisty-session-splashes ...
Removing feisty-wallpapers ...
Removing liblog4j1.2-java ...
Removing java-common ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Removing libatk1-ruby ...
Removing libaudacious4 ...
Removing libavahi-compat-howl0 ...
Removing libavformat0d ...
Removing libavcodec0d ...
Removing libberylsettings0-gconf ...
Removing libcairo-ruby ...
Removing libflac++5c2 ...
Removing libgdiplus ...
Removing libgdk-pixbuf2-ruby ...
Removing libglib2-ruby ...
Removing libgpod1 ...
Removing libgs-esp8 ...
Removing libgtk2-ruby ...
Removing liblzo-dev ...
Removing libnspr-dev ...
Removing libntfs-3g0 ...
Removing liboggflac3 ...
Removing libpango1-ruby ...
Removing libquicktime0 ...
Removing librexml-ruby ...
Removing libsilc-1.0-2 ...
Removing libslab0 ...
Removing libstlport5.1 ...
Removing libswfdec0.3 ...
Removing libtagc0 ...
Removing libxmlsec1-gnutls ...
Removing sysutils ...
Removing memtester ...
Removing unixodbc ...
Removing odbcinst1debian1 ...
Removing procinfo ...
Removing tofrodos ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


YAY! It appears to be working, although somewhat error-ridden. 



Following this, I just now went back to install some (appearingly) necessary packages, such as language-pack-en. 

> myles@myles-laptop:~$ sudo apt-get install language-pack-en
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  language-pack-en-base locales
The following NEW packages will be installed:
  language-pack-en language-pack-en-base locales
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6350kB of archives.
After unpacking 22.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package locales.
(Reading database ... 145664 files and directories currently installed.)
Unpacking locales (from .../locales_2.6.1-1_all.deb) ...
Selecting previously deselected package language-pack-en-base.
Unpacking language-pack-en-base (from .../language-pack-en-base_1%3a7.10+20071012_all.deb) ...
Selecting previously deselected package language-pack-en.
Unpacking language-pack-en (from .../language-pack-en_1%3a7.10+20071012_all.deb) ...
Setting up locales (2.6.1-1) ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

Setting up language-pack-en (1:7.10+20071012) ...
Setting up language-pack-en-base (1:7.10+20071012) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
 * Reloading GNOME Display Manager configuration...                                        * Changes will take effect when all current X sessions have ended.
                                                                                   [ OK ]

I'm not sure if language-pack-en is absolutely needed, but I figured I'd not try to risk it on my next reboot of X. I will reinstall all packages removed during my **tzdata** complete removal, just to be on the safe side, then run **sudo apt-get update** and following **sudo apt-get upgrade**. It seems this issue could be possibly resolved.

---

### Post by bapoumba on 2007-10-18
if you are using GNOME, please install **ubuntu-desktop**.

---

### Post by dinkins on 2007-10-18
Thankfully, ubuntu-desktop is still there :D

> myles@myles-laptop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Is there any consensis as to why I would lose all my settings defaults in programs such as pidgin and audacious? It isn't a huge deal or anything, but was that related to my util-linux packages or locales packages messing up before?

---

### Post by bapoumba on 2007-10-18
You should not. The config files are in your /home (at least for pidgin, I guess too for audacious).

---

### Post by luminair on 2007-10-18
Other people getting errors with the gui method: [https://bugs.launchpad.net/bugs/153980](https://bugs.launchpad.net/bugs/153980)

---

