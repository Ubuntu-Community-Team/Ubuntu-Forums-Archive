---
title: "frustrating &quot;partial upgrade&quot;"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by TheBuzzSaw on 2008-05-30
I am running Ubuntu 8.04 AMD64. When I go to update my system, it requests a partial upgrade first. I've done these before, and they usually execute just fine. However, today:

[img]http://img61.imageshack.us/img61/542/screenshotupdatemanagerim6.png[/img]

It's been this way all day. Help...?

---

### Post by tamoneya on 2008-05-30
do it to in terminal and we may get something more descriptive.  The commands are:```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by TheBuzzSaw on 2008-05-31
It just happened on my laptop too. Here is the terminal from my 32-bit Ubuntu 8.04 on my laptop:

```

buzz@buzz-laptop:~$ sudo apt-get update
[sudo] password for buzz: 
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Hit http://archive.canonical.com hardy/partner Packages              
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-proposed Release.gpg
Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US
Hit http://archive.canonical.com hardy/partner Sources
Hit http://security.ubuntu.com hardy-security/main Packages
Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://us.archive.ubuntu.com hardy-proposed Release             
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://us.archive.ubuntu.com hardy-proposed/main Packages
Hit http://us.archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-proposed/universe Packages
Reading package lists... Done
buzz@buzz-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-human
  openoffice.org-writer python-uno
The following packages will be upgraded:
  ttf-opensymbol
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 330kB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy-proposed/main ttf-opensymbol 1:2.4.1~rc1-1ubuntu1 [330kB]
Fetched 330kB in 1s (229kB/s)          
(Reading database ... 126815 files and directories currently installed.)
Preparing to replace ttf-opensymbol 1:2.4.0-3ubuntu6 (using .../ttf-opensymbol_1%3a2.4.1~rc1-1ubuntu1_all.deb) ...
Unpacking replacement ttf-opensymbol ...
Setting up ttf-opensymbol (1:2.4.1~rc1-1ubuntu1) ...
Updating fontconfig cache...

```

---

### Post by paulo_ on 2008-05-31
It's happening the same here...

The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-human
  openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

---

### Post by gashach on 2008-05-31
try :
sudo apt-get install openoffice.org

it will do the update.

---

### Post by stiffmaster on 2008-05-31
I understand that doing **sudo apt-get install openoffice.org** will do the update but it will uninstall some packages are those important? What are thos packages used for ?

```
$ sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openoffice.org-base openoffice.org-base-core openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-filter-binfilter
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-officebean openoffice.org-style-human
  openoffice.org-writer python-uno
Suggested packages:
  graphicsmagick-imagemagick-compat imagemagick hunspell-dictionary menu
  openclipart-openoffice.org pstoedit libmyodbc odbc-postgresql libsqliteodbc
  tdsodbc mdbtools libmysql-java libpg-java openoffice.org-gcj
  openoffice.org-report-builder openoffice.org-style-hicontrast
  openoffice.org-style-industrial
The following packages will be REMOVED:
  language-support-en language-support-fr language-support-translations-en
  language-support-translations-fr openoffice.org-help-en-gb
  openoffice.org-help-fr openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-l10n-fr thunderbird-locale-en-gb thunderbird-locale-fr
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-filter-binfilter
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-officebean openoffice.org-style-human
  openoffice.org-writer python-uno
17 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
Need to get 61.4MB of archives.
After this operation, 80.0MB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by housam on 2008-05-31
I think it is the proposed packages . read this [[COLOR="Red"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5086959")

---

### Post by tamoneya on 2008-05-31
the other option would be ```
sudo apt-get dist-upgrade
```

---

