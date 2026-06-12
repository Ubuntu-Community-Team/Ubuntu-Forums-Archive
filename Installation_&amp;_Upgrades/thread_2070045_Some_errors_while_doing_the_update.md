---
title: "Some errors while doing the update"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2012-10-11
Hi Everybody,

I am facing some errors after the update is done:

```

Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1DB8ADC1CFCA9579
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 09A55915B44C294F
W: Duplicate sources.list entry http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu/ lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_jon-severinsson_ffmpeg_ubuntu_dists_lucid_main_binary-i386_Packages)

```

I appreciate your help

Thanks in advance

---

### Post by jerrrys on 2012-10-11
Here you go

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Duplicate+sources.list&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Duplicate+sources.list&as_qdr=all&sa=Google+Search&lang=en)

If something doesn't make sense, please post back  :)

---

### Post by alfirdaous on 2012-10-12
```

apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1DB8ADC1CFCA9579 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 1DB8ADC1CFCA9579
gpg: requesting key CFCA9579 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

---

