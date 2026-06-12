---
title: "Install anything"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by invictuz on 2008-11-07
Hey there, totally lost, I just installed 8.04 so I could dual boot with XP; I have a few programs that I want to throw on here, and I have the .tar files, however, being linux-tarded, I have no clue what it means to compile into "the base directory" of any program.  Thanks for your help.

- Zachary

---

### Post by Sealbhach on 2008-11-07
> **invictuz said:**
> Hey there, totally lost, I just installed 8.04 so I could dual boot with XP; I have a few programs that I want to throw on here, and I have the .tar files, however, being linux-tarded, I have no clue what it means to compile into "the base directory" of any program.  Thanks for your help.

- Zachary

What are you trying to install? Most of the stuff you need you can get in Add/Remove programs or Synaptic or install via the terminal using:

```
sudo apt-get install *packagename*
```


.

---

### Post by Idefix82 on 2008-11-07
Ubuntu comes with a package manager and most things should be installed using that. Go to System->Administration->Synaptic Package Manager and see if that helps you. You can search there by various criteria.

The next best method is to find a .deb file on the internet. That should be easy to install by double clicking it. If that also fails you might start thinking about compiling from source, which is not witch craft but a little more hassle.

Anyway, see if Synaptic has what you are looking for.

By the way, a google search of "Installing software ubuntu" returns this as the first hit:
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by dabl on 2008-11-07
> **invictuz said:**
> Hey there, totally lost, I just installed 8.04 so I could dual boot with XP; I have a few programs that I want to throw on here, and I have the .tar files, however, being linux-tarded, I have no clue what it means to compile into "the base directory" of any program.  Thanks for your help.

- Zachary

No, if you're just starting with Linux, you don't want to "throw programs". You want to open Synaptic and get your packages from the repositories.

Then, if you really want to learn to compile from source code, or convert applications from .rpm to .deb., or things like that, you need to buy a book, or spend some hours with Mr. Google and the many online sources of information like that.

If you start attempting willy-nilly to install from tarballs, you're just going to bork up your new Linux system.  :)

---

### Post by whyiamhere on 2008-11-07
apt-get problem
=================

  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Reading package lists... Done
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release.gpg](http://packages.medibuntu.org/dists/intrepid/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/dapper/Release.gpg](http://packages.medibuntu.org/dists/dapper/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/dapper/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by oldos2er on 2008-11-07
"apt-get problem"

 Rather than hijacking someone else's thread, you should start your own. That said, it looks like you have no internet connection.

---

### Post by oldos2er on 2008-11-07
> **invictuz said:**
> Hey there, totally lost, I just installed 8.04 so I could dual boot with XP; I have a few programs that I want to throw on here, and I have the .tar files, however, being linux-tarded, I have no clue what it means to compile into "the base directory" of any program.  Thanks for your help.

- Zachary

 Please read [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

