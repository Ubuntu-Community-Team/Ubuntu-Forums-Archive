---
title: "Cannot recover from Virtualbox installation"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by RustyWyatt on 2007-04-19
Hi Folks,

First, I am an absolute newbee! I have been running Ubuntu 6.10 for a month or so and have been pretty successful at getting up to speed. Unfortunately, I tried to install "Virtualbox" about a week ago.

Now, when I try to run Synaptic Package Manger I get the following error:

---
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
---

I have tried every solution that I have found in these forums...

After repeated installation attempts, “Virtualbox" always hangs at the blue “acceptance” screen.

Here are a few repair examples:

sudo aptitude install build-essential

3tom@DesktopPC:~$ sudo aptitude install build-essential
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
kdelibs-data kdelibs4c2a libmysqlclient15off libqt3-mt linux-libc-dev
mysql-common
The following packages have been kept back:
evolution evolution-data-server evolution-data-server-common
evolution-plugins file firefox firefox-gnome-support gnome-hearts
language-pack-en language-pack-gnome-en libaudio2 libcamel1.2-8
libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
libedataserver1.2-7 libedataserverui1.2-8 libegroupwise1.2-12
libexchange-storage1.2-2 libfreetype6 libkrb53 libmagic1
libnautilus-extension1 libnspr4 libnss3 libwpd8c2a libx11-6 libx11-data
libxfont1 linux-headers-2.6.17-11 linux-headers-2.6.17-11-generic
linux-image-2.6.17-11-generic nautilus nautilus-data openoffice.org
openoffice.org-base openoffice.org-calc openoffice.org-common
openoffice.org-core openoffice.org-draw openoffice.org-evolution
openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
openoffice.org-java-common openoffice.org-math
openoffice.org-style-default openoffice.org-style-industrial
openoffice.org-writer opera popularity-contest python-uno ttf-opensymbol
update-notifier xmms xserver-xorg-core xserver-xorg-dev
0 packages upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

Then we had

tom@DesktopPC:~$ sudo aptitude update && sudo aptitude upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release [38.4kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages [79.3kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages [14B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources [24.0kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages [14B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages [21.3kB]
Fetched 163kB in 29s (5560B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
opera
The following packages will be upgraded:
digikam evolution evolution-data-server evolution-data-server-common
evolution-plugins file firefox firefox-gnome-support gnome-hearts
kdelibs-data kdelibs4c2a language-pack-en language-pack-gnome-en
libaudio2 libcamel1.2-8 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
libedata-cal1.2-6 libedataserver1.2-7 libedataserverui1.2-8
libegroupwise1.2-12 libexchange-storage1.2-2 libfreetype6 libkrb53
libmagic1 libmysqlclient15off libnautilus-extension1 libnspr4 libnss3
libqt3-mt libwpd8c2a libx11-6 libx11-data libxfont1
linux-headers-2.6.17-11 linux-headers-2.6.17-11-generic
linux-image-2.6.17-11-generic linux-libc-dev mysql-common nautilus
nautilus-data openoffice.org openoffice.org-base openoffice.org-calc
openoffice.org-common openoffice.org-core openoffice.org-draw
openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
openoffice.org-impress openoffice.org-java-common openoffice.org-math
openoffice.org-style-default openoffice.org-style-industrial
openoffice.org-writer popularity-contest python-uno ttf-opensymbol tzdata
update-notifier xmms xserver-xorg-core xserver-xorg-dev
65 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1049kB will be used.
Do you want to continue? [Y/n/?]
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
tom@DesktopPC:~$

I have also tried removing virtualbox via the command line which also failed. I have tried rebooting between all of these attempts.

In the end, I'm still broken...

All help greatly appreciated!!

Tom

---

### Post by ipguru99 on 2007-04-19
The below is from:
[http://virtualbox.org/wiki/User_FAQ](http://virtualbox.org/wiki/User_FAQ)


Debian/Ubuntu 1.3.2 packages: If the installation of the VirtualBox_*.deb package was not successful because the compilation of the kernel module fails, it might not be possible to remove the package nor to install other packages as the pre-remove (prerm) script of the package (which is executed prior to package removing or upgrading) aborts with an error "(Kernel module not found)...fail!". In that case do the following:

    * Edit /etc/init.d/virtualbox and change line 129 from 'exit 1' to 'exit 0'
    * Reinstall the virtualbox package by 'dpkg -i <the VirtualBox package for your distribution>'. An installation failure of this package is expected.
    * Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from 'exit 1' to 'exit 0'
    * Execute 'dpkg --configure --pending'
    * The package should now be installed successfully. However, the kernel module is still not compiled. Before you will be able to execute VirtualBox you have to create a kernel module for your current kernel, as described in the User Manual (see our Downloads section). 

This happened to me as well... ;-)

ipguru99

---

### Post by RustyWyatt on 2007-04-19
Thanks ipguru99,

I'll give this a try tonight!

Tom

---

### Post by RustyWyatt on 2007-04-19
Howdy ipguru99,

I do not seem to have the "/etc/init.d/virtualbox" file. I have searched my HD and browsed around without any luck.  Sorry for the confusion but I am really a newbee...

Thanks,
Tom

---

### Post by iWill on 2007-04-20
Have the exact same problem....anyone can help out?

---

### Post by RustyWyatt on 2007-04-21
Well iWill,

My previously rock solid 6.10 system has become very unstable to the point where I'm going to have to stop using it!  I guess I'll install 7.x from scratch in the next week or so... Meanwhile I'll have to run on my WinXP partition. ;(

This is really the pits but I think we have had the misfortune to need help just when 7.x ihas been released.  Looking at all of the issues upgrading to 7.x, I can understand why no one is thinking about Virtualbox problems...

Good Luck,
Tom

---

