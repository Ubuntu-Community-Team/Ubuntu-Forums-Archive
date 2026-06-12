---
title: "update manager locks up"
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by engine on 2013-12-20
My trusty ubuntu box is back home, after eight or nine months in storage. Log in, launch Firefox; so far so good.
Open Update manager, which tells me there are 126 updates to install; no real surprise there. Unfortunately ... that's as far as I get :-{ [Settings] doesn't respond, [Close] and [x] don't respond, [Install updates] doesn't start anything.
Any handy tips or tricks for how to run the updates and get my box back? Thanks in advance!

(btx, can't select a prefix - the pulldown won't stay open)

---

### Post by ian-weisser on 2013-12-20
Open a terminal.

Try the following command. Post the *entire* output here. Please use ```
 tags to contain the output.
[code]sudo apt-get update && sudo apt-get upgrade
```

---

### Post by engine on 2013-12-21
Thanks for the tip ... hope the results make sense. Impossible to get to Firefox on the Linux box, but I managed to upload the .txt to a synchronised Dropbox folder and retrieve on another machine. Here goes:
```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common
  bind9-host dhcp3-client dhcp3-common dnsutils firefox firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support firefox-branding
  firefox-gnome-support firefox-locale-en flashplugin-installer gnupg
  gnupg-curl gpgv hpijs hplip hplip-data icedtea-6-jre-cacao icedtea-6-plugin
  icedtea-netx icedtea6-plugin libapache2-mod-php5 libbind9-60 libc-bin
  libc-dev-bin libc6 libc6-dev libc6-i686 libcurl3 libcurl3-gnutls libdns64
  libgcrypt11 libgnutls26 libhpmud0 libisc60 libisccc60 libisccfg60 libjpeg62
  liblwres60 libmysqlclient16 libnspr4-0d libnss3-1d libpam-modules
  libpam-runtime libpam0g libperl5.10 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib4 libpoppler5
  libpq5 libpython2.6 libruby1.8 libservlet2.5-java libsmbclient libssl0.9.8
  libtiff4 libwbclient0 libx11-6 libx11-data libxcb-render0 libxcb1 libxext6
  libxi6 libxml2 libxml2-utils libxrender1 libxslt1.1 libxt6 libxtst6
  libxxf86vm1 linux-libc-dev mysql-client-5.1 mysql-client-core-5.1
  mysql-common mysql-server mysql-server-5.1 mysql-server-core-5.1
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssl perl
  perl-base perl-modules php5 php5-cli php5-common php5-gd php5-mysql
  policykit-1 poppler-utils python python-django python-httplib2
  python-libxml2 python-minimal python-openssl python2.6 python2.6-minimal
  samba-common samba-common-bin smbclient tomboy tzdata tzdata-java webmin
  winbind wuala xserver-common xserver-xephyr xserver-xorg-core xsltproc
120 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 224MB of archives.
After this operation, 10.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Get:1 http://repo.wuala.com/ stable/main wuala 0.5-1 [26.3MB]
Get:2 http://be.archive.ubuntu.com/ubuntu/ lucid-updates/main perl-modules 5.10.1-8ubuntu2.3 [3,486kB]
Get:3 http://download.webmin.com/download/repository/ sarge/contrib webmin 1.660 [21.6MB]
Get:4 http://be.archive.ubuntu.com/ubuntu/ lucid-updates/main libc-bin 2.11.1-0ubuntu7.13 [734kB]
Get:5 http://be.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6 2.11.1-0ubuntu7.13 [3,907kB]
Get:6 http://be.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6-i686 2.11.1-0ubuntu7.13 [1,243kB]
```

---

### Post by Old_Grey_Wolf on 2013-12-21
The desktop version of Lucid (10.04) is no longer supported with updates. You need a newer release.

---

### Post by engine on 2013-12-22
Goodness me - I hadn't realised the machine had been trundling on for so long! OK, thanks for the clear tip.
Now: following the instructions on the ubuntu site for updating 10.04 to 12.04 as the first step, I've gone for System > Administration > Software source. A dialogue box pops up:
```

Could not grab your mouse.
A malicious client may be eavesdropping on your session or you may just have clicked a menu or some application just decided to get focus.
Try again. [Close]

```
This doesn't read like a standard dialogue. Any ideas?

---

### Post by Old_Grey_Wolf on 2013-12-22
> **engine said:**
> 
This doesn't read like a standard dialogue. Any ideas?

It is a real dialogue. It may be better to do a fresh install of 12.04.

I searched and found this.

There are two ways to work around this:

1. After clicking on the package manager, click your desktop, this closes the menu. 
or
2. Make sure all items are showing in the menu (Place,Applications,System). There should be no "tab" bar on the left and a blank dot at the top. When you click on any item in the menu now it should close the menu.

---

### Post by engine on 2013-12-24
Well, now running 12.04 &#8210; I'll assume it's my elderly hardware that makes "walking" closer to the mark than "running" :-} thanks again for the tip.

Snippy observation: once everything had downloaded, the status bar said it should take around 16 hours to complete the upgrade. Not a problem in itself, but I think I had to be there in front of the PC six times to answer questions. I'm not a sysAdmin paid to sit in front of a monitor! the install/upgrade routine should take the trouble to check for these conditions up front and offer one dialogue "You need to confirm/reject the following changes before the upgrade can begin." Yes, this is an observation from a user's point of view, not concerned with practicalities.

Neutral observation: I remembered, too late, that you have to run all available updates before you can upgrade an LTS release. If the Update manager dialogue had included this as a reminder, things might have been easier from the start. 

Next step, and not out of ingratitude: find out how to configure the box to launch from DVD &#8210; sure it always used to &#8210; so I can try a 13.04 version advertised as "extends life of older hardware". <vbg>

---

