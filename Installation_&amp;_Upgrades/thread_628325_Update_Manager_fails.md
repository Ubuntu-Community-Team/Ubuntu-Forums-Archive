---
title: "Update Manager fails"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by newlinuxuser07 on 2007-12-01
I'm an old Windows pro and just took the plunge into the Linux world by installing Ubuntu 7.10.
I loved how it installed, with complete drive reformat (killing the old Window partition that was there) in 20 minutes!
The speed of the OS just blows me away thus far.
So, I went to the Update Manager to install updates.
There was 93 updates pending.
I hit update and 3 installed before it blew up.
With 90 updates left, I tried again, but got the same error.
I then tried to install some packages individually, but I keep getting the same error.
I rebooted (Windows habit) and still no go.
The error is pretty cryptic.
Here's what I get:

Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tzdata (2007h-0ubunut0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10

Sorry if something isn't quite right in the above text.
Since I could select, but not copy the error text, I had to manually type it word for word and I might have miss spelled something.
Anyway, I really want to get going with Ubuntu, so can someone help me work through this?

---

### Post by douglasheld on 2007-12-02
Hello,

I think it looks like there is a problem with the time zone data package update.  I recommend you uncheck the 'tzdata' package in the list, and try to update everything else.

I hope that works!

Doug

---

### Post by kevinatkins on 2007-12-02
Hi,

Updates do, very occasionally, go slightly wrong, but it should be possible to fix this. We're probably going to need to attack this from the command line, so the first thing to do is fire up a terminal window (Accessories -> Terminal)

In there, type:

sudo apt-get update

When prompted, type in your password (there will be no on-screen feedback as you type your password, just type it and press return). This will ensure that your repositories are up-to-date - you should see a lot of messages on-screen and after processing all the repositories, there shouldn't be any errors. 

After that, type:

sudo apt-get upgrade

Now this bit may fail - if it does, please post back any messages that appear, particularly any pertaining to running apt-get again with other options.

---

### Post by xeth_delta on 2007-12-02
also from the terminal, try typing:
```
sudo apt-get update
sudo apt-get install -f
```

Xeth

---

### Post by daengbo on 2007-12-02
newlinuxuser07,

It sound like you may have a corrupted package. The download may have gone wrong. Remove the tzdata package from /var/cache/apt/archives/ and try again.

---

### Post by xeth_delta on 2007-12-02
> **daengbo said:**
> newlinuxuser07,

It sound like you may have a corrupted package. The download may have gone wrong. Remove the tzdata package from /var/cache/apt/archives/ and try again.

daengbo is right, that could be a reason. Go to a terminal and clean the downloaded packages from the apt cache:
```
sudo apt-get clean
sudo apt-get autoclean
```

Xeth

---

### Post by newlinuxuser07 on 2007-12-03
Thanks everybody for the advice.
I'll try your instructions out and let you know how it goes.  ;-)

---

### Post by newlinuxuser07 on 2007-12-03
Alas, the pesky Error 10 seems to be very stubborn.
Here's my log from a couple of options I tried, including just installing Wine by itself.
It doesn't make sense since I installed directly from the 7.10 disk.
Am I going to have to reinstall again?

Anyway, here's the log:

user@ubuntu:~$ sudo apt-get update
[sudo] password for user:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [81.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [24.0kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [28.7kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources [6019B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [5217B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources [833B]
Fetched 210kB in 2s (102kB/s)   
Reading package lists... Done
user@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apturl bittorrent capplets-data compiz compiz-core compiz-gnome
  compiz-plugins cupsys cupsys-bsd cupsys-client cupsys-common eog evince
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins file-roller firefox
  firefox-gnome-support gcalctool gdm gedit gedit-common ghostscript
  ghostscript-x gnome-about gnome-cards-data gnome-control-center
  gnome-desktop-data gnome-games gnome-games-data gnome-menus gnome-panel
  gnome-panel-data gnome-screensaver gnome-session gnome-system-monitor
  gnome-system-tools gtk2-engines gtkhtml3.14 hwdb-client-common
  hwdb-client-gnome language-pack-en language-pack-gnome-en libcamel1.2-10
  libcupsimage2 libcupsys2 libdecoration0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libflac8
  libgnome-desktop-2 libgnome-menu2 libgnome-window-settings1 libgnomeui-0
  libgnomeui-common libgs8 libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpcre3 libpcrecpp0 libpng12-0 libpoppler-glib2
  libpoppler2 libpurple0 libsmbclient libssl0.9.8 libwnck-common libwnck22
  linux-restricted-modules-2.6.22-14-generic linux-restricted-modules-common
  openssl pidgin pidgin-data poppler-utils python-bittorrent python-gmenu
  samba-common smbclient sound-juicer ubufox
93 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1550kB/103MB of archives.
After unpacking 8446kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-en 1:7.10+20071120 [1082kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-gnome-en 1:7.10+20071120 [428kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main apturl 0.1ubuntu2 [6822B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ubufox 0.4~beta1-0ubuntu6 [32.6kB]
Fetched 1550kB in 5s (284kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 93 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ sudo apt-get clean
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ dpkg --configure-a
dpkg: unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
user@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
user@ubuntu:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--10:40:54--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

10:40:55 (14.71 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

user@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US        
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release [1005B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources [904B]                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Get:7 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages [1139B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3242B in 1s (2739B/s)
Reading package lists... Done
user@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support libaudio2
Suggested packages:
  nas msttcorefonts
The following NEW packages will be installed:
  binfmt-support libaudio2 wine
0 upgraded, 3 newly installed, 0 to remove and 93 not upgraded.
1 not fully installed or removed.
Need to get 11.1MB of archives.
After unpacking 51.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe binfmt-support 1.2.10 [21.4kB]
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main wine 0.9.50~winehq0~ubuntu~7.10-1 [11.0MB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libaudio2 1.9-2 [77.5kB]
Fetched 11.1MB in 1m48s (102kB/s)                                              
Setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kevinatkins on 2007-12-03
Hi,

OK, looking like a more stubborn problem. I've done a bit of Googling, and it's possible this might be a bug in the tzdata package. Apparently, if you temporarily set your timezone to London (System -> Administration - > Time and Date) then try updating again it should work...

Not really a very good introduction to Ubuntu for you, I know... Anyway, if you could give that a try and post back..

---

### Post by newlinuxuser07 on 2007-12-03
BINGO!!!

Wow, that worked like a charm.  I set my time zone to London and restarted the updates and tada!  It worked!
Yeah, it's been a little frustrating, I must admit.
I'm just glad everyone ignored my little tirade and kept on trying to help met get this going.

THANK YOU so much for your help on this!

---

### Post by kevinatkins on 2007-12-04
Excellent! So glad you've got it sorted. Like I said, it's not really the best introduction to Ubuntu for you - I upgraded to 7.10 from 7.04 a few weeks ago, and I've got to say, there do seem to be a few bugs. No doubt matters will improve, but it has been slightly disappointing - 7.04 was very good indeed. 6.6 was another great release...

---

