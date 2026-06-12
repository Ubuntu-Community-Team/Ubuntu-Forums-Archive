---
title: "apt-get brocken after upgrade.."
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by nfuhs on 2011-11-12
Hi,
my webserver is down... i tried to upgrade my ubuntu system and now if i try apt-get:

The following packages will be upgraded:
  kbd
1 upgraded, 0 newly installed, 36 to remove and 334 not upgraded.
12 not fully installed or removed.
Need to get 0B/239kB of archives.
After this operation, 137MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 80501 files and directories currently installed.)
Preparing to replace kbd 1.15-1ubuntu5 (using .../kbd_1.15.2-3ubuntu1_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 4: dpkg-maintscript-helper: not found
dpkg: error processing /var/cache/apt/archives/kbd_1.15.2-3ubuntu1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 4: dpkg-maintscript-helper: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/kbd_1.15.2-3ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
You have new mail in /var/mail/root

This is serious... i need my webserver back all my websites and so are down...
Please help.
Thanks for reading

---

### Post by L a r r y on 2011-11-12
I'm not sure if I can answer your question, but someone will probably like to have more information:

What version of Ubuntu before upgrade, what version after?

Was it Ubuntu that you upgraded or the server or something else?

What server package, what computer hardware, anything else in terms of details that might help?

I currently run Ubuntu 10.04, and have a XAMPP server running here that serves up a web site for local development.  I have everything set up to be the same pathwise and capabilities wise as the online server. -- Perl, PHP, server side includes, MySQL.

-- Larry

---

### Post by nfuhs on 2011-11-13
root@dante:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

I tried to upgrade to 11.10.
Cant i just clean or rebuilt dpkg

to get rid of this:

dpkg: error processing /var/cache/apt/archives/kbd_1.15.2-3ubuntu1_amd64.deb (--unpack):
subprocess new pre-installation script returned error exit status 127

Thanks for your help so far

---

### Post by nfuhs on 2011-11-13
I also tried this:


root@dante:/var/www# cd /var/cache/apt/archives/
root@dante:/var/cache/apt/archives# dpkg --force-all --install kbd_1.15.2-3ubuntu1_amd64.deb 
(Reading database ... 80500 files and directories currently installed.)
Preparing to replace kbd 1.15-1ubuntu5 (using kbd_1.15.2-3ubuntu1_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 4: dpkg-maintscript-helper: not found
dpkg: error processing kbd_1.15.2-3ubuntu1_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 4: dpkg-maintscript-helper: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Errors were encountered while processing:
 kbd_1.15.2-3ubuntu1_amd64.deb
root@dante:/var/cache/apt/archives# 

I need my server back..

---

### Post by nfuhs on 2011-11-13
Hmm there seem to be more problems..

root@dante:/var/cache/apt/archives# apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  upstart-logd
The following NEW packages will be installed:
  console-setup keyboard-configuration
The following packages have been kept back:
  alien ant-gcj ant-optional-gcj apache2 apache2-mpm-prefork apache2.2-common
  apt apt-utils aptitude avahi-daemon bc bind9-host build-essential
  ca-certificates-java clamav clamav-base clamav-daemon clamav-freshclam
  command-not-found consolekit courier-authdaemon courier-authlib
  courier-authlib-mysql courier-authlib-userdb courier-base courier-ssl cpp
  dhcp3-client dhcp3-common diff dmsetup dnsutils expect ftp g++ gcc gettext
  ghostscript gnupg gpgv iamerican icedtea-6-jre-cacao imagemagick info
  iptables ispell landscape-common libcairo2 libclamav6 libclass-accessor-perl
  libcups2 libcupsimage2 libcurl3 libcurl3-gnutls libdevmapper1.02.1 libgcc1
  libgcj-bc libgl1-mesa-glx libglib2.0-0 libgtk2.0-0 libgtk2.0-bin
  libjaxp1.3-java-gcj libltdl7 libncurses5 libncurses5-dev libnewt0.52
  libnspr4-0d libnss3-1d libpam-modules libpango1.0-0 libpulse0 libpython2.6
  libqt4-assistant libqt4-dbus libqt4-designer libqt4-gui libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-xml libqtcore4 libqtgui4 libsvn1 libthai-data libthai0
  libts-0.0-0 libwww-perl libx11-6 libx11-data libx11-dev libxerces2-java-gcj
  linux-image-server linux-server lsb lsb-desktop lsb-release lvm2 man-db
  mount mysql-server ncurses-bin ntpdate openjdk-6-jdk openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib parted proftpd-basic
  proftpd-mod-ldap proftpd-mod-mysql proftpd-mod-pgsql python python-apt
  python-dbus python-gnupginterface python-gobject python-minimal python-newt
  python-openssl python-pexpect python-pycurl python-serial python-smartpm
  python-twisted-core python2.6 python2.6-minimal qt4-qtconfig rpm subversion
  sysv-rc ubuntu-standard ufw unixodbc update-inetd update-manager-core
  usbutils vim vim-common vim-runtime vim-tiny wireless-tools wpasupplicant
  x11-utils x11proto-core-dev xfsprogs xkb-data zend-framework
The following packages will be upgraded:
  acpid amavisd-new apache2-utils apt-transport-https at base-files
  busybox-initramfs ca-certificates cron dbus debhelper e2fslibs e2fsprogs ed
  fetchmail flex fontconfig-config friendly-recovery grub grub-common hostname
  html2text initscripts iproute iputils-ping kbd less libapache2-mod-php5
  libaprutil1 libarchive-zip-perl libasound2 libatk1.0-0 libaudio2
  libavahi-common3 libcwidget3 libdbus-1-3 libdbus-glib-1-2 libdjvulibre21
  libdrm2 libedit2 libexpat1 libexpat1-dev libfontconfig1 libfreetype6
  libgc1c2 libgcrypt11 libgd2-xpm libgdbm3 libglu1-mesa libgnutls26 libgomp1
  libgpg-error0 libice-dev libice6 libidn11 liblcms1 libldap-2.4-2 libmng1
  libncursesw5 libneon27 libneon27-gnutls libpam0g libpcap0.8 libpcre3
  libpcre3-dev libpcrecpp0 libpixman-1-0 libpng12-0 libpq5 libqt3-mt
  libreadline5 libsasl2-2 libsasl2-modules libselinux1 libsigc++-2.0-0c2a
  libsm-dev libsm6 libsqlite3-0 libss2 libssl-dev libssl0.9.8 libt1-5
  libtasn1-3 libtiff4 libuuid1 libwmf0.2-7 libwrap0 libxau-dev libxau6
  libxcb-render0 libxcb1 libxcb1-dev libxcomposite1 libxcursor1 libxdamage1
  libxdmcp-dev libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1
  libxrandr2 libxrender1 libxt-dev libxt6 libxv1 libxxf86vm1 lilo lprng
  lsb-core lshw lsof lynx lynx-cur lzma mawk mdadm module-init-tools nano
  netbase netcat netcat-traditional ntfs-3g openssh-client openssh-server
  openssl php-pear php5 php5-cli php5-common php5-curl php5-dev php5-gd
  php5-mcrypt php5-mysql postfix ppp procps psmisc re2c screen spamc sudo
  sysklogd tcpdump telnet w3m wget xauth
150 upgraded, 2 newly installed, 1 to remove and 151 not upgraded.
71 not fully installed or removed.
Need to get 0B/42.8MB of archives.
After this operation, 6746kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Couldn't configure pre-depend upstart-job for hostname, probably a dependency cycle.
root@dante:/var/cache/apt/archives# apt-get clean
root@dante:/var/cache/apt/archives# sudo apt-get clean
sudo: unable to resolve host dante
root@dante:/var/cache/apt/archives# 

What should i do?

---

### Post by raja.genupula on 2011-11-13
i have seen some old threads and got something issue with host name ....look at this 
[http://ubuntuforums.org/showthread.php?t=799896](http://ubuntuforums.org/showthread.php?t=799896)

---

### Post by nfuhs on 2011-11-13
Fixed host and hostname but

still problems can´t i just tell ubuntu or apt-get install all new?

Last login: Sun Nov 13 20:32:10 on console
Mac-mini:~ noby$ ssh -c 3des -2 -l root 188.40.129.213 -p 22 
root@188.40.129.213's password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.28-19-server x86_64)

 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Sun Nov 13 20:43:45 CET 2011

  System load:  0.22               Processes:           168
  Usage of /:   0.6% of 687.17GB   Users logged in:     0
  Memory usage: 7%                 IP address for eth0: 188.40.129.213
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

*** /dev/md2 will be checked for errors at next reboot ***
*** /dev/md1 will be checked for errors at next reboot ***

You have new mail.
Last login: Sun Nov 13 17:09:40 2011 from osbk-4db178fe.pool.mediaways.net
root@dante:~# nano /etc/host
host.conf    hostname     hosts        hosts.allow  hosts.deny   
root@dante:~# nano /etc/hosts
root@dante:~# nano /etc/hostname 
root@dante:~# shutdown -r now
The program 'shutdown' can be found in the following packages:
 * upstart
 * molly-guard
Try: apt-get install <selected package>
root@dante:~# apt-get upstart
E: Invalid operation upstart
root@dante:~# apt-get install upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kbd: Depends: console-setup but it is not going to be installed
       Depends: initramfs-tools but it is not going to be installed
  upstart: Depends: initscripts but it is not going to be installed
           Depends: mountall but it is not going to be installed
           Depends: ifupdown (>= 0.6.8ubuntu29)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@dante:~# apt-get install -f upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kbd: Depends: console-setup but it is not going to be installed
       Depends: initramfs-tools but it is not going to be installed
  upstart: Depends: initscripts but it is not going to be installed
           Depends: mountall but it is not going to be installed
           Depends: ifupdown (>= 0.6.8ubuntu29)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
You have new mail in /var/mail/root
root@dante:~#

---

### Post by raja.genupula on 2011-11-14
```
sudo apt-get -f install
```
try this

---

### Post by nfuhs on 2011-11-14
I choosed a reinstall after all didn´t helped the hosting company told me that my server was hacked also...
Now i have a new installation with 11.10 server
is there any tutorial here howto run several kvm machines as webserver and backup them?

Or are there better ideas and ways for the new webserver?
I also plan to run hadoop on it

---

