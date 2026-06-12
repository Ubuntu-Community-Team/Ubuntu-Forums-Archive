---
title: "partial upgrade problem"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by a.kazemi on 2012-11-21
hi everybody
does anyone know in ubuntu 12.04 x64 bit what does this repository do "http://ubuntu.mirror.cambrium.nl/ubuntu/" exactly?
when I unchecked it in the software sources second tab I wouldn't get the partial upgrade error also can update packages as usual but cannot install some packages! for example the ia32-libs which is required for some softwares like teamviewer or skype and when I checked it I get partial upgrade error and cannot update system as usual because it corrupts my other packages...

I am totally confused please somebody give me a solution!:confused::confused::confused::confused::confused::confused::confused:

---

### Post by Bashing-om on 2012-11-21
That is a repository for all your updates, as such needed! ( or another mirror site)

May I suggest that you re enable the site and post the results of terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```
so we can see the errors generated and begin a process to a solution.

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by a.kazemi on 2012-11-22
here it is:
```
hpc@ubuntu:~$ sudo apt-get update
Ign [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                            
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release   
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/main amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/universe amd64 Packages 
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/main i386 Packages      
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/universe i386 Packages  
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/main TranslationIndex   
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg           
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/main Translation-en     
Hit [http://ubuntu.mirror.cambrium.nl](http://ubuntu.mirror.cambrium.nl) quantal/universe Translation-en 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done

```
and

```
hpc@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libglapi-mesa:i386 but it is not installed
                            Recommends: libgl1-mesa-glx:i386 but it is not installed
                            Recommends: libgl1-mesa-dri:i386 but it is not installed
 libglu1-mesa:i386 : Depends: libgl1-mesa-glx:i386 but it is not installed or
                              libgl1:i386
 libqt4-opengl:i386 : Depends: libgl1-mesa-glx:i386 but it is not installed or
                               libgl1:i386
 libvisual-0.4-plugins:i386 : Depends: libgl1-mesa-glx:i386 but it is not installed or
                                       libgl1:i386
E: Unmet dependencies. Try using -f.

```
and if you want to see the result of > apt-get -f install after those commands, it is here:

```
hpc@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libkdc2-heimdal virtuoso-minimal libkonq5-templates libqca2 bind9
  libqt4-qt3support libkxmlrpcclient4 cdparanoia libunistring0
  libpolkit-qt-1-1 libk3b6 libknewstuff3-4 libqapt-runtime libvirtodbc0
  libnepomuksync4 libhdb9-heimdal libkdeclarative5 libnepomukquery4a
  bind9utils nepomuk-core-data libqt4-designer libkonq-common libthreadweaver4
  libkdecore5 phonon libnepomukutils4 libktexteditor4 libkmediaplayer4
  oxygen-icon-theme plasma-scriptengine-javascript libkrosscore4
  calligra-l10n-engb po-debconf libflac++6 kdevelop-l10n libapt-inst1.5
  libkcddb4 libkactivities-bin intltool-debian virtuoso-opensource-6.1-bin
  python-talloc libndr-standard0 tdb-tools libsolid4 python-ldb
  libdlrestrictions1 k3b-data libnepomuk4 libsoprano4 python-dnspython
  ldb-tools libattica0.4 virtuoso-opensource-6.1-common gettext libkdnssd4
  libkparts4 libmp3lame0 kde-runtime-data libclucene0ldbl libqapt1 python-tdb
  attr shared-desktop-ontologies kdoctools libkactivities6 libmikmod2 icoutils
  libtevent0 libkidletime4 katepart kdevelop-php-l10n libao4 libkcmutils4
  libntrack0 soprano-daemon libkfile4 libkpty4 libdvdnav4 kde-l10n-engb
  libphonon4 libdvdread4 libgettextpo0 libkntlm4 libsamba-util0 libplasma3
  phonon-backend-gstreamer libkemoticons4 libnepomukcore4abi1 libexiv2-12
  ntrack-module-libnl-0 kdelibs-bin libkdewebkit5 libldb1 libkjsembed4 libmad0
  nepomuk-core libkio5 libkjsapi4 libstreams0 libid3tag0 libntrack-qt4-1
  kdelibs5-data libmusicbrainz5-0 libqtwebkit4 libmail-sendmail-perl
  libkde3support4 libknotifyconfig4 libndr0 kdelibs5-plugins
  libsys-hostname-long-perl libkhtml5 libmpcdec6 libkdeui5 libkdesu5
  libkatepartinterfaces4 kdevelop-php-docs-l10n kate-data libmms0
  libstreamanalyzer0 libkonq5abi1 libfaad2 libaudiofile1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
Suggested packages:
  libglide3:i386
The following NEW packages will be installed:
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
0 upgraded, 7 newly installed, 0 to remove and 1221 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,247 kB of archives.
After this operation, 35.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 335419 files and directories currently installed.)
Unpacking libglapi-mesa:i386 (from .../libglapi-mesa_9.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libglapi-mesa_9.0-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libglapi-mesa/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Unpacking libdrm2:i386 (from .../libdrm2_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libdrm2/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              Unpacking libdrm-radeon1:i386 (from .../libdrm-radeon1_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-radeon1_2.4.39-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libdrm-radeon1/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              Unpacking libdrm-intel1:i386 (from .../libdrm-intel1_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-intel1_2.4.39-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libdrm-intel1/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              Unpacking libdrm-nouveau2:i386 (from .../libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libdrm-nouveau2/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              Unpacking libgl1-mesa-dri:i386 (from .../libgl1-mesa-dri_9.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_9.0-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Unpacking libgl1-mesa-glx:i386 (from .../libgl1-mesa-glx_9.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_9.0-0ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libgl1-mesa-glx/changelog.Debian.gz' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libglapi-mesa_9.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_i386.deb
 /var/cache/apt/archives/libdrm-radeon1_2.4.39-0ubuntu1_i386.deb
 /var/cache/apt/archives/libdrm-intel1_2.4.39-0ubuntu1_i386.deb
 /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb
 /var/cache/apt/archives/libgl1-mesa-dri_9.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/libgl1-mesa-glx_9.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by NikTh on 2012-11-22
Hi .
somehow you've added quantal (Ubuntu 12.10) mirrors to your sources.list. 

Multiple problems can occure when you mix different versions of Ubuntu. 

I suggest to remove the quantal entries from sources.list . Open the file with gedit 

```
gksudo gedit /etc/apt/sources.list
```and comment out (place this symbol # at the start of each line) all the quantal entries. 

Then try again. 
```
sudo apt-get --purge autoremove
sudo apt-get update; sudo apt-get dist-upgrade
```If you put the results between [CODE] brackets are easiest to read than quote :) .[See here how]("http://i.stack.imgur.com/zADbK.png") 

Thanks

---

### Post by a.kazemi on 2012-11-22
> **NikTh said:**
> Hi .
somehow you've added quantal (Ubuntu 12.10) mirrors to your sources.list. 

Multiple problems can occure when you mix different versions of Ubuntu. 

I suggest to remove the quantal entries from sources.list . Open the file with gedit 

```
gksudo gedit /etc/apt/sources.list
```and comment out (place this symbol # at the start of each line) all the quantal entries. 

Then try again. 
```
sudo apt-get --purge autoremove
sudo apt-get update; sudo apt-get dist-upgrade
```If you put the results between [CODE] brackets are easiest to read than quote :) .[See here how]("http://i.stack.imgur.com/zADbK.png") 

Thanks

but exactly the problem is here! when I remove this mirror some packages cannot be installed such as teamviewer7 or skype !

---

### Post by a.kazemi on 2012-11-22
:confused:

---

### Post by hgergo on 2012-11-22
Hmm now a partial upgrade window popped up no checking what it is

L.E

skype-bin is held back??

---

### Post by a.kazemi on 2012-11-22
I done it one time and it upgraded my ubuntu 12.04 to 12.1 and then I have recovered it

I have never tried to install skype before this now when I want to do it, ia32-libs error stop it!

---

### Post by NikTh on 2012-11-22
Hi , 
for some weird reason (happened to me also) you have to install skype like this 
```
sudo apt-get install skype-bin
``` 

I guess it will be installed correctly. 
brief update: Skype now is 4.1 for Ubuntu 12.04 

As for teamviewer , I think you have to download the appropriate pacakge from the site. [Here](http://www.teamviewer.com/en/index.aspx)

Thanks

---

### Post by a.kazemi on 2012-11-26
I finally install whole Ubuntu again and now there is no problem but the issue hasn't been solved !

---

### Post by Chozabu on 2012-12-25
try removing all the files it complains about perhaps?
like './usr/share/doc/libdrm2/changelog.Debian.gz'

---

