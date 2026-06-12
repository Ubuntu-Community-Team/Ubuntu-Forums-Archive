---
title: "Unable to upgrade"
date: 2016-10-02
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2016-10-02
Hello everyone;

I tried to upgrade, but I encountered an error:

```

The following packages have been kept back:
  clamav-base clamav-daemon clamav-freshclam duplicity icedtea-7-jre-jamvm libgd3 libnx-x11 libxcomp3 libxcompext3
  libxcompshad3 nxagent openjdk-7-jre openjdk-7-jre-headless php-pear x2goagent x2goserver x2goserver-extensions
  x2goserver-xsession youtube-dl
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin bind9 bind9-host bind9utils clamav-docs curl dnsutils eog firefox
  firefox-globalmenu firefox-locale-ar firefox-locale-cs firefox-locale-de firefox-locale-en firefox-locale-es
  firefox-locale-fr firefox-locale-it firefox-locale-nl firefox-locale-pl firefox-locale-pt fontconfig fontconfig-config
  fonts-opensymbol gir1.2-gdkpixbuf-2.0 gnupg gpgv isc-dhcp-client isc-dhcp-common libapache2-mod-php5
  libapache2-mod-php5.6 libapache2-mod-php7.0 libbind9-80 libcurl3 libcurl3-gnutls libcurl3-nss libdns81 libfontconfig1
  libgcrypt11 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libidn11 libisc83 libisccc80 libisccfg82 liblwres80
  libmysqlclient18 libpq5 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-cs libreoffice-help-de
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-help-es libreoffice-help-fr libreoffice-help-it
  libreoffice-help-nl libreoffice-help-pl libreoffice-help-pt libreoffice-help-pt-br libreoffice-impress
  libreoffice-l10n-ar libreoffice-l10n-cs libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-es libreoffice-l10n-fr libreoffice-l10n-it libreoffice-l10n-nl libreoffice-l10n-pl
  libreoffice-l10n-pt libreoffice-l10n-pt-br libreoffice-math libreoffice-style-human libreoffice-style-tango
  libreoffice-writer libssl-dev libssl-doc libssl1.0.2 linux-libc-dev mysql-client-5.5 mysql-client-core-5.5
  mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 openssh-client openssh-server openssl php-common php5
  php5-cgi php5-cli php5-common php5-curl php5-dev php5-gd php5-mcrypt php5-mysql php5-pgsql php5-readline php5-xsl
  php5.6 php5.6-cli php5.6-common php5.6-json php5.6-opcache php5.6-readline php7.0 php7.0-cli php7.0-common php7.0-json
  php7.0-opcache php7.0-readline python-imaging python-uno ssh-askpass-gnome thunderbird thunderbird-globalmenu
  thunderbird-locale-ar thunderbird-locale-cs thunderbird-locale-de thunderbird-locale-en thunderbird-locale-en-gb
  thunderbird-locale-en-us thunderbird-locale-es thunderbird-locale-es-ar thunderbird-locale-es-es thunderbird-locale-fr
  thunderbird-locale-it thunderbird-locale-nl thunderbird-locale-pl thunderbird-locale-pt thunderbird-locale-pt-br
  thunderbird-locale-pt-pt uno-libs3 ure
145 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
11 not fully installed or removed.
Need to get 0 B/401 MB of archives.
After this operation, 6659 kB of additional disk space will be used.
E: Internal Error, No file name for libssl1.0.0

```

I tried to do these:

```

sudo dpkg --configure -a
Reboot
apt-get update
apt-get upgrade
```

But I still get the same error, configuration is:

```

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

Thanks in advance

---

### Post by kc1di on 2016-10-03
Try these commands and try again.

```
sudo apt-get autoclean
sudo apt-get clean
```

---

### Post by ian-weisser on 2016-10-03
Politely disagree. 'clean' will undo all the work of autoclean to remove older package of autoclean, and simply erase the entire package cache. We don't want to do that

Instead, try:
```
sudo apt-get update
sudo apt-get autoclean      // Remove old packages from the cache
sudo dpkg -i /var/cache/apt/archives/libssl1.0.0<TAB>     // Manually install the offending libssl1.0.0 package
sudo apt-get upgrade
```

If the sequence fails, then try:
```
sudo apt-get update
sudo apt-get autoclean
sudo dpkg -i /var/cache/apt/archives/*
sudo apt-get upgrade
```

If that sequence fails, please show us the complete session output.

---

### Post by alfirdaous on 2016-10-03
I run the below command, and I've got this error:

```

# sudo dpkg -i /var/cache/apt/archives/libssl1.0.2_1.0.2j-0+deb.sury.org~precise+1_amd64.deb 
(Reading database ... 193237 files and directories currently installed.)
Preparing to replace libssl1.0.2 1.0.2j-0+deb.sury.org~precise+1 (using .../libssl1.0.2_1.0.2j-0+deb.sury.org~precise+1_amd64.deb) ...
Unpacking replacement libssl1.0.2 ...
Setting up libssl1.0.2 (1.0.2j-0+deb.sury.org~precise+1) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by ian-weisser on 2016-10-03
That's merely a locale warning. Keep going.

---

### Post by alfirdaous on 2016-10-03
Well, now It works, thanks

---

