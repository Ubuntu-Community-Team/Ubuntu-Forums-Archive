---
title: "Updating stopped midway.Im lost :)"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by novinthen on 2008-05-04
Well, when all the updates downloaded and it was installing itself , my pc shutdown itself half way...

When i tried re-updating it... I got this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What to do now... :(

---

### Post by Pumalite on 2008-05-04
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
Post the output.

---

### Post by yinglcs2 on 2008-05-04
Hi,

I am having the same problem. I am not sure what is the status of my upgrade:

I did follow the suggestion and here is the output.  i appreciate if someone can help me fixing my problem.



```

$ sudo dpkg --configure -a
[sudo] password for scheung: 
scheung:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lirc pwgen libwvstreams4.3-extras libgtkhtml3.8-15 libfaad2-0 libmtp6
  libmtp7 libneon26 libxine1-x libsnmp10 libnet-daemon-perl libgtk1.2 sqlite
  libfame-0.9 libmagick++9c2a libglew1.4 libzvbi0 libxcb-xv0 libdbi-perl
  libpvm3 libmp4v2-0 libpt-1.10.10-plugins-alsa libggzmod4 libsgutils1
  libgtkhtml3.16-cil libpt-1.10.10 libgpod2 libgpod3 libmpeg4ip-dev
  libsqlite0-dev libplrpc-perl libsvg1 libx264-54 setserial gutsy-wallpapers
  libmp4v2-dev libmikmod2 libflickrnet2.1.5-cil libggz2 libxcb-shape0
  libzvbi-common libmpeg4ip-0 libcrypto++6 libgtkhtml2.0-cil gnome-games-data
  transcode ntp libungif4-dev libgsl0 libopal-2.2 libwvstreams4.3-base
  libiso9660-4 libgpod-common xsane-common libmozjs0d libgtk1.2-common
  libdb4.5 libggzcore9 libtotem-plparser7 libuniconf4.3 sqlite3 v4l-conf
  libxcb-shm0 linux-source-2.6.22 libidn11-dev libntfs-3g12 librsvg2.0-cil
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scheung:~ $ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg                    
Ign http://security.ubuntu.com hardy-security/main Translation-en_US         
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US   
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release   
Hit http://security.ubuntu.com hardy-security/main Packages                  
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages             
Hit http://security.ubuntu.com hardy-security/main Sources                    
Hit http://security.ubuntu.com hardy-security/restricted Sources              
Hit http://security.ubuntu.com hardy-security/universe Sources                
Hit http://security.ubuntu.com hardy-security/multiverse Sources              
Hit http://us.archive.ubuntu.com hardy Release.gpg                            
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-backports Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Reading package lists... Done
scheung:~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-gnome2-extras xfonts-encodings
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/906kB of archives.
After this operation, 49.2kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 162086 files and directories currently installed.)
Preparing to replace python-gnome2-extras 2.19.1-0ubuntu4 (using .../python-gnome2-extras_2.19.1-0ubuntu7_i386.deb) ...
Unpacking replacement python-gnome2-extras ...
dpkg: error processing /var/cache/apt/archives/python-gnome2-extras_2.19.1-0ubuntu7_i386.deb (--unpack):
 unable to make backup link of `./usr/share/doc/python-gnome2-extras/examples/gdl/gdl_combo_button.py' before installing new version: Operation not permitted
Preparing to replace xfonts-encodings 1:1.0.2-1 (using .../xfonts-encodings_1%3a1.0.2-3_all.deb) ...
Unpacking replacement xfonts-encodings ...
dpkg: error processing /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb (--unpack):
 unable to make backup link of `./usr/share/fonts/X11/encodings/large/big5hkscs-0.enc.gz' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-gnome2-extras_2.19.1-0ubuntu7_i386.deb
 /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
scheung:~ $ 



```

---

### Post by Pumalite on 2008-05-04
Run:
sudo apt-get autoremove
sudo apt-get clean

---

### Post by yinglcs2 on 2008-05-04
I tried this:
Run:
sudo apt-get autoremove
sudo apt-get clean 

And then try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
Post the output. 

But I still get the same error.

```

dpkg: error processing /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb (--unpack):
 unable to make backup link of `./usr/share/fonts/X11/encodings/large/big5hkscs-0.enc.gz' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-gnome2-extras_2.19.1-0ubuntu7_i386.deb
 /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


[CODE]
scheung:~ $  sudo apt-get autoremove
[sudo] password for scheung: 
Sorry, try again.
[sudo] password for scheung: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lirc pwgen libwvstreams4.3-extras libgtkhtml3.8-15 libfaad2-0 libmtp6
  libmtp7 libneon26 libxine1-x libsnmp10 libnet-daemon-perl libgtk1.2 sqlite
  libfame-0.9 libmagick++9c2a libglew1.4 libzvbi0 libxcb-xv0 libdbi-perl
  libpvm3 libmp4v2-0 libpt-1.10.10-plugins-alsa libggzmod4 libsgutils1
  libgtkhtml3.16-cil libpt-1.10.10 libgpod2 libgpod3 libmpeg4ip-dev
  libsqlite0-dev libplrpc-perl libsvg1 libx264-54 setserial gutsy-wallpapers
  libmp4v2-dev libmikmod2 libflickrnet2.1.5-cil libggz2 libxcb-shape0
  libzvbi-common libmpeg4ip-0 libcrypto++6 libgtkhtml2.0-cil gnome-games-data
  transcode ntp libungif4-dev libgsl0 libopal-2.2 libwvstreams4.3-base
  libiso9660-4 libgpod-common xsane-common libmozjs0d libgtk1.2-common
  libdb4.5 libggzcore9 libtotem-plparser7 libuniconf4.3 sqlite3 v4l-conf
  libxcb-shm0 linux-source-2.6.22 libidn11-dev libntfs-3g12 librsvg2.0-cil
  libxine1
The following packages will be REMOVED:
  gnome-games-data gutsy-wallpapers libcrypto++6 libdb4.5 libdbi-perl
  libfaad2-0 libfame-0.9 libflickrnet2.1.5-cil libggz2 libggzcore9 libggzmod4
  libglew1.4 libgpod-common libgpod2 libgpod3 libgsl0 libgtk1.2
  libgtk1.2-common libgtkhtml2.0-cil libgtkhtml3.16-cil libgtkhtml3.8-15
  libidn11-dev libiso9660-4 libmagick++9c2a libmikmod2 libmozjs0d libmp4v2-0
  libmp4v2-dev libmpeg4ip-0 libmpeg4ip-dev libmtp6 libmtp7 libneon26
  libnet-daemon-perl libntfs-3g12 libopal-2.2 libplrpc-perl libpt-1.10.10
  libpt-1.10.10-plugins-alsa libpvm3 librsvg2.0-cil libsgutils1 libsnmp10
  libsqlite0-dev libsvg1 libtotem-plparser7 libungif4-dev libuniconf4.3
  libwvstreams4.3-base libwvstreams4.3-extras libx264-54 libxcb-shape0
  libxcb-shm0 libxcb-xv0 libxine1 libxine1-x libzvbi-common libzvbi0
  linux-source-2.6.22 lirc ntp pwgen setserial sqlite sqlite3 transcode
  v4l-conf xsane-common
0 upgraded, 0 newly installed, 68 to remove and 2 not upgraded.
After this operation, 147MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162085 files and directories currently installed.)
Removing gnome-games-data ...
Removing gutsy-wallpapers ...
Removing libcrypto++6 ...
Removing libuniconf4.3 ...
Removing libwvstreams4.3-extras ...
Removing libdb4.5 ...
Removing libdbi-perl ...
Removing libfaad2-0 ...
Removing transcode ...
Removing libfame-0.9 ...
Removing libflickrnet2.1.5-cil ...
Removing libflickrnet2.1.5-cil from Mono
Removing libggzmod4 ...
Removing libggzcore9 ...
Removing libggz2 ...
Removing libglew1.4 ...
Removing libgpod2 ...
Removing libgsl0 ...
Removing libgtk1.2 ...
Removing libgtk1.2-common ...
Removing libgtkhtml2.0-cil ...
Removing libgtkhtml3.16-cil ...
Removing libgtkhtml3.8-15 ...
Removing libidn11-dev ...
Removing libiso9660-4 ...
Removing libmagick++9c2a ...
Removing libmikmod2 ...
Removing libmozjs0d ...
Removing libmp4v2-dev ...
Removing libmp4v2-0 ...
Removing libmpeg4ip-dev ...
Removing libmpeg4ip-0 ...
Removing libmtp6 ...
Removing libmtp7 ...
Removing libneon26 ...
Removing libplrpc-perl ...
Removing libnet-daemon-perl ...
Removing libntfs-3g12 ...
Removing libopal-2.2 ...
Removing libpt-1.10.10 ...
Removing libpt-1.10.10-plugins-alsa ...
Removing libpvm3 ...
Removing librsvg2.0-cil ...
Removing libsnmp10 ...
Removing libsqlite0-dev ...
Removing libsvg1 ...
Removing libtotem-plparser7 ...
Removing libungif4-dev ...
Removing libwvstreams4.3-base ...
Removing libx264-54 ...
Removing libxine1 ...
Removing libxine1-x ...
Removing libxcb-shape0 ...
Removing libxcb-shm0 ...
Removing libxcb-xv0 ...
Removing libzvbi0 ...
Removing libzvbi-common ...
Removing linux-source-2.6.22 ...
Removing lirc ...
Removing ntp ...
 * Stopping NTP server ntpd                                              [ OK ] 
Removing pwgen ...
Removing setserial ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

Removing sqlite ...
Removing sqlite3 ...
Removing v4l-conf ...
Removing xsane-common ...
Removing libgpod3 ...
Removing libgpod-common ...
Removing libsgutils1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
scheung:~ $ sudo apt-get clean
scheung:~ $ sudo dpkg --configure -a
scheung:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scheung:~ $ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-backports Release            
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/universe Packages     
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Reading package lists... Done
scheung:~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-gnome2-extras xfonts-encodings
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 906kB of archives.
After this operation, 49.2kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main python-gnome2-extras 2.19.1-0ubuntu7 [323kB]
Get:2 http://us.archive.ubuntu.com hardy/main xfonts-encodings 1:1.0.2-3 [584kB]
Fetched 906kB in 7s (117kB/s)                                                  
(Reading database ... 158945 files and directories currently installed.)
Preparing to replace python-gnome2-extras 2.19.1-0ubuntu4 (using .../python-gnome2-extras_2.19.1-0ubuntu7_i386.deb) ...
Unpacking replacement python-gnome[INDENT][/INDENT]2-extras ...
dpkg: error processing /var/cache/apt/archives/python-gnome2-extras_2.19.1-0ubuntu7_i386.deb (--unpack):
 unable to make backup link of `./usr/share/doc/python-gnome2-extras/examples/gdl/gdl_combo_button.py' before installing new version: Operation not permitted
Preparing to replace xfonts-encodings 1:1.0.2-1 (using .../xfonts-encodings_1%3a1.0.2-3_all.deb) ...
Unpacking replacement xfonts-encodings ...
dpkg: error processing /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb (--unpack):
 unable to make backup link of `./usr/share/fonts/X11/encodings/large/big5hkscs-0.enc.gz' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-gnome2-extras_2.19.1-0ubuntu7_i386.deb
 /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
scheung:~ $ 

[/CODE}

---

### Post by novinthen on 2008-05-04
thanks a bunch man.. it worked ;-)

novinthen@novinthen-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


:D .....

now im trying to update into Hardy... ;-) ... :popcorn:

---

### Post by yinglcs2 on 2008-05-04
Hi,

I am still having this problem: Can anyone please help me?

Thank you.

```

dpkg: error processing /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb (--unpack):
 unable to make backup link of `./usr/share/fonts/X11/encodings/large/big5hkscs-0.enc.gz' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-gnome2-extras_2.19.1-0ubuntu7_i386.deb
 /var/cache/apt/archives/xfonts-encodings_1%3a1.0.2-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by cespinal on 2008-08-01
im having a similar problem as well!! 
E: nvidia-glx: subprocess post-removal script returned error exit status 2

I cant friggin get my screen resolution back to normal cuz of that error!

---

