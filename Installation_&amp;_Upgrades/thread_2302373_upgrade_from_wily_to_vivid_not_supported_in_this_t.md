---
title: "upgrade from wily to vivid not supported in this tool"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by anbu-s on 2015-11-09
I tried to do a software update check it came up with a partial upgrade window - when i click on it , it says upgrade from wily to vivid is not supported in this tool. How do i solve this?
I'm on ubuntu 15.10

---

### Post by Bucky Ball on 2015-11-09
How are you doing the software update?

What errors do these give?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by anbu-s on 2015-11-09
> **Bucky Ball said:**
> How are you doing the software update?

What errors do these give?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

sudo apt-get update gives me this:

```

Hit http://ca.archive.ubuntu.com wily-updates/universe Translation-en         
W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)/dists/vivid/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Bucky Ball on 2015-11-09
An upgrade from Wily to Vivid is not possible. Wily is 15.10, the latest available release. Vivid is the one before it, 15.04. You are trying to downgrade and that is not possible.

Are you fully installed to hard drive or running from install media? If the latter, don't bother with an update. If the former, go to Software and Updates and untick the CD. You are using that as a source and the CD is probably not in the machine, then run the update/upgrade commands again.

---

### Post by grahammechanical on 2015-11-10
You have the vivid vervet (15.04) cdrom as a software source. When we install Ubuntu the cdrom gets listed as a software source but it is then disabled. And so we do not get this error.

Go to Software & Updates >Other Software tab and uncheck the box labelled CDROM with Ubuntu 15.04 "Vivid Vervet" Officially supported Restricted copyright

Having the cdrom listed as a possible software source is useful if we need to install a package from the DVD such as network manager when we do not have an internet connection. But it should be for the version of Ubuntu that is installed and it should be disabled otherwise Update Manager will keep asking us to put the DVD in the drive.

Regards.

---

