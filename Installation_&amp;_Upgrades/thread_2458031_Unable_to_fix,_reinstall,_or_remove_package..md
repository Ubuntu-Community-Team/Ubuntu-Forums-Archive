---
title: "Unable to fix, reinstall, or remove package."
date: 2021-02-14
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-02-14
I just upgrade a 16.04 LTS to 18.04 LTS and I'm stuck. One package won't fix, install reinstall or remove.
I have never seen this error before . I wonder if I should simple delete or rename '/usr/lib/libpt.so.2.10.11' to see if it will work.

```
# apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-facebook account-plugin-flickr appmenu-qt5 gir1.2-gnomekeyring-1.0
  gnome-icon-theme-symbolic gnome-user-share hardening-includes kate-data katepart
  libaccount-plugin-generic-oauth libapache2-mod-dnssd libautodie-perl libcapnp-0.5.3
  libevent-2.0-5 libgcr-3-common libgfortran3 libgnutls-openssl27 libjs-sphinxdoc libjs-underscore
  libkatepartinterfaces4 libllvm6.0 libnm-gtk-common libopencc1 librpmbuild3 libsub-identify-perl
  libtxc-dxtn-s2tc0 libustr-1.0-1 libxcb-xf86dri0 libxerces-c3.1 python-debianbts python-pyatspi
  python-reportbug signon-plugin-password
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  libpt2.10.11
The following NEW packages will be installed:
  libpt2.10.11
0 upgraded, 1 newly installed, 0 to remove and 598 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,128 kB of archives.
After this operation, 4,030 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 395310 files and directories currently installed.)
Preparing to unpack .../libpt2.10.11_2.10.11~dfsg-2.1_i386.deb ...
Unpacking libpt2.10.11 (2.10.11~dfsg-2.1) ...
dpkg: error processing archive /var/cache/apt/archives/libpt2.10.11_2.10.11~dfsg-2.1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libpt.so.2.10.11', which is also in package libpt2.10.10v5 2.10.11~dfsg-1ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libpt2.10.11_2.10.11~dfsg-2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2021-02-15
rsteinmetz70112 - Hello

As we have:
> 
0 to remove and 598 not upgraded.

there is indications that the system has bot been updated.

Run terminal commands:
```

sudo apt update
sudo apt full-upgrade

```

And advise us of these results.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by rsteinmetz70112 on 2021-02-15
I had run those commands before but failed to capture teh out put so here goes
```
# apt update
Get:1 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:4 http://security.ubuntu.com/ubuntu bionic-security/universe i386 DEP-11 Metadata [59.7 kB]
Get:5 http://security.ubuntu.com/ubuntu bionic-security/main i386 DEP-11 Metadata [48.8 kB]
Get:6 http://security.ubuntu.com/ubuntu bionic-security/multiverse i386 DEP-11 Metadata [2,464 B]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main Sources [504 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [1,220 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [1,884 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 DEP-11 Metadata [295 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 DEP-11 Metadata [2,464 B]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 DEP-11 Metadata [289 kB]
Fetched 4,483 kB in 20s (229 kB/s)

(appstreamcli:22714): GLib-CRITICAL **: 17:50:48.477: g_strchug: assertion 'string != NULL' failed

(appstreamcli:22714): GLib-CRITICAL **: 17:50:48.477: g_strchomp: assertion 'string != NULL' failed

(appstreamcli:22714): GLib-CRITICAL **: 17:50:48.929: g_strchug: assertion 'string != NULL' failed

(appstreamcli:22714): GLib-CRITICAL **: 17:50:48.929: g_strchomp: assertion 'string != NULL' failed

(appstreamcli:22714): GLib-CRITICAL **: 17:50:49.374: g_strchug: assertion 'string != NULL' failed

(appstreamcli:22714): GLib-CRITICAL **: 17:50:49.374: g_strchomp: assertion 'string != NULL' failed
AppStream cache update completed, but some metadata was ignored due to errors.

Reading package lists... Done
Building dependency tree
Reading state information... Done
598 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

```
# apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 ekiga : Depends: libpt2.10.11 but it is not installed
 libopal3.10.10 : Depends: libpt2.10.11 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

The output of ```
apt install -f
``` is in the original message.

---

### Post by Bashing-om on 2021-02-15
rsteinmetz70112; Wow

Have not seen this appstream notice in some years.

What have we to work with ?
show us:
```

apt-cache policy appstream

```

[INDENT][INDENT]as ahunt'n we shall go
[/INDENT][/INDENT]

---

### Post by rsteinmetz70112 on 2021-02-15
Here you go:

```
# apt-cache policy appstream
appstream:
  Installed: 0.9.4-1ubuntu4
  Candidate: 0.12.0-3ubuntu1
  Version table:
     0.12.0-3ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages
     0.12.0-3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main i386 Packages
 *** 0.9.4-1ubuntu4 100
        100 /var/lib/dpkg/status
```

---

### Post by Bashing-om on 2021-02-15
rsteinmetz70112; Uh huh -

Best I recall the 0.9.4-1ubuntu4 version is the affected version

Let's try:
```

sudo apt remove --purge appstream
sudo apt update
sudo apt install appstream
sudo apt full-upgrade

```

[INDENT]maybe Yes
[/INDENT]

---

### Post by rsteinmetz70112 on 2021-02-15
I'm away from my office. I'll try tomorrow.

---

### Post by rsteinmetz70112 on 2021-02-16
Ok here we go:

```
# apt --purge appstream
E: Command line option --purge is not understood in combination with the other options
# apt purge appstream
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 ekiga : Depends: libpt2.10.11 but it is not going to be installed
 gnome-software : Depends: appstream but it is not going to be installed
 libopal3.10.10 : Depends: libpt2.10.11 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```


```
# apt install appstream
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 appstream : Depends: libappstream4 (>= 0.11.7) but it is not going to be installed
             Breaks: gnome-software (< 3.22.5-1) but 3.20.5-0ubuntu0.16.04.13 is to be installed
 ekiga : Depends: libpt2.10.11 but it is not going to be installed
 libopal3.10.10 : Depends: libpt2.10.11 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by rsteinmetz70112 on 2021-02-16
OK Noodling around the Internet I found a dpkg command and tried it:

 ```
sudo dpkg** -i --force-overwrite** /var/cache/apt/archives/libpt2.10.11_2.10.11~dfsg-2.1_i386.deb
```

then 

```
apt install -f 
```worked.

then

```
apt autoremove 
```worked
then 

```
the apt update 
```worked

then
```
apt upgrade 
```failed 

but 
```
apt full-upgrade 
```ran

and fetched 669 MB and 1047 packages
It failed but 

```
apt install -f
``` ran
 but 
```
errors were encountered while processing 
/tmp/apt-dpkg-install-5K2elm/04-gpgconf_2.2.4-1ubuntu1.3_i386.deb
/tmp/apt-dpkg-install-5K2elm/05-gnupg-utils_2.2.4-1ubuntu1.3_i386.deb
/tmp/apt-dpkg-install-5K2elm/06-gpg-agent_2.2.4-1ubuntu1.3_i386.deberrors were encountered
/tmp/apt-dpkg-install-5K2elm/04-gpgconf_2.2.4-1ubuntu1.3_i386.deb
/tmp/apt-dpkg-install-5K2elm/05-gnupg-utils_2.2.4-1ubuntu1.3_i386.deb
/tmp/apt-dpkg-install-5K2elm/06-gpg-agent_2.2.4-1ubuntu1.3_i386.deb

```

But I guess that's progress.

---

### Post by Bashing-om on 2021-02-16
rsteinmetz70112 - Hey hey !

You do good work - sorry about my mistake with the --purge command - fixed in the post.

As many 32 bit (i386) packages are no longer supported - I will have to do some research to provide a better means forward. A cursory look (20.04) indicates that gpgconf in 32 bit arch is still supported.

[INDENT][INDENT]I shall return :)[/INDENT][/INDENT]

---

### Post by Bashing-om on 2021-02-16
rsteinmetz70112; OK

Looking at the [https://packages.ubuntu.com/bionic/gnupg-utils](https://packages.ubuntu.com/bionic/gnupg-utils) tree, looks like all is supported under the  gpgconf package.

Let's try:
```

sudo apt clean
sudo apt remove --purge gpgconf
sudo apt update
sudo apt upgrade
sudo apt install gpgconf
sudo dpkg --configure -a
sudo dpkg -C

```

If all is good then "dpkg -C" will only return to prompt.

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by rsteinmetz70112 on 2021-02-17
I plan to rebuild this with 64 bit, but I decided to upgrade to 18.04 first. 
That may not have ben a good decision :(. 
It now boots but I have processes taking up 100% of the CPU and the console locking up.

---

### Post by CelticWarrior on 2021-02-17
> [COLOR=#000000]That may not have ben a good decision [/COLOR]:sad:[COLOR=#000000].[/COLOR]

Definitely.

---

### Post by rsteinmetz70112 on 2021-02-17
Ok 

```
sudo apt remove --purge gpgconf --simulate
```

Wants to remove a whole bunch of stuff.

```
The following packages will be REMOVED:
  apturl* dirmngr* duplicity* fwupd* fwupd-signed* fwupdate* fwupdate-signed*
  gir1.2-rb-3.0* gnome-software* gnome-software-plugin-snap* gnupg* gpg*
  gpg-agent* gpg-wks-client* gpg-wks-server* gpgconf* gpgsm* gthumb*
  kactivitymanagerd* kde-runtime* kinit* kio* kpackagelauncherqml*
  libblockdev-crypto2* libbrasero-media3-1* libgmime-3.0-0* libgpgme++2v5*
  libgpgme11* libgpgmepp6* libgrilo-0.3-0* libkf5akonadicontact5abi1*
  libkf5akonadimime5* libkf5calendarcore5* libkf5calendarutils-bin*
  libkf5calendarutils5abi1* libkf5contacteditor5* libkf5declarative5*
  libkf5identitymanagement5abi1* libkf5imap5* libkf5kcmutils5*
  libkf5kdelibs4support5* libkf5kdelibs4support5-bin*
  libkf5kdepimdbusinterfaces5* libkf5kontactinterface5* libkf5notifyconfig5*
  libkf5parts-plugins* libkf5parts5* libkf5pimtextedit5abi2* libkf5plasma5*
  libkf5plasmaquick5* libkf5quickaddons5* libkf5tnef5* libkf5wallet-bin*
  libkf5wallet5* libkwalletbackend5-5* libreoffice-avmedia-backend-gstreamer*
  libreoffice-base-core* libreoffice-calc* libreoffice-core* libreoffice-draw*
  libreoffice-gnome* libreoffice-gtk3* libreoffice-help-en-us*
  libreoffice-impress* libreoffice-math* libreoffice-ogltrans*
  libreoffice-pdfimport* libreoffice-presentation-minimizer*
  libreoffice-writer* librhythmbox-core10* libtotem-plparser18*
  libvolume-key1* nautilus-share* plasma-framework* python-apt*
  python-aptdaemon* python-aptdaemon.gtk3widgets* python-gnupginterface*
  python-oneconf* python3-gnupg* python3-software-properties* python3-uno*
  qml-module-org-kde-kconfig* qml-module-org-kde-kirigami2*
  qml-module-org-kde-kquickcontrols* qml-module-org-kde-kquickcontrolsaddons*
  rhythmbox* rhythmbox-plugin-alternative-toolbar* rhythmbox-plugin-zeitgeist*
  rhythmbox-plugins* samba-dsdb-modules* software-center*
  software-properties-common* software-properties-gtk* system-image-common*
  system-image-dbus* ubuntu-extras-keyring* ubuntu-software*
The following NEW packages will be installed:
  gnupg1 gnupg1-l10n
```

And it tells me I have a lot of unused packages

```
The following packages were automatically installed and are no longer required:
  apturl-common brasero-common fonts-opensymbol gir1.2-snapd-1 gnupg-l10n
  gnupg-utils gstreamer1.0-gtk3 gthumb-data icoutils kde-runtime-data
  kdelibs-bin kdelibs5-plugins kdoctools libabw-0.1-1 libboost-iostreams1.65.1
  libboost-locale1.65.1 libburn4 libdmapsharing-3.0-2 libdmtx0a
  libepubgen-0.1-1 libexttextcat-2.0-0 libfwupd2 libical2 libisofs6 libjte1
  libkactivities6 libkcmutils4 libkde3support4 libkdeclarative5 libkdesu5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkf5akonadicontact-data
  libkf5akonadimime-data libkf5calendarcore5abi1 libkf5calendarutils-data
  libkf5contacteditor-data libkf5doctools5 libkf5identitymanagement-data
  libkf5imap-data libkf5kirigami2-5 libkf5pimtextedit-data libkf5prison5
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5 libkf5tnef-data
  libkfile4 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libktexteditor4 libkxmlrpcclient4 libmythes-1.2-0
  libntrack-qt4-1 libntrack0 liborcus-0.13-0 libphonon4 libplasma3
  libpolkit-qt-1-1 libqrencode3 libqt4-opengl libqt4-qt3support
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqtwebkit4 librsync1
  libsmbios-c2 libsolid4 libthreadweaver4 libxmlb1 lp-solve
  ntrack-module-libnl-0 oneconf oneconf-common phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common plasma-scriptengine-javascript python-cups
  python-debian python-debtagshw python-defer python-fasteners
  python-monotonic python-piston-mini-client python-urllib3 python-xapian
  python3-mako python3-oneconf python3-piston-mini-client
  qml-module-qtqml-models2 qml-module-qtquick-controls2
  qml-module-qtquick-templates2 rhythmbox-data
  software-center-aptdaemon-plugins
**Use 'apt autoremove' to remove them.**
```

But

```
# apt autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Basically everything works, as long as I don't try to use the GUI.

Maybe I should let it run and reinstall just unbuntu-desktop

---

### Post by Bashing-om on 2021-02-17
rsteinmetz70112 - Yukkie-poo

Not ready to throw in the towel yet. All's insights into this matter are appreciated :) 
As "autoremove" shows discrepancies in the outputs, let's suppose that mergelist is messed up.
 MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon. When corrupted, they can be safely deleted. Apt will recreate them during the next apt update.

```

sudo apt clean
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade
sudo dpkg -C

```

[INDENT]what now ?
[/INDENT]

---

### Post by rsteinmetz70112 on 2021-02-17
It didn't change the results. 

but:
```
 dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 cdrecord             Dummy transition package for wodim
 libdb4.3             Berkeley v4.3 Database Libraries [runtime]
 libdb4.4             Berkeley v4.4 Database Libraries [runtime]
 libnetcdf3           An interface for scientific data access to large binary d
 libreadline4         GNU readline and history libraries, run-time libraries
 php4-pear            PHP Extension and Application Repository (transitional pa
 sysvutils            System-V-like utilities (transitional package)
 x-window-system-core transitional package for Debian etch
```

I'll try reinstalling those packages tomorrow.

---

### Post by Bashing-om on 2021-02-17
rsteinmetz70112 ; Ouch

Houston, we have a problem >>
```

apt list x-window-system-core

```

[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian) <- Advice On Not Breaking Their System - Don't - just don't ! The same applies to Ubuntu.

I have no experience in cleaning up a Debianstien system. I be pleased to watch the advise of others here.

[INDENT][INDENT]exit stage left
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2021-02-17
B-om I think he is still using Ubuntu.
I myself would probably start with:>>(I'll use aptitude as a rule in these cases)
```
aptitude install pkg-config xserver-xorg-dev
```

---

### Post by rsteinmetz70112 on 2021-02-18
Yes This is Ubuntu18.04 LTS

```
# apt list x-window-system-core
Listing... Done
x-window-system-core/now 1:7.2-5ubuntu13 all [installed,local]
```

I typically use apt to do such things. aptitude is not installed on this computer and I'm hesitant to start installing new  stuff until I can get it straightened out. 

Looking at the packages which are rceccomended for reinstallations  starting at teh top of the list 
```
# apt install cdrecord --reinstall --simulate
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of cdrecord is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
```
# apt remove cdrecord --reinstall --simulate
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  cdrecord
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv cdrecord [9:1.1.2-1ubuntu1]
```

I guess I'll remove it. If I need something else I'll install it later

---

### Post by ActionParsnip on 2021-02-18
What is the output of:
```

apt-cache policy ekiga libpt2.10.11

```
thanks

---

### Post by rsteinmetz70112 on 2021-02-18
OK moving on:

The following packages could not be reinstalled and I was able to remove and purge them:
[LIST]
[*]cdrecord             Dummy transition package for wodim
[*] libdb4.3             Berkeley v4.3 Database Libraries [runtime]
[*] libdb4.4             Berkeley v4.4 Database Libraries [runtime]
[*] libnetcdf3           An interface for scientific data access to large binary d
[*]php4-pear                    PHP Extension and Application Repository (transitional package)
[*]sysvutils                      System-V-like utilities (transitional package)
[*]x-window-system-core  transitional package for Debian etch
[/LIST]

I was unable to reinstall or remove or purge this package using apt or dpkg:
[LIST]
[*]libreadline4         GNU readline and history libraries, run-time libraries
[/LIST]

Researching it appears that this library is from the previous version of Ubuntu. The current version also appears to have some dependency problems.
I think I can probably leave this alone.
Actually I edited  libreadline4.prerm to remove the install-info line. I was then able to remove libread4 and purge it.

I then ran 
```
#apt update
#apt upgrade

```

Both ran clean.
I don't know that I've fixed everything but at least the error messages are gone.

---

### Post by Bashing-om on 2021-02-18
rsteinmetz70112; Yay

Again - good work - 
I still have reservations as to what
"x-window-system-core transitional package for [color=red]Debian etch[/color]
may have done to the GUI, as it is not an ubuntu package:
[https://packages.ubuntu.com/search?keywords=x-window-system-core&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=x-window-system-core&searchon=names&suite=bionic&section=all) >> Sorry, your search gave no results

Maybe just leave well enough alone and live with the miss-used disk space ?

If required to delve into the Debain Window-system; I just do not have the experience to know.

[INDENT]a know it all I am not
[/INDENT]

---

### Post by rsteinmetz70112 on 2021-02-18
OK I have now ```
install deborphan
``` and removed all orphan programs. 

It took several iterations and created a number of autoremoveable file. 

Once I got to no orphan files and no autoremoveable files I updated and upgraded. 

I then reinstalled ubuntu-desktop.

Things seem to be working although I'm still testing.

I've uncovered two linked library issues, but they don't seem to be critical.

---

### Post by rsteinmetz70112 on 2021-02-19
I got this error:

```
/etc/ld.so.conf.d/i386-linux-gnu_EGL.conf: No such file or directory
```
checking on the files I get a bunch of links
```
# ls -l /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf
lrwxrwxrwx 1 root root 41 Apr 18  2015 /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf -> /etc/alternatives/i386-linux-gnu_egl_conf
# ls -l  /etc/alternatives/i386-linux-gnu_egl_conf
lrwxrwxrwx 1 root root 48 Feb 14 16:55 /etc/alternatives/i386-linux-gnu_egl_conf -> /usr/lib/i386-linux-gnu/libhybris-egl/ld.so.conf
# ls -l /usr/lib/i386-linux-gnu/libhybris-egl/ld.so.conf
-rw-r--r-- 1 root root 0 Feb 19 10:37 /usr/lib/i386-linux-gnu/libhybris-egl/ld.so.conf
```

This file doesn't exist on other computers.
Googling it seems to be a broken link from a previous Nvidia driver.

---

