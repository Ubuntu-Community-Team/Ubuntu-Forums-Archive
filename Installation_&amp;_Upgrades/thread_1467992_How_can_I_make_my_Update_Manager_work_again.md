---
title: "How can I make my Update Manager work again?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Indian Art on 2010-05-01
How can I make my Update Manager work again?

Here is the background:

Update Manager shows 121 updates (which include important security upgrades, Recommended Updates & other Updates which include Google Chrome and PlayOnLinux)

However, on clicking 'Install Updates', feeding the password and clicking 'Apply', Update Manager falsely states "Changes Applied
Update is Complete"

It further states "Not all Updates succeeded. For further details of failure, please expand the 'Details' panel below."

That details panel states, “Extracting packages from templates :100%”
“[B]Preconfiguring Packages …
(Reading database … 5% dpkg: unrecoverable fatal error, aborting :
files list file for package 'foomatic-gui is missing final newline
E: Sub-process / usr/bin/dpkg returned an error code (2)
 A package failed to install. Trying to recover: [/B] ”

Please help.

What should I do to resolve this? :KS

---

### Post by Indian Art on 2010-05-01
I opened a terminal and typed in this line: 
 
sudo apt-get update && sudo apt-get upgrade 
 
I got the following error in the process: 
 
sp@sp-desktop:~$ sudo apt-get update && sudo apt-get upgrade 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B] 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US  
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]  
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic Release.gpg 
Ign [http://ftp.usf.edu](http://ftp.usf.edu) karmic/main Translation-en_US 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [929B] 
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg 
Ign [http://ftp.usf.edu](http://ftp.usf.edu) karmic/universe Translation-en_US 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates Release.gpg 
Ign [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates/main Translation-en_US 
Ign [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates/universe Translation-en_US 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security Release.gpg 
Ign [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security/main Translation-en_US 
Ign [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security/universe Translation-en_US 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic Release 
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_US 
Get:4 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B] 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates Release 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security Release 
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic/main Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic/main Sources 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic/universe Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic/universe Sources 
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates/main Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates/main Sources 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates/universe Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-updates/universe Sources 
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security/main Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security/main Sources 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security/universe Packages 
Hit [http://ftp.usf.edu](http://ftp.usf.edu) karmic-security/universe Sources 
Fetched 3,659B in 2s (1,441B/s) 
Reading package lists... Done 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
The following packages have been kept back: 
 linux-generic linux-headers-generic linux-image-generic 
The following packages will be upgraded: 
 aisleriot app-install-data-commercial app-install-data-partner compiz 
 compiz-core compiz-gnome compiz-plugins compiz-wrapper cups cups-bsd 
  cups-client cups-common cups-ppdc cupsddk cupsys cupsys-bsd cupsys-client 
 cupsys-common devicekit-disks dpkg dpkg-dev erlang-base erlang-crypto 
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl 
 erlang-syntax-tools erlang-xmerl firefox firefox-3.0-branding 
  firefox-3.1-dbg firefox-3.1-gnome-support firefox-3.5 firefox-3.5-branding 
  firefox-3.5-dbg firefox-3.5-gnome-support foomatic-filters gcalctool glchess 
 glines gnect gnibbles gnobots2 gnome-blackjack gnome-games 
  gnome-games-common gnome-mahjongg gnome-screensaver gnome-sudoku gnometris 
  gnomine gnotravex gnotski google-chrome-unstable gstreamer0.10-plugins-bad 
 gtali iagno icedtea-6-jre-cacao icedtea6-plugin ifupdown 
 kdebase-workspace-bin kdebase-workspace-data 
  kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 landscape-common 
  libaudiofile0 libavcodec52 libavformat52 libavutil49 libcups2 libcupscgi1 
 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0 
 libdvdnav4 libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 
  libnss3-1d libnss3-1d-dbg libnss3-dev libpng12-0 libpng12-dev libpostproc51 
 libpq5 libpurple-bin libpurple0 libsmbclient libswscale0 libwbclient0 
 linux-firmware linux-libc-dev obexd-client openjdk-6-jre 
 openjdk-6-jre-headless openjdk-6-jre-lib pidgin pidgin-data 
 plasma-dataengines-workspace plasma-widgets-workspace playonlinux 
 samba-common samba-common-bin same-gnome smbclient sudo ttf-opensymbol 
  tzdata tzdata-java uno-libs3 ure winbind xserver-common xserver-xorg-core 
 xulrunner-1.9.1 xulrunner-1.9.1-gnome-support 
121 upgraded, 0 newly installed, 0 to remove and 3 not upgraded. 
Need to get 0B/163MB of archives. 
After this operation, 16.2MB of additional disk space will be used. 
Do you want to continue [Y/n]? Y 
WARNING: The following packages cannot be authenticated! 
 playonlinux 
Install these packages without verification [y/N]? y 
Extracting templates from packages: 100% 
Preconfiguring packages ... 
(Reading database ... [B]5%dpkg: unrecoverable fatal error, aborting: 
files list file for package 'foomatic-gui' is missing final newline [/B]
E: Sub-process /usr/bin/dpkg returned an error code (2) 
sp@sp-desktop:~$

---

### Post by Indian Art on 2010-05-01
I tried to remove the foomatic package, and then installing again ( **sudo apt-get remove foomatic-gui** & then **sudo apt-get install foomatic-gui** ) 
 
However, that too did not work (the error message can be posted on request).

Please help.

---

### Post by Indian Art on 2010-05-01
[B][COLOR="Red"]Will this help:

sudo gedit /var/lib/dpkg/statoverride

delete the postfix line[/COLOR][/B]

???!? :confused:

---

### Post by Indian Art on 2010-05-01
> **Indian Art said:**
> [B][COLOR="Red"]Will this help:

sudo gedit /var/lib/dpkg/statoverride

delete the postfix line[/COLOR][/B]

???!? :confused:

Here is what I got from the Terminal:

root postdrop 02555 /usr/sbin/postqueue
hplip root 755 /var/run/hplip
root mlocate 2755 /usr/bin/mlocate
postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop

I don't know which line to delete, that is if I need to delete a line

---

### Post by Indian Art on 2010-05-02
The problem was solved by copying the good (not corrupted) file from my Laptop PC (also running Ubuntu and dual booted) and using the terminal to paste it over the corrupted file of the problematic Desktop PC. I used a pen-drive and then the terminal For instance, sudo mv /home/sp/Music/system-tools-backends.list /var/lib/dpkg/info/system-tools-backends.list ). Good thing the update manager pointed out the offending agents (corrupt files). They were all ".lists" of some kind. 
:D
Thanks everyone.
:)

---

