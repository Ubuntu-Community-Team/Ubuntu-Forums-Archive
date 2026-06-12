---
title: "basu upgrade failed!!! help!!!"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by defunkt on 2007-01-16
i was upgrading the base to 6.10 using the deamon and it failed and requested a restart.  so upon restart it booted and i was able to log in.  but my menu's are black and my clock is purple.  the taskbars are multiple colors but still work.  

i figured id run some upgrades, maybe reinstall some packages...  well, i get an error using apt-get upgrade.   here....


admin@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  foomatic-filters-ppds gcc gnumeric gnumeric-common librdf0 linux-image-386
  python-adns python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-eunuchs python-htmlgen python-imaging python-imaging-sane
  python-jabber python-ldap python-mysqldb python-pam python-pexpect
  python-pylibacl python-pyopenssl python-pyxattr python-reportlab
  python-simpletal python-sqlite python-xmpp python2.4-librdf ubuntu-standard
The following packages will be upgraded:
  apache2-common apache2-mpm-prefork apache2-utils at bicyclerepair
  binutils-static bittornado bluez-cups bogofilter bogofilter-bdb
  bogofilter-common bsdmainutils cpp-4.0 dash debconf-utils desktop-base
  dhcp3-client dhcp3-common discover1-data dmsetup dosfstools dselect ethtool
  evms evms-ncurses fdutils fetchmail findutils gcc-4.0 gcc-4.0-base grep
  groff-base grub hostname hwdata info initscripts installation-report iproute
  iptables iputils-arping kdelibs-data klogd language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  less libadns1 libapache2-mod-php5 libapr0 libartsc0 libblkid1 libdb3
  libdb4.2 libdiscover1 libelfg0 libesd-alsa0 libevms-2.5 libgd2-xpm libgeoip1
  libglade2-0 libgmp3c2 libgnucrypto-java libgsl0 libgtk1.2 libgtk1.2-common
  libid3tag0 libijs-0.35 libiw28 libjessie-java libltdl3 libmodplug0c2
  libmpcdec3 libnetpbm10 libpcre3 libpq4 libqt3-mt libraptor1 librasqal0
  libruby1.8 libsqlite0 libss2 libt1-5 libungif4g libuuid1 libvorbisfile3 lshw
  ltrace lvm-common lvm2 lynx manpages mdadm memtest86+ mii-diag mount
  mtr-tiny myspell-en-us mysql-common nano ncurses-base netcat netpbm ntpdate
  odbcinst1debian1 php5 php5-common php5-gd php5-pgsql planner
  popularity-contest powernowd pppconfig pppoeconf procmail python-cddb
  python-epydoc python-examples python-gd python-genetic python-geoip
  python-id3lib python-pqueue python-pyao python-pyogg python-pyvorbis
  python-unit python2.4-examples python2.4-gd reiser4progs reiserfsprogs
  reportbug rsync ruby1.8 slocate strace sysklogd tcpdump telnet ttf-arabeyes
  ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp ttf-bengali-fonts ttf-devanagari-fonts
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts w3m wamerican wbritish
  wireless-tools xfsprogs xscreensaver
164 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
Need to get 0B/86.2MB of archives.
After unpacking 22.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
/tmp/libsqlite0.config.77993: line 8: dpkg: command not found
/tmp/fdutils.config.78301: line 16: dpkg: command not found
/tmp/php5-gd.config.78921: line 16: dpkg: command not found
/tmp/php5-pgsql.config.78923: line 16: dpkg: command not found
/tmp/reiser4progs.config.79233: line 6: dpkg: command not found
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
admin@ubuntu:~$ 




apparently the dpkg doesnt exist...  ive gone into teh directory and it is not there....  could explain teh problem...  

so, knowing that the synaptec packet manager used apt-get, i didnt think it would work, but i looked anyway...  the packet manager isnt even on the menu, nowhere to be found.  

heres the biggest issue i have...  my cdrom doesnt work, i can get a external from a friend, but was hoping there is an easy way to download this file and resintall the packages...  

i ahve the 6.10 cd and the network is up, i could transfer files but i assume they are highley compressed and packaged up so i couldnt get that file.....  


any input would be appreciated...   

Defunkt

---

### Post by defunkt on 2007-01-16
ok...  since my last post i have copied the dpkg file from a friends 6.10 edgy laptop to mine.  but it now returns an error when downloading addition packages....


here

admin@ubuntu:/usr/bin$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  foomatic-filters-ppds gcc gnumeric gnumeric-common librdf0 linux-image-386
  python-adns python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-eunuchs python-htmlgen python-imaging python-imaging-sane
  python-jabber python-ldap python-mysqldb python-pam python-pexpect
  python-pylibacl python-pyopenssl python-pyxattr python-reportlab
  python-simpletal python-sqlite python-xmpp python2.4-librdf ubuntu-standard
The following packages will be upgraded:
  apache2-common apache2-mpm-prefork apache2-utils at bicyclerepair
  binutils-static bittornado bluez-cups bogofilter bogofilter-bdb
  bogofilter-common bsdmainutils cpp-4.0 dash debconf-utils desktop-base
  dhcp3-client dhcp3-common discover1-data dmsetup dosfstools dselect ethtool
  evms evms-ncurses fdutils fetchmail findutils gcc-4.0 gcc-4.0-base grep
  groff-base grub hostname hwdata info initscripts installation-report iproute
  iptables iputils-arping kdelibs-data klogd language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  less libadns1 libapache2-mod-php5 libapr0 libartsc0 libblkid1 libdb3
  libdb4.2 libdiscover1 libelfg0 libesd-alsa0 libevms-2.5 libgd2-xpm libgeoip1
  libglade2-0 libgmp3c2 libgnucrypto-java libgsl0 libgtk1.2 libgtk1.2-common
  libid3tag0 libijs-0.35 libiw28 libjessie-java libltdl3 libmodplug0c2
  libmpcdec3 libnetpbm10 libpcre3 libpq4 libqt3-mt libraptor1 librasqal0
  libruby1.8 libsqlite0 libss2 libt1-5 libungif4g libuuid1 libvorbisfile3 lshw
  ltrace lvm-common lvm2 lynx manpages mdadm memtest86+ mii-diag mount
  mtr-tiny myspell-en-us mysql-common nano ncurses-base netcat netpbm ntpdate
  odbcinst1debian1 php5 php5-common php5-gd php5-pgsql planner
  popularity-contest powernowd pppconfig pppoeconf procmail python-cddb
  python-epydoc python-examples python-gd python-genetic python-geoip
  python-id3lib python-pqueue python-pyao python-pyogg python-pyvorbis
  python-unit python2.4-examples python2.4-gd reiser4progs reiserfsprogs
  reportbug rsync ruby1.8 slocate strace sysklogd tcpdump telnet ttf-arabeyes
  ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp ttf-bengali-fonts ttf-devanagari-fonts
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts w3m wamerican wbritish
  wireless-tools xfsprogs xscreensaver
164 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
Need to get 0B/86.2MB of archives.
After unpacking 22.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 109645 files and directories currently installed.)
Preparing to replace findutils 4.2.22-2 (using .../findutils_4.2.27-3_i386.deb) ...
Document `findutils' is not installed, cannot remove.
Unpacking replacement findutils ...
dpkg: error processing /var/cache/apt/archives/findutils_4.2.27-3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/locate', which is also in package slocate
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/findutils_4.2.27-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
admin@ubuntu:/usr/bin$ 



ive been readon some other entries and they say to do apt-get upgrade then update and repeat....  but i seem to get the same error in teh same spot every time...  
i guess the next step is what to do with the findutils.....  

my hope is if i can install the rest of these its stop what bugs im having.... 

defunkt

---

### Post by Delkster on 2007-01-18
When upgrading from one distribution release to another you should use dist-upgrade instead of upgrade.

It's a little puzzling the dpkg would appear to be missing. Something may be quite badly broken at this point.

In any case, try dist-upgrade instead of upgrade, and you could also try "apt-get -f install" to fix any broken dependencies.

---

### Post by defunkt on 2007-01-18
unfortunatly after i tried using the deamon, i used apt-get dist-upgrade...  but recieved this error...  

after readong some other forums i ahve also tried apt-get -f install but recieve the same error...  



then let me ask another question...  is there an easy way to reinstall the basic packages?  im out of a cd-rom and am afraid this is gonna be a real pain t get reloaded...  its just an old enough laptop that there is no USB boot options...

---

