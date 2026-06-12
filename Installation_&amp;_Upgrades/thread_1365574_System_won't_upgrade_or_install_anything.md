---
title: "System won't upgrade or install anything"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by shmoofoo on 2009-12-27
i've tried running sudo apt-get update in terminal but i get this message 

[HTML]oem@ubuntu:~$ sudo apt-get update
[sudo] password for oem:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/multiverse Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/universe Translation-en_US
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.48:8080 (192.168.0.48). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
[/HTML]

now i think this has got something to do with the source file but how do i change it? I'm not even sure which version of ubuntu i'm running anymore cuz i've not upgraded my system in over a year. so somebody. please help me out here.

---

### Post by taurus on 2009-12-27
Gutsy, 7.10 (over two years now), has reached the end of its life.  Maybe you should consider backing up your personal files and install the latest one, 9.10, then.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by shmoofoo on 2009-12-27
right.. thanks. but how do i do that? i mean back up files and install the other version. I didn't even install the one i'm running right now. i've no idea how to go about this =/

---

### Post by snowpine on 2009-12-27
> **shmoofoo said:**
> right.. thanks. but how do i do that? i mean back up files and install the other version. I didn't even install the one i'm running right now. i've no idea how to go about this =/

To back up any files you want to keep, just copy them to an external hard drive/USB flash drive/CD-R/etc.

To install Ubuntu: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by taurus on 2009-12-27
Do you have anything important in $HOME that you need to copy/move?  You can copy them to a USB thumbdrive first.  Then. download the latest ISO image and burn it to a CD.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu](https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu)

Then, reboot and install it.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by shmoofoo on 2009-12-27
thankyou taurus and snowpine for replying. i've two questions though. should i backup data of other disk drives as well? cuz once i run installation i don't want to risk loosing all that. but before i even begin with that i want to know if its possible to install the new software through a usb drive? like if i copy the iso image to a usb and run it from there, would it work?

---

### Post by snowpine on 2009-12-28
> **shmoofoo said:**
> thankyou taurus and snowpine for replying. i've two questions though. should i backup data of other disk drives as well? cuz once i run installation i don't want to risk loosing all that. but before i even begin with that i want to know if its possible to install the new software through a usb drive? like if i copy the iso image to a usb and run it from there, would it work?

1. You should always have backups of your data, that is just common sense. :)
2. Yes, you can install Ubuntu from a USB drive instead of a CD: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

