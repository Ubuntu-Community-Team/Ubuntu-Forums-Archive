---
title: "cannot upgrade  feisty to gutsy"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by kenny1948 on 2008-03-07
OK,
I have tried many suggestions on these forums but still cannot seem to upgrade from Feisty to Gutsy.

When I simply tried to update, I got a message" no new release available"

Then I tried one of the commands I saw here and this is what happened:

kenny1948@kenny1948-desktop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
kenny1948@kenny1948-desktop:~$ sudo apt-get upgrade

This is the message I get whenever I try to add or change anything using terminal.
I always get that same could not connect message!

I have no idea what that address is, anyone know?:confused:

---

### Post by Pumalite on 2008-03-07
Check your connection If OK., try changing Server. Also post:
cat /etc/apt/sources.list

---

### Post by kenny1948 on 2008-03-07
what do you mean by changing my server?

You don't mean my internet server?  :confused:

---

### Post by Pumalite on 2008-03-07
System>Administration>Software Sources>Change Server

---

### Post by kenny1948 on 2008-03-07
[

Thanks I will try that.

---

### Post by kenny1948 on 2008-03-07
unfortunately when I tried that, I got another error message unfortunately I Can't cut and paste it into this message.  It says however that

 could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

then there is a long list of urls which I presume are repositories

I have gotten this message before.  I don't understand it.:confused:

---

### Post by Pumalite on 2008-03-07
You can try this other method, but you have to have a good connection:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by kenny1948 on 2008-03-08
Well once again this is what happened:



kenny1948@kenny1948-desktop:~$ sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 
kenny1948@kenny1948-desktop:~$ sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list
kenny1948@kenny1948-desktop:~$ 
kenny1948@kenny1948-desktop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
kenny1948@kenny1948-desktop:~$ 
kenny1948@kenny1948-desktop:~$ sudo apt-get dist-upgrad
E: Invalid operation dist-upgrad
kenny1948@kenny1948-desktop:~$ 

I use a broadband connection through RoadRunner  which is the only ISP that I can use here that is compatible with Linux:(

---

### Post by kenny1948 on 2008-03-08
Pumalite,
I am curious, where are you located?

I am in Florida, USA

Thanks

---

### Post by zvacet on 2008-03-08
**system<admin<software sources>**check all boxes under Ubuntu software and updates tab.Reload.Try to upgrade again.

---

### Post by bapoumba on 2008-03-08
To the OP: are you behind a proxy? Did you set one up?

---

### Post by kenny1948 on 2008-03-12
OK,
I know it's been a few days. I want to thank all who gave me advice!

I finally managed to install Gutsy!:biggrin:

I originally had it coexisting with windows xp, then had to reinstall windows. Because I wanted to install Nero Burning software.  Unfortunately after reloading windows not only did it wipe Linux off my hard drive, it was totally unusable. The version was too old to get an upgrade. Thanks Bill Gates!:mad:

So I somehow finally managed to burn a Gutsy CD which after about four trys finally worked. It downloaded and when it asked me for the partition I deleted it.  I now ONLY have Ubuntu installed, and it is working flawlessly.

Thank you, Thank you, Thank you

---

