---
title: "apt-get update timeout"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by mattbilson on 2011-02-20
Hi,

I'm pretty new to Ubuntu and am having some problems with apt-get that I think could be to do with my network/dns.

Any help would be greatly appreciated!

So fresh after installing Ubuntu 10.10, I added the package for Hudson to my sources list :

[LIST]
[*]sudo su
[*]wget -q -O - [http://hudson-ci.org/debian/hudson-ci.org.key](http://hudson-ci.org/debian/hudson-ci.org.key) | apt-key add -
[*]echo "deb [http://hudson-ci.org/debian](http://hudson-ci.org/debian) binary/" > /etc/apt/sources.list.d/hudson.list
[/LIST]
And then ran sudo apt-get update.
Which gave me the output below :

hudson@hudson-virtualbox:~$ sudo apt-get update
Ign [http://hudson-ci.org](http://hudson-ci.org) binary/ Release.gpg               
Ign [http://hudson-ci.org/debian/](http://hudson-ci.org/debian/) binary/ Translation-en    
Ign [http://hudson-ci.org/debian/](http://hudson-ci.org/debian/) binary/ Translation-en_NZ 
Ign [http://hudson-ci.org](http://hudson-ci.org) binary/ Release                   
Ign [http://hudson-ci.org](http://hudson-ci.org) binary/ Packages/DiffIndex
Ign [http://hudson-ci.org](http://hudson-ci.org) binary/ Packages
Ign [http://hudson-ci.org](http://hudson-ci.org) binary/ Packages
Hit [http://hudson-ci.org](http://hudson-ci.org) binary/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_NZ
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_NZ
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_NZ
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources [829kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4,370B]           
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4,370B]           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4,370B]           
99% [4 Sources 0B/4,370B 0%]

The last Get line continued to run (incrementing the number everytime and seemingly unable to find the package). Eventually (it had reached it's 30th try) I cancelled the process.

I then opened Update Manager, opened Settings and within the Ubuntu Software tab, unchecked both "Proprietary drivers for devices (restricted)" and "Software restricted by copyright or legal issues (multiverse)".
After that, running check within Update Manager worked fine.

However on clicking "Install Updates", it hangs on 0% of the first item - dpkg.

Running sudo apt-get update then sudo apt-get upgrade gives the same results.

However, running sudo apt-get install dpkg works fine, and installs dpkg.
Then running sudo apt-get upgrade stalls on the new, first item (login).

It seems I can install items individually using sudo apt-get install [item] but not in a batch using sudo apt-get upgrade. :(

I thought it might be a dns issue, so I've set my DNS servers to 8.8.8.8,8.8.4.4 (Google's public dns) but that doesn't seem to have helped.

Is there a package I need to install to use apt-get to upgrade multiple packages properly?

Any help would be greatly appreciated.
Thanks

---

### Post by Old_Grey_Wolf on 2011-02-20
For those that are going to try to help, can you post the output of this command.
```
cat -n /etc/apt/sources.list
```
Edit: also post the output of this command```
cat -n /etc/apt/sources.list.d/hudson.list
```

---

### Post by mattbilson on 2011-02-20
Thanks Old_Gray_Wolf.

cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main
    11    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
    17    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
    18    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
    19    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    
    27    ## Uncomment the following two lines to add software from the 'backports'
    28    ## repository.
    29    ## N.B. software from this repository may not have been tested as
    30    ## extensively as that contained in the main release, although it includes
    31    ## newer versions of some applications which may provide useful features.
    32    ## Also, please note that software in backports WILL NOT receive any review
    33    ## or updates from the Ubuntu security team.
    34    # deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    35    # deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    36    
    37    ## Uncomment the following two lines to add software from Canonical's
    38    ## 'partner' repository.
    39    ## This software is not part of Ubuntu, but is offered by Canonical and the
    40    ## respective vendors as a service to Ubuntu users.
    41    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
    42    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
    43    
    44    ## This software is not part of Ubuntu, but is offered by third-party
    45    ## developers who want to ship their latest software.
    46    # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
    47    # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
    48    
    49    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main
    50    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main
    51    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
    52    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe

and

cat -n /etc/apt/sources.list.d/hudson.list
     1    deb [http://hudson-ci.org/debian](http://hudson-ci.org/debian) binary/


If there's anything else that could help with this, just let me know.

---

### Post by Old_Grey_Wolf on 2011-02-20
You may be able to enter```
aptitude update
aptitude install hudson
```
If not try entering
```
wget -O /tmp/hudson.deb http://hudson-ci.org/latest/debian/hudson.deb
sudo dpkg --install /tmp/hudson.deb

```

Then do ```
sudo apt-get update
sudo apt-get install hudson
```

---

### Post by mattbilson on 2011-02-21
Thanks Old_Gray_Wolf, however that hasn't solved the problem.

aptitude install hudson failed just like apt-get install [package] - when it tried to load the first dependency.

The wget command worked fine, but then the dpkg install command failed on the dependencies : 
```
 sudo dpkg --install /tmp/hudson.deb
Selecting previously deselected package hudson.
(Reading database ... 118475 files and directories currently installed.)
Unpacking hudson (from /tmp/hudson.deb) ...
dpkg: dependency problems prevent configuration of hudson:
 hudson depends on daemon; however:
  Package daemon is not installed.
 hudson depends on java-virtual-machine; however:
  Package java-virtual-machine is not installed.
 hudson depends on java2-runtime; however:
  Package java2-runtime is not installed.
dpkg: error processing hudson (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 hudson

```

I tried installing daemon independently (and thought of working through all the dependencies mentioned above) but this isn't solving the problem... and there are a lot of dependencies! :O

What is it that's responsible for loading and configuring dependencies? Is it apt-get itself, or something else? Do you think this could be the problem?

Once again, thanks for your help! :)

---

### Post by Old_Grey_Wolf on 2011-02-21
From Hudson's website [http://issues.hudson-ci.org/browse/HUDSON-8741](http://issues.hudson-ci.org/browse/HUDSON-8741).

Apparently they have not populated the repository for Ubuntu.

---

### Post by mattbilson on 2011-02-21
Great spot - I'll definitely take a look in to the new repository as Hudson transitions to Jenkins.
 
  However, because any apt-get upgrade is stalling on items unrelated (or   seemingly unrelated to me), it seems like it's an issue separate to   Hudson.
 
 To test this, I just unchecked the Hudson binary from the Other software tab within Update Manager > Settings.
 
 From my limited knowledge, that should remove Hudson from the problem for now.
 Although when running sudo apt-get upgrade, there are some dependencies which still need meeting.
 
 Running sudo apt-get -f install gives this :
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ca-certificates-java daemon default-jre default-jre-headless gcj-4.4-base
  gcj-4.4-jre-headless gcj-4.4-jre-lib gcj-jre-headless icedtea-6-jre-cacao
  java-common libaccess-bridge-java libaccess-bridge-java-jni libgcj-common
  libgcj10 libgif4 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  ttf-dejavu-extra tzdata tzdata-java
Suggested packages:
  fastjar gcj-4.4-jdk libgcj10-awt gcj-jdk equivs libgcj10-dbg icedtea6-plugin
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts
The following NEW packages will be installed:
  ca-certificates-java daemon default-jre default-jre-headless gcj-4.4-base
  gcj-4.4-jre-headless gcj-4.4-jre-lib gcj-jre-headless icedtea-6-jre-cacao
  java-common libaccess-bridge-java libaccess-bridge-java-jni libgcj-common
  libgcj10 libgif4 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  ttf-dejavu-extra tzdata-java
The following packages will be upgraded:
  tzdata
1 upgraded, 20 newly installed, 0 to remove and 264 not upgraded.
1 not fully installed or removed.
Need to get 60.9MB of archives.
After this operation, 152MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:6 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:7 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
Get:8 http://archive.ubuntu.com/ubuntu/ maverick/universe daemon i386 0.6.4-1 [83.3kB]
0% [8 daemon 0B/83.3kB 0%]

```

Which seems to show a problem getting the first dependency - daemon.

---

### Post by mattbilson on 2011-02-21
'sudo apt-get remove hudson' completely gets rid of hudson (to my knowledge) and fixes the broken dependency issue caused by hudson.

Then running sudo apt-get upgrade once again stalls on the first item :
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups evolution-plugins linux-generic linux-headers-generic
  linux-image-generic
The following packages will be upgraded:
  alsa-utils app-install-data-partner apparmor apparmor-utils apport
  apport-gtk aptdaemon bind9-host brasero brasero-cdrkit brasero-common
  bsdutils compiz compiz-core compiz-gnome compiz-plugins computer-janitor
  computer-janitor-gtk cups-bsd cups-client cups-common dbus dbus-x11 dnsutils
  empathy empathy-common evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange
  firefox firefox-branding firefox-gnome-support fuse-utils gcalctool
  gconf-defaults-service gconf2 gconf2-common gdb gdm-guest-session
  gnome-keyring gnome-settings-daemon gnome-system-tools gvfs gvfs-backends
  gvfs-fuse gwibber gwibber-service hpijs hplip hplip-cups hplip-data
  humanity-icon-theme ibus ibus-gtk ifupdown indicator-sound initscripts
  jockey-common jockey-gtk language-pack-en language-pack-gnome-en
  libapparmor-perl libapparmor1 libasound2 libbind9-60 libblkid1
  libbrasero-media1 libc-bin libc-dev-bin libc6 libc6-dev libcairo2
  libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdbus-1-3 libdecoration0 libdns66 libdrm-intel1
  libdrm-nouveau1 libdrm-radeon1 libdrm2 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13
  libedataserverui1.2-8 libegroupwise1.2-13 libevdocument3 libevolution
  libevview3 libfreetype6 libfuse2 libgconf2-4 libgcr0 libgdata-google1.2-1
  libgdata1.2-1 libgexiv2-0 libgp11-0 libgpod-common libgpod4 libgssapi-krb5-2
  libgudev-1.0-0 libgvfscommon0 libhpmud0 libibus2 libisc60 libisccc60
  libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 liblcms1 libldap-2.4-2
  liblwres60 libmagickcore3 libmagickwand3 libnautilus-extension1 libnss3-1d
  libpam-gnome-keyring libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libparted0debian1 libplymouth2 libpoppler-glib5
  libpoppler7 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin
  libpurple0 libsane-hpaio libsmbclient libsqlite3-0 libssl0.9.8
  libsyncdaemon-1.0-1 libudev0 libutouch-grail1 libuuid1 libvte-common libvte9
  libwbclient0 libwebkit-1.0-2 libwebkit-1.0-common libxml2 libxml2-utils
  light-themes linux-firmware linux-headers-2.6.35-22
  linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic linux-libc-dev
  login media-player-info mount nautilus nautilus-data nautilus-sendto-empathy
  nautilus-share nvidia-96-modaliases openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-style-human openoffice.org-writer openssh-client openssl
  parted passwd pitivi plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text poppler-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python python-apport python-apt python-aptdaemon
  python-aptdaemon-gtk python-cupshelpers python-ibus python-libxml2
  python-minimal python-papyon python-problem-report python-ubuntuone-client
  python-uno python-vte rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins rhythmbox-ubuntuone-music-store samba-common
  samba-common-bin simple-scan smbclient software-center ssh-askpass-gnome
  sudo system-config-printer-common system-config-printer-gnome
  system-config-printer-udev sysv-rc sysvinit-utils tar telepathy-gabble
  telepathy-haze tomboy ttf-opensymbol ttf-ubuntu-font-family tzdata ubufox
  ubuntu-docs ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome udev
  uno-libs3 update-inetd update-manager update-manager-core upstart ure
  util-linux uuid-runtime vino xdg-utils xserver-common xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-video-intel xul-ext-ubufox
  xulrunner-1.9.2
260 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 256MB of archives.
After this operation, 4,526kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:6 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:7 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:8 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:9 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:10 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
Get:11 http://archive.ubuntu.com/ubuntu/ maverick-updates/main login i386 1:4.1.4.2-1ubuntu3.2 [315kB]
0% [11 login 0B/315kB 0%]

```

---

### Post by Old_Grey_Wolf on 2011-02-21
What does ```
sudo apt-get -f install
```do if you enter that command?

---

### Post by mattbilson on 2011-02-21
It gives a similar result to the above, where it seems to stall on the first item.

However... I left the above process running while I left the office for a few hours, and it turns out that on the 173rd attempt, the login package was actually downloaded.

Seems like there's something wrong as it's taking so many attempts and so much time to find packages, but it's currently slowly working through the list of packages which need updating.

Hopefully this will work! Fingers crossed.

Thanks for your help Old_Gray_Wolf

---

### Post by Old_Grey_Wolf on 2011-02-21
> **mattbilson said:**
> It gives a similar result to the above, where it seems to stall on the first item.

However... I left the above process running while I left the office for a few hours, and it turns out that on the 173rd attempt, the login package was actually downloaded.

Seems like there's something wrong as it's taking so many attempts and so much time to find packages, but it's currently slowly working through the list of packages which need updating.

Hopefully this will work! Fingers crossed.

Thanks for your help Old_Gray_Wolf

It is starting to appear that you need to pick a better server for your updates. 

You seem to have had multiple problems simultaneously; which makes it hard to troubleshoot. 

After the updates complete, try this.

Get into Synaptic Package Manager and go to the menu "Settings > Repositories"; then, select "Other..." from the "Download from:" menu. Then click on the "Select Best Server" button. It will take some time for Synaptic to test the servers and give you a suggested server. When it does, click the "Choose Server button". Then follow the instructions to Reload.

Then try the sudo update and sudu upgrade to see if it responds faster.

Edit: I checked the Ubuntu 10.04 and 10.10 repositories and hudson is still not there. I guess you will need to monitor their website to determine how and when you can get hudson installed.

---

### Post by russellbell on 2011-02-21
I think nz.archive.ubuntu.com is broken.  I can't do an apt-get update (or install) either.  See below; I can ping archive.ubuntu.com just fine, but not nz.archive.ubuntu.com.

# apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_NZ
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic Release.gpg
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10), connection timed out
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/main Translation-en_NZ
...

# ping nz.archive.ubuntu.com
PING ubuntu.citylink.co.nz (202.7.6.10) 56(84) bytes of data.
^C
--- ubuntu.citylink.co.nz ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7010ms

# ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.40) 56(84) bytes of data.
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=1 ttl=249 time=302 ms
...

---

### Post by Old_Grey_Wolf on 2011-02-21
If nz.archive.ubuntu.com seems to be broken then get into Synaptic Package Manager and go to the menu "Settings > Repositories", and select a different server.

---

### Post by Old_Grey_Wolf on 2011-02-22
It is sad to say; however, we may now know why the nz.archive.ubuntu.com was not responding. 

6.3 magnitude earth quake.

---

### Post by mattbilson on 2011-02-22
I'm afraid my problem started before the earthquake near Christchurch.

I changed the server to what Ubuntu decided was the best server (an australian server) however updates are still incredibly slow when the the item being upgraded has many dependencies (installing the packages individually works instantly).

---

