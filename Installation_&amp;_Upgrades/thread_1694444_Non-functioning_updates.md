---
title: "Non-functioning updates"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by lupo1939 on 2011-02-24
I have 2 updates in the list from Update Manager that will not function.  Both begin "libwvstreams".  When I try to run them nothing happens, the machine goes into suspended animation.  How do I get rid of them (get them out of the list)?

---

### Post by dino99 on 2011-02-24
close update-manager and use synaptic to know about broken packages or else like partial updates

---

### Post by sikander3786 on 2011-02-24
From Applications > Accessories > Terminal, can you please post the output of following command.

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon and post your text in between the generated [code] tags for readability purposes.

---

### Post by lupo1939 on 2011-02-24
sudo apt-get update && sudo apt-get upgrade
[sudo] password for ted: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libwvstreams4.6-extras
The following packages will be upgraded:
  libwvstreams4.6-base
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/254kB of archives.
After this operation, 8,192B disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by sikander3786 on 2011-02-26
What if you say 'yes' and install those updates and again run these 2 commands.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

Say 'no' to both of them.

---

