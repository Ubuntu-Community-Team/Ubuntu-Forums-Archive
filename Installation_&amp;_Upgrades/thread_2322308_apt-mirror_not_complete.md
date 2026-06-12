---
title: "apt-mirror not complete?"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by Caruana_Jonathan on 2016-04-27
I use a deployment server for a while now (12.04 and 14.04) and wish to prepare the upgrade to the 16.04 release.


So I edited my apt-mirror-configuration file as follows : 

```

############# config ##################

#
set base_path /mirror
#
# if you change the base path you must create the directories below with write privileges
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
## set defaultarch xxx (votre architecture i386/hppa/powerPC/ia64...)
#set defaultarch ia64
set nthreads 20    
set tilde 0

# trusty 32Bit Mirror
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty                     main restricted universe multiverse
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty-security            main restricted universe multiverse
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty-updates             main restricted universe multiverse
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty-backports           main restricted universe multiverse

deb-i386 http://re.archive.ubuntu.com/ubuntu trusty                     main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty-updates             main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty-security            main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-i386 http://re.archive.ubuntu.com/ubuntu trusty-backports           main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer

# trusty 64Bit Mirror
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty                    main restricted universe multiverse
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty-security           main restricted universe multiverse
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty-updates            main restricted universe multiverse
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty-backports          main restricted universe multiverse

deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty                    main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty-updates            main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty-security           main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://re.archive.ubuntu.com/ubuntu trusty-backports          main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer

# xenial 32Bit Mirror
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial                     main restricted universe multiverse
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial-security            main restricted universe multiverse
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial-updates             main restricted universe multiverse
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial-backports           main restricted universe multiverse

deb-i386 http://re.archive.ubuntu.com/ubuntu xenial                     main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial-updates             main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial-security             main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-i386 http://re.archive.ubuntu.com/ubuntu xenial-backports           main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer

# xenial 64Bit Mirror
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial                          main restricted universe multiverse
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial-updates            main restricted universe multiverse
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial-security             main restricted universe multiverse
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial-backports          main restricted universe multiverse

deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial                        main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial-updates        main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial-security        main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb-amd64 http://re.archive.ubuntu.com/ubuntu xenial-backports          main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer


clean http://re.archive.ubuntu.com/ubuntu
```

after finishing the synchronization I found my good records "Xenial" http accessible.


However, when I test a deployment I meet several 404 errors because many folders "by-hash" are not present:

```

[25/Apr/2016:09:29:23 +0200] "GET /ubuntu/dists/xenial/main/i18n/by-hash/SHA256/f514e12580e59b8f6ae10801a91f14708bdead04db91aa20fe9e2c0384413c67 HTTP/1.1" 404 384 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:29:23 +0200] "GET /ubuntu/dists/xenial/restricted/i18n/by-hash/SHA256/02cbeba7eff7b00f22ee839e33219b7b9a2fd7ee2403e142cb4cdb93d116170b HTTP/1.1" 404 390 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:29:23 +0200] "GET /ubuntu/dists/xenial-updates/main/binary-amd64/by-hash/SHA256/9b57dfc1a6983fabf19bab3c3b2c83b268b54009dff56d1dbd15e93f4beff50a HTTP/1.1" 404 400 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:29:23 +0200] "GET /ubuntu/dists/xenial-updates/main/i18n/by-hash/SHA256/ad702643cb1176cc5ef81306d5944e72217f9fffa587c02976acd4e2b9ee8fa3 HTTP/1.1" 404 392 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:29:23 +0200] "GET /ubuntu/dists/xenial-updates/restricted/binary-amd64/by-hash/SHA256/65de7e01eff8cf2f9a287153971467b1c11811213b64a38bdf673bad240436ff HTTP/1.1" 404 406 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:29:23 +0200] "GET /ubuntu/dists/xenial-updates/restricted/i18n/by-hash/SHA256/65de7e01eff8cf2f9a287153971467b1c11811213b64a38bdf673bad240436ff HTTP/1.1" 404 398 "-" "Debian APT-H
[25/Apr/2016:09:48:16 +0200] "GET /ubuntu/dists/xenial-updates/main/binary-amd64/by-hash/SHA256/9b57dfc1a6983fabf19bab3c3b2c83b268b54009dff56d1dbd15e93f4beff50a HTTP/1.1" 404 400 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:48:16 +0200] "GET /ubuntu/dists/xenial-updates/main/i18n/by-hash/SHA256/ad702643cb1176cc5ef81306d5944e72217f9fffa587c02976acd4e2b9ee8fa3 HTTP/1.1" 404 392 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:48:16 +0200] "GET /ubuntu/dists/xenial-updates/restricted/binary-amd64/by-hash/SHA256/65de7e01eff8cf2f9a287153971467b1c11811213b64a38bdf673bad240436ff HTTP/1.1" 404 406 "-" "Debian APT-HTTP/1.3 (1.2.10)"
[25/Apr/2016:09:48:16 +0200] "GET /ubuntu/dists/xenial-updates/restricted/i18n/by-hash/SHA256/65de7e01eff8cf2f9a287153971467b1c11811213b64a38bdf673bad240436ff HTTP/1.1" 404 398 "-" "Debian APT-
```


Yet they are available on the re.archive.ubuntu.com deposit:

example : [http://re.archive.ubuntu.com/ubuntu/dists/xenial/by-hash/SHA256/](http://re.archive.ubuntu.com/ubuntu/dists/xenial/by-hash/SHA256/)

What should I add in my apt-mirror-configuration file to synchronize them?


Similarly, I tried an update 14.04 to 16.04 pc on a test client notebook, and another folder is missing (deb11) during an "apt-get update" :

```

Failed to fetch http://monurl.int/ubuntu/dists/xenial/multiverse/dep11/Components-amd64.yml
Failed to fetch http://monurl.int/ubuntu/dists/xenial/main/dep11/Components-amd64.yml
...
```

thank you in advance for your help

---

### Post by Caruana_Jonathan on 2016-04-28
Up :(

---

