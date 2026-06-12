---
title: "Broken Apt"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by megadodo on 2006-05-30
First the problem, secondly how i think it came about

1. If i try to install/upgrade anything, I get the following error message from apt-get install/updrade:
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  kubuntu-desktop
The following packages will be upgraded:
  acpid alsa-utils app-install-data example-content gtk2-engines-gtk-qt
  kde-guidance kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  language-pack-en language-pack-en-base language-pack-kde-en
  language-pack-kde-en-base language-support-en libkpathsea4 libscim8c2a
  libscrollkeeper0 linux-restricted-modules-2.6.15-23-386
  linux-restricted-modules-common ntpdate nvidia-glx openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us
  openoffice.org-math openoffice.org-writer python-pgsql python-uno
  python2.4-pgsql scrollkeeper shared-mime-info tetex-bin ttf-opensymbol
  ubuntu-minimal ubuntu-standard wine x-window-system-core x11-common
  xbase-clients xlibs-dev xserver-xorg xserver-xorg-driver-all
  xserver-xorg-input-all xutils
51 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/134MB of archives.
After unpacking 3506kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a6.06+20060529_all.deb (--unpack):
 files list file for package `kivio-data' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a6.06+20060529_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@RichLaptop:~$                                        
``` 
Anyone know how to fix this?

2. I have a feeling this is due to the fact I deleted (with rm) the contents of /var/cache/apt/archives while spring cleaning. I realise now that I was supposed to use apt-get clean, but had never even heard of this command at the time. The directory contained 3.1GB of debs! Thats half of my total disk space... Surely a distro like (k)ubuntu should autoclean this at boot, or with a cron job, or after installing packages. Half the disk space taken up with debs of already installed packages is ludicrous. 
But anyway, the result was that I foolishly deleted the contents of the directory by hand, and now apt is broken :(

Thanks in advance, and apologies for the mini rant!

Rich

---

### Post by jimbren on 2006-05-30
Have you tried using apt-get clean since manually deleting the files?  

I did something simliar while using Warty, and that took care of the problem for me.

---

### Post by megadodo on 2006-05-30
Hey thanks for the help, but unfortunately there is no change after running apt-get clean or apt-get autoclean.

As an experiment, I tried removing the problem file (language-pack-en_1%3a6.06+20060529_all.deb), and the next time I ran apt-get upgrade, It downloaded it again and came up with the same error message. Does this mean that its that specific deb it is downloading that has an error in it? If so, it may not be my problem but the repositrys.
Also, thats an incredibly wierd file name, is it correct?
Thanks in advance
Rich

---

### Post by megadodo on 2006-05-31
Anyone any ideas? I still havent got it to work, and its completely crippling my system, as i cant install/uninstall anything. Is there a way to "reinstall" apt?
Surely I dont have to reinstall Dapper again?
Rich, and sorry for the bumping but im getting desperate!

---

### Post by metoo on 2006-06-01
Solved?

It seems that this language-pack package is broken.

You have 2 options here. Before you proceed do a 'apt-get update' to get the latest packages. If you are lucky this is already fixed.

1) Use 'sudo apt-get install *package*' to update as many packages as possible which do not depend on the language package.
E.g. 'sudo apt-get install openoffice.org' should be able to install all the openoffice stuff.
This way you are making the list of not upgradable package smaller until you reach a point when the rest is depending on the broken package. You have to wait until it is fixed.

If you use 'sudo synaptic', you can do this graphically with point and click. ('apt-get install synaptic' if it is not installed already).
Do not select all upgradable packages at once. Just a few and use several iterations until there is a no go because of the broken package.

2) Try to change the sources in /etc/apt/sources.list
could be, that your mirror has a broken package (unlikely though).

In any case, deleting anything in the apt cache will not screw up your system. Re-install is not required - this is Linux.

---

### Post by roccofoti on 2006-06-01
[QUOTE=megadodo]Anyone any ideas? I still havent got it to work, and its completely crippling my system, as i cant install/uninstall anything. Is there a way to "reinstall" apt?
Surely I dont have to reinstall Dapper again?
Rich, and sorry for the bumping but im getting desperate![/QUOTE]

Hi megadodo!

I had your same problem. Your problem is related with the file kivio-data*.deb. try to delete it and let me know if you solved

Ciao
Rocco

---

### Post by megadodo on 2006-06-01
Many thanks for the replies.

having tried the suggestions and im not sure it is the language pack that is broken. I do not have the kivio-data deb in the cache so I dont think its the actual deb that is causing the problem. 
I ran "sudo apt-get install openoffice.org" and got the same error but reffering to a different package:
```
root@RichLaptop:/var/cache/apt/archives# apt-get install openoffice.org
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  openoffice.org-help menu oooqs-kde unixodbc prelink openoffice.org-hyphenation openoffice.org-thesaurus msttcorefonts
  openoffice.org-gnome xlibmesa-gl libgl1 openoffice.org-officebean openclipart-openoffice.org pstoedit
  openoffice.org-filter-so52
The following packages will be upgraded:
  openoffice.org
1 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.
Need to get 0B/1956B of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/openoffice.org_2.0.2-2ubuntu12_i386.deb (--unpack):
 files list file for package `kivio-data' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org_2.0.2-2ubuntu12_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@RichLaptop:/var/cache/apt/archives#
```

Openoffice has nothing to do with kivio or the language-en thing and yet it still gives the same error. Any other program I try to install gives a similar error.

Rich

---

### Post by megadodo on 2006-06-02
OK progress has been made. I found the file "/var/lib/dpkg/info/kivio-data.list" which appears to be the "files list file" reffered to in the error. This file is corrupt, and after a few lines consists of "binary crap" ie just random stuff like you get if you open a binary file in a text editor. 
Therefore, could someone be kind enough to post their /var/lib/dpkg/info/kivio-data.list file? Or let me know where I can obtain a complete version of it?
Thanks
Rich

---

### Post by megadodo on 2006-06-02
Ok i removed the kivio-data.list file, then uninstalled kivio-data (which didnt actually do anything as it said there were no files) then reinstalled kivio-data, so it put a new kivio-data.list file in and now all is well.

Richard.

---

### Post by ubuntu_demon on 2006-06-02
here's some information :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

