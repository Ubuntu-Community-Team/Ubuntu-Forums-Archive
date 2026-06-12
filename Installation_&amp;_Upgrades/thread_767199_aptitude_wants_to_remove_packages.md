---
title: "aptitude wants to remove packages"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by peterff on 2008-04-25
Hi,

I just upgraded from Gutsy to Hardy using the update-manager, which I know is a frontend for apt. I've been using aptitude since the beginning of my Gutsy installation and have not had problems with it, but I've heard that it may attempt to remove packages installed by apt. After running an aptitude update; aptitude safe-upgrade, I get the following output. I believe this is a case of what I described above; however, I thought that one symptom of that problem was that aptitude listed packages installed by apt as automatically installed. Of the few I've checked that are listed below, none is listed by aptitude as automatically installed. On the other hand, apt does not want to remove these packages when I do an apt-get update; apt-get upgrade. Perhaps someone with a Hardy install could tell me if he or she has any of these packages installed--or if they were installed in the process of upgrading to Hardy?

The following packages are unused and will be REMOVED:
  g++-4.1 libconvert-asn1-perl libcrypt-smbhash-perl libdigest-md4-perl 
  libdigest-sha1-perl libdvdread3 libhal-dev libhal-storage-dev 
  libio-socket-ssl-perl libjcode-pm-perl liblzo1 libmp4v2-0 libmudflap0 
  libmudflap0-4.2-dev libnet-ldap-perl libnet-ssleay-perl libnspr4-dev 
  libnss3-dev libqt3-mt libqt4-core libqt4-gui libstdc++6-4.1-dev 
  libtorrent10 libungif4g libunicode-map-perl libunicode-map8-perl 
  libunicode-maputf8-perl libunicode-string-perl libx264-54 libxine1-doc 
  mcpp mozilla-firefox-locale-en-gb smbldap-tools xf86dga xgc xpmutils

---

### Post by Pumalite on 2008-04-25
They are probably debris of your old OS

---

### Post by capink on 2008-04-30
If you want to keep these packages and continue using aptitude, run the following command

```
sudo aptitude keep-all
```

---

