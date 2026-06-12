---
title: "Ubuntu cannot find repositories"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Taris-Quickpaw on 2008-03-16
at some point in the last few days, i lost the ability to connect to any of the ubuntu repositories.  i cannot get any programs to install, and this is bad.

I've checked the software sources in System > Software Sources and everything looks like it's on and ready, but when i try to install something, or reload Synaptic Package manager, A window pops up and tells me "could not download repository indexes" and lists them all with an error message.

I'm really kinda stuck here, so if anyone knows what's going on, could you give a linux newb that doesnt know command line a hand?

Error Message:

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release.gpg:](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/i18n/Translation-en_US.bz2:](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://mirror.noreply.org/pub/tor/dists/gutsy/Release.gpg:](http://mirror.noreply.org/pub/tor/dists/gutsy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://mirror.noreply.org/pub/tor/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://mirror.noreply.org/pub/tor/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://packages.medibuntu.org/dists/gusty/Release.gpg:](http://packages.medibuntu.org/dists/gusty/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://packages.medibuntu.org/dists/gusty/free/i18n/Translation-en_US.bz2:](http://packages.medibuntu.org/dists/gusty/free/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://packages.medibuntu.org/dists/gusty/non-free/i18n/Translation-en_US.bz2:](http://packages.medibuntu.org/dists/gusty/non-free/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by Antarctica on 2008-03-16
Localhost:  [http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost).  In short, localhost means you're connecting to yourself.  You should try checking your network settings.  How are you connected to the Internet?  WIreless?  Ethernet?  Dialup modem (God I hope not.  Those things need to die.)?  You're experiencing a network problem.

---

### Post by Taris-Quickpaw on 2008-03-16
well, IM, IRC, webpages(obviously) all work.  i checked, and it's the outbound connection, so i dont know.  =/

---

### Post by Taris-Quickpaw on 2008-03-16
oh yea, it's a wired college connection.

---

### Post by Antarctica on 2008-03-16
Hmm... weird!

---

### Post by Taris-Quickpaw on 2008-03-16
very.  any other recommendations?

---

### Post by Antarctica on 2008-03-16
Try ```
sudo aptitude update
```?

---

### Post by Taris-Quickpaw on 2008-03-16
> Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://mirror.noreply.org](http://mirror.noreply.org) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://mirror.noreply.org](http://mirror.noreply.org) gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done


=/

---

### Post by Bubba64 on 2008-03-17
You might need to change the mirror go to software sources click on download from and you have other which allows you a bunch of different mirrors to choose from you can also have it look for the fastest one but that has never worked for me I use either the main or Canada or the one at my college [email]cat@pdx.edu[/email].

---

### Post by Antarctica on 2008-03-17
Firewall problem?

---

### Post by zvacet on 2008-03-17
You have mixed repos.Put # sign in front of every Feisty line.Then 

```
sudo apt-get update
```

You can try change server to some local near to you.

---

