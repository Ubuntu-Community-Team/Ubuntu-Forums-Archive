---
title: "Need help with repository errors after upgrade"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by ahickey on 2008-06-15
I originally installed 7.04 and was very happy.
It worked.  Installed extra apps. They worked.  Life was good.

Then I click the Upgrade when 7.10 was released unleashing a world of pain.  Basically, the upgrade failed and took my system with with.  No apt-get update, apt-get upgrade or any of the other recommendations in this forum could fix it.
It was so bad I couldn't even run terminal.  
After 6 months of intermittently trying to fix it and having to use a Windows system 8.04 LTS was released.  Long term support version.  That has to be solid and reliable.  Canonical aren't going to take a chance on releasing a version that is damaged.  Everything is going to be in place to make it easy to use and install.  SO, I did the install.

It worked... System came up.  I had the usual entertainment with Xorg, but nothing to frighten me.  Even my wireless network worked first time with DHCP.

About a week after installing I was prompted that Updated were available, so I did as recommended and let it install them.
World of pain again.  
I'm on my third re-install of 8.04 (only OS on he system, full hard disk allocated) and it is dead once again due to updates.
Once again I cannot even run terminal, actually this time is worse as I cannot login as bash is broken.

It also says that gstreamer doesn't support i386 when I tried installed the codec to allow me to play divx files.  I think this might not be correct. 

I am actually typing this from a LiveCD version of PupyLinux.

So, I need to do another full, clean install of my operating systems and I'm starting to consider whether it is worth the effort as my computer has been out of action for over 6 months.

I like Ubuntu.  I loved it at 7.04 and I would like that back.

Some of the error messages I got were

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.Could not download all repository indexes

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

I opened [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/) in my browser and downloaded the file manually - still corrupted.
I changed to the main server for updates - same thing happened.
To verify that it wasn't my network creating the errors I Bittorrented some files and they all downloaded perfectly with no errors.

I also got the following set:

> Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

E: /var/cache/apt/archives/libgnutls13_2.0.4-1ubuntu2.1_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/openssh-client_1%3a4.7p1-8ubuntu1.2_i386.deb: corrupted filesystem tarfile - corrupted package archive



E: /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-18-generic_2.6.24-18.26_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/libgnutls13_2.0.4-1ubuntu2.1_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/openssh-client_1%3a4.7p1-8ubuntu1.2_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/evolution_2.22.2-0ubuntu1.2_i386.deb: corrupted filesystem tarfile - corrupted package archive



Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.24-18-generic.
(Reading database ... 95678 files and directories currently installed.)
Unpacking linux-image-2.6.24-18-generic (from .../linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb) ...
Done.
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Selecting previously deselected package linux-ubuntu-modules-2.6.24-18-generic.
Unpacking linux-ubuntu-modules-2.6.24-18-generic (from .../linux-ubuntu-modules-2.6.24-18-generic_2.6.24-18.26_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-18-generic_2.6.24-18.26_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libgnutls13 2.0.4-1ubuntu2 (using .../libgnutls13_2.0.4-1ubuntu2.1_i386.deb) ...
Unpacking replacement libgnutls13 ...
dpkg: error processing /var/cache/apt/archives/libgnutls13_2.0.4-1ubuntu2.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Preparing to replace libssl0.9.8 0.9.8g-4ubuntu3 (using .../libssl0.9.8_0.9.8g-4ubuntu3.1_i386.deb) ...
Unpacking replacement libssl0.9.8 ...
Preparing to replace openssh-client 1:4.7p1-8ubuntu1 (using .../openssh-client_1%3a4.7p1-8ubuntu1.2_i386.deb) ...
Unpacking replacement openssh-client ...
dpkg: error processing /var/cache/apt/archives/openssh-client_1%3a4.7p1-8ubuntu1.2_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace evolution 2.22.1-0ubuntu3 (using .../evolution_2.22.2-0ubuntu1.2_i386.deb) ...
Unpacking replacement evolution ...
dpkg: error processing /var/cache/apt/archives/evolution_2.22.2-0ubuntu1.2_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace evolution-common 2.22.1-0ubuntu3 (using .../evolution-common_2.22.2-0ubuntu1.2_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace evolution-plugins 2.22.1-0ubuntu3 (using .../evolution-plugins_2.22.2-0ubuntu1.2_i386.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace libspeex1 1.1.12-3 (using .../libspeex1_1.1.12-3ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement libspeex1 ...
Preparing to replace gstreamer0.10-plugins-good 0.10.7-3 (using .../gstreamer0.10-plugins-good_0.10.7-3ubuntu0.1_i386.deb) ...
Unpacking replacement gstreamer0.10-plugins-good ...
Preparing to replace linux-generic 2.6.24.16.18 (using .../linux-generic_2.6.24.18.20_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.24.16.18 (using .../linux-image-generic_2.6.24.18.20_i386.deb) ...
Unpacking replacement linux-image-generic ...
Preparing to replace linux-restricted-modules-common 2.6.24.12-16.34 (using .../linux-restricted-modules-common_2.6.24.13-18.41_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Selecting previously deselected package linux-restricted-modules-2.6.24-18-generic.
Unpacking linux-restricted-modules-2.6.24-18-generic (from .../linux-restricted-modules-2.6.24-18-generic_2.6.24.13-18.41_i386.deb) ...
Preparing to replace linux-restricted-modules-generic 2.6.24.16.18 (using .../linux-restricted-modules-generic_2.6.24.18.20_i386.deb) ...
Unpacking replacement linux-restricted-modules-generic ...
Selecting previously deselected package linux-headers-2.6.24-18.
Unpacking linux-headers-2.6.24-18 (from .../linux-headers-2.6.24-18_2.6.24-18.32_all.deb) ...
Selecting previously deselected package linux-headers-2.6.24-18-generic.
Unpacking linux-headers-2.6.24-18-generic (from .../linux-headers-2.6.24-18-generic_2.6.24-18.32_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.24.16.18 (using .../linux-headers-generic_2.6.24.18.20_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace openssl 0.9.8g-4ubuntu3 (using .../openssl_0.9.8g-4ubuntu3.1_i386.deb) ...
Unpacking replacement openssl ...
Preparing to replace ssh-askpass-gnome 1:4.7p1-8ubuntu1 (using .../ssh-askpass-gnome_1%3a4.7p1-8ubuntu1.2_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Selecting previously deselected package openssl-blacklist.
Unpacking openssl-blacklist (from .../openssl-blacklist_0.1-0ubuntu0.8.04.4_all.deb) ...
Preparing to replace ssl-cert 1.0.14-0ubuntu2 (using .../ssl-cert_1.0.14-0ubuntu2.1_all.deb) ...
Unpacking replacement ssl-cert ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb
 /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-18-generic_2.6.24-18.26_i386.deb
 /var/cache/apt/archives/libgnutls13_2.0.4-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openssh-client_1%3a4.7p1-8ubuntu1.2_i386.deb
 /var/cache/apt/archives/evolution_2.22.2-0ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libspeex1 (1.1.12-3ubuntu0.8.04.1) ...

Setting up libssl0.9.8 (0.9.8g-4ubuntu3.1) ...

Setting up openssl (0.9.8g-4ubuntu3.1) ...

Setting up ssh-askpass-gnome (1:4.7p1-8ubuntu1.2) ...

Setting up linux-restricted-modules-common (2.6.24.13-18.41) ...

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not installed.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.22.2); however:
  Version of evolution on system is 2.22.1-0ubuntu3.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.24-18 (2.6.24-18.32) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up gstreamer0.10-plugins-good (0.10.7-3ubuntu0.1) ...

Setting up evolution-common (2.22.2-0ubuntu1.2) ...

Setting up openssl-blacklist (0.1-0ubuntu0.8.04.4) ...
Setting up ssl-cert (1.0.14-0ubuntu2.1) ...

Setting up linux-headers-2.6.24-18-generic (2.6.24-18.32) ...

Setting up linux-headers-generic (2.6.24.18.20) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-restricted-modules-2.6.24-18-generic
 linux-image-generic
 evolution-plugins
 linux-restricted-modules-generic
 linux-generic


My source.list is:

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse


I want to use Ubuntu, but unless the repository and corrupt packages issue isn't resolved I cannot reply on it to work for me when I need it.  Again, how could this happen on the LTS.  With 7.10 I kind of went, that's acceptable because it's kind of bleeding edge, but 8.04 should be rock solid in every way.

Any assistance would be hugely appreciated.  I want o get back to a working computer and my preference (even after all this pain) is to stick with Ubuntu.

---

### Post by ahickey on 2008-06-15
Did a fresh install of 8.04, ignoring the Updates Icon and started to install some apps I wanted.
gftp was one of them and you can see below the error I got.

> 
An error occured

The following details are provided:
E: /var/cache/apt/archives/gftp-gtk_2.0.18-17ubuntu1_i386.deb: corrupted filesystem tarfile - corrupted package archive


I have deleted the file from the folder just in case...

More of the same.

---

### Post by ahickey on 2008-07-22
I have now sorted this.
It was a memory problem.
Replaced my memory and all is working well now.

It was a real intermittent error so took a while to sort out.
I even replaced my motherboard thinking that might be the problem.

Thanks to everybody on the forum for your advice and help.

Albert.

---

