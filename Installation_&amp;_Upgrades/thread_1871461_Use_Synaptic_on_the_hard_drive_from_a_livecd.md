---
title: "Use Synaptic on the hard drive from a livecd?"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by ElMoshe on 2011-10-28
So, I've sort of really messed up my laptop, and I'm booted off of a live disk, and from terminal I've chroot'ed to my hdd partitions, but I think I need synaptic to fix the problem. How can I direct Synaptic onto my hdd so it reads and installs there, not on the live-session?

---

### Post by oldfred on 2011-10-28
You should not need synaptic. You can install anything from command line once chrooted into your system.

kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

If you know package name, examples with desktop & grub:

# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by ElMoshe on 2011-10-30
So, I'm trying to do what you said before and reinstall kernal, but I get

```
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Ign http://ubuntu.mirrors.tds.net oneiric InRelease
Ign http://ubuntu.mirrors.tds.net oneiric-updates InRelease
Ign http://ubuntu.mirrors.tds.net oneiric-security InRelease
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://dl.google.com stable InRelease
Err http://ubuntu.mirrors.tds.net oneiric Release.gpg
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates Release.gpg
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security Release.gpg
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Ign http://ubuntu.mirrors.tds.net oneiric Release
Ign http://archive.canonical.com oneiric Release
Ign http://extras.ubuntu.com oneiric Release
Ign http://dl.google.com stable Release
Ign http://ubuntu.mirrors.tds.net oneiric-updates Release
Ign http://extras.ubuntu.com oneiric/main Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security Release
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/main Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/restricted Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/multiverse Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/universe Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/main i386 Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner Sources/DiffIndex
Ign http://extras.ubuntu.com oneiric/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric/restricted i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/universe i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/multiverse i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric/main TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric/multiverse TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric/restricted TranslationIndex
Ign http://archive.canonical.com oneiric/partner i386 Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Ign http://dl.google.com stable/main TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric/universe TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/restricted Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/main Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/multiverse Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/universe Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/main i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/restricted i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/universe i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/multiverse i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/main TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/multiverse TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/restricted TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-updates/universe TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/restricted Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/main Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/multiverse Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/universe Sources/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/main i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/restricted i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/universe i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/multiverse i386 Packages/DiffIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/main TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/multiverse TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/restricted TranslationIndex
Ign http://ubuntu.mirrors.tds.net oneiric-security/universe TranslationIndex
Err http://extras.ubuntu.com oneiric/main Sources                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main i386 Packages                         
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main Translation-en_US
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main Translation-en
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main i386 Packages
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en_US
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner Sources
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner i386 Packages                  
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner Translation-en_US              
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner Translation-en                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/main Sources                          
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/restricted Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/multiverse Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/universe Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/main i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/restricted i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/universe i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/multiverse i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/main Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/multiverse Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/multiverse Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/restricted Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/restricted Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/universe Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric/universe Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/restricted Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/main Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/multiverse Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/universe Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/main i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/restricted i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/universe i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/multiverse i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/main Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/main Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/multiverse Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/multiverse Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/restricted Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/restricted Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/universe Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-updates/universe Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/restricted Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/main Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/multiverse Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/universe Sources
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/main i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/restricted i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/universe i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/multiverse i386 Packages
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/main Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/main Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/multiverse Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/multiverse Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/restricted Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/restricted Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/universe Translation-en_US
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
Err http://ubuntu.mirrors.tds.net oneiric-security/universe Translation-en
  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)
W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/Release.gpg  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/Release.gpg  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/main/binary-i386/Packages  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/restricted/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/multiverse/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/universe/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/main/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/restricted/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/universe/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/multiverse/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/multiverse/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/restricted/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_US  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en_US  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/universe/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric/universe/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/restricted/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/main/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/multiverse/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/universe/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/main/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/main/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/restricted/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/main/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/multiverse/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/universe/source/Sources  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/main/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/universe/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/main/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/oneiric-security/universe/i18n/Translation-en  Something wicked happened resolving 'ubuntu.mirrors.tds.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# 

```

Never got this before so I'm sorta stuck...

---

### Post by oldfred on 2011-10-31
It looks like you are missing the network.

sudo: unable to resolve host ubuntu

That is usually related to the cp command for copying resolv.conf. Or was your network down for some other reason.

---

### Post by ElMoshe on 2011-10-31
I mean, I don't think it could be my network because I was on Skype while I ran the update. Any idea on how I can get this to work?

---

### Post by oldfred on 2011-10-31
Were you running from your liveCD without chrooting into your install? You cannot run directly from liveCD as then you are trying to update the CD which is read only.

---

