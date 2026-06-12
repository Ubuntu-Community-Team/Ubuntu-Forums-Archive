---
title: "Natty 11.04 Update problems"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by 2912pwil on 2011-09-12
Been running 11.04 fine for a couple of months.  About(?) 2 weeks ago started getting slow-downs.

Been having problems with &#8220;Update&#8221; & Natty, 11.04.  

At some point to try & fix I'd done &#8220;apt-get install -f&#8221; and whatever was then suggested (nope, silly me, didn't keep notes of what I'd done: Apologies guys!).  11.04 was a fresh install having wiped previous Ubuntu partition, albeit on dual-booting-with-Windoze system. Ran fine for a couple of months.

From Synaptic...

&#8220;&#8221;&#8221;&#8221;
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

E: Unable to correct dependencies
&#8220;&#8221;&#8221;&#8221;&#8221;&#8221;


From &#8220;Update&#8221; 589 broken packages...
&#8220;&#8221;&#8221;

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

&#8220;&#8221;&#8221;&#8221;&#8221;

From time2time, particularly after boot & after starting &#8220;Update&#8221;, System will appear busy, monitor reports high CPU, disk light on pretty continuous and it feels like it is almost dead/running through treacle.. : Eventually system returns to &#8220;normal&#8221;.  

SW sources now reduced just Canonical for Ubuntu, "Other SW" all boxes unticked, security updates only &#8211; no partners, no 3rd party. 


&#8220;Update&#8221; now reports...

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

When trying &#8220; fix broken packages&#8221; in Synaptic I get..

&#8220;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;
E: Unable to correct problems, you have held broken packages.

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

E: Unable to correct dependencies


&#8220;&#8221;&#8221;&#8221;&#8221;

Any suggestions?? I'm unhappy with a not-up-2-date-on-security system but can't see my way out.

Regards & thanks in advance!!

---

### Post by mörgæs on 2011-09-12
If you want to know which commands you have given earlier, you can just write **history **at the prompt. 

You could try to boot the computer, wait for it to settle and close all programs which might have started automatically, for example Update Manager. After that try the commands

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by 2912pwil on 2011-09-20
Many thanks morgaes , apologies for the delay, been otherwise engaged.

1st 2 commands ran clean...

3rd on gave loads of error messages, couldn't get all of them but here's those I did get - apologies,lots!!!...
> 
                    Depends: python-gobject but it is not installed
                    Depends: policykit-1 but it is not installed
                    Recommends: aptdaemon but it is not installed
 python-aptdaemon.gtk3widgets : Depends: python-gobject (>= 2.27.91) but it is not installed
                                Depends: gir1.2-gtk-2.0 but it is not installed or
                                         gir1.2-gtk-3.0 but it is not installed
                                Depends: gir1.2-vte-0.0 but it is not installed or
                                         gir1.2-vte-2.90 but it is not installed
 python-brlapi : Depends: libbrlapi0.5 but it is not installed
                 Depends: libc6 (>= 2.4) but it is not installed
 python-cairo : Depends: libc6 (>= 2.4) but it is not installed
 python-dbus : Depends: libc6 (>= 2.3.6-6~) but it is not installed
               Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
               Recommends: python-gobject but it is not installed or
                           python-gtk (< 2.10) but it is not installable
 python-egenix-mxdatetime : Depends: libc6 (>= 2.4) but it is not installed
                            Depends: python-central (>= 0.6.11) but it is not installed
 python-egenix-mxtools : Depends: libc6 (>= 2.4) but it is not installed
                         Depends: python-central (>= 0.6.11) but it is not installed
 python-gdbm : Depends: libc6 (>= 2.4) but it is not installed
 python-gmenu : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                Depends: libgnome-menu2 (>= 2.27.92) but it is not installed
                Depends: python-gtk2 but it is not installed
                Depends: python-xdg (>= 0.18-1ubuntu2) but it is not installed
 python-gnome2 : Depends: python-gobject (>= 2.17.0) but it is not installed
                 Depends: python-gtk2 (>= 2.10.3) but it is not installed
                 Depends: python-pyorbit (>= 2.0.1-4) but it is not installed
                 Depends: python2.6-gobject
                 Depends: python2.6-gtk2
                 Depends: python2.6-pyorbit
                 Depends: python2.7-gobject
                 Depends: python2.7-gtk2
                 Depends: python2.7-pyorbit
                 Depends: libatk1.0-0 (>= 1.29.3) but it is not installed
                 Depends: libc6 (>= 2.4) but it is not installed
                 Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
                 Depends: libgnome2-0 (>= 2.17.3) but it is not installed
                 Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installed
                 Depends: libice6 (>= 1:1.0.0) but it is not installed
                 Depends: liborbit2 (>= 1:2.14.10) but it is not installed
                 Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                 Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
                 Depends: libsm6 but it is not installed
                 Depends: python-gconf (= 2.28.1-1ubuntu3) but it is not installed
 python-gnomecanvas : Depends: libatk1.0-0 (>= 1.29.3) but it is not installed
                      Depends: libc6 (>= 2.4) but it is not installed
                      Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                      Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                      Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
 python-gnupginterface : Depends: gnupg (>= 1.2.1) but it is not installed or
                                  gnupg2 but it is not installed
 python-gobject-cairo : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                        Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 python-gtkspell : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
                   Depends: libc6 (>= 2.3.6-6~) but it is not installed
                   Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                   Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                   Depends: python-gtk2 but it is not installed
 python-ibus : Depends: python-gtk2 but it is not installed
               Depends: iso-codes but it is not installed
 python-indicate : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
                   Depends: libc6 (>= 2.4) but it is not installed
                   Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                   Depends: libindicate5 (= 0.5.0-0ubuntu2) but it is not installed
                   Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                   Depends: python-gobject (>= 2.28.1) but it is not installed
 python-launchpad-integration : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                                Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                                Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
                                Depends: python-central (>= 0.6.11) but it is not installed
                                Recommends: launchpad-integration but it is not installed
 python-libproxy : Depends: libproxy0 (>= 0.3.1-2ubuntu5) but it is not installed
 python-mako : Depends: python-markupsafe but it is not installed
 python-minimal : Depends: python2.7-minimal (>= 2.7.1-1~) but it is not installed
                  Depends: dpkg (>= 1.13.20) but it is not installed
 python-papyon : Depends: python-gobject (>= 2.10) but it is not installed
                 Depends: python-openssl (>= 0.6) but it is not installed
                 Depends: python-gst0.10 but it is not installed
                 Depends: python-farsight but it is not installed
                 Depends: python-crypto but it is not installed
 python-pexpect : Depends: python-central (>= 0.6.11) but it is not installed
 python-pycurl : Depends: libc6 (>= 2.3.6-6~) but it is not installed
 python-software-properties : Depends: python-central (>= 0.6.11) but it is not installed
                              Depends: python-apt (>= 0.6.20ubuntu16) but it is not installed
                              Depends: unattended-upgrades but it is not installed
                              Depends: iso-codes but it is not installed
 python-support : Depends: dpkg (>= 1.14.19) but it is not installed
 python-twisted-bin : Depends: libc6 (>= 2.3.6-6~) but it is not installed
 python-twisted-web : Depends: python-twisted-core (>= 10.2) but it is not installed
 python-ubuntuone-client : Depends: python-ubuntuone-storageprotocol (>= 1.6.1) but it is not installed
                           Depends: python-xdg but it is not installed
                           Depends: python-notify but it is not installed
                           Depends: python-pyinotify but it is not installed
                           Depends: python-twisted-names but it is not installed
                           Depends: python-oauth (>= 1.0~svn1092-0ubuntu2) but it is not installed
 python-ubuntuone-control-panel : Depends: python-gobject but it is not installed
                                  Depends: python-oauth but it is not installed
                                  Depends: python-simplejson but it is not installed
                                  Depends: python-twisted-core but it is not installed
 python-wnck : Depends: libc6 (>= 2.3.6-6~) but it is not installed
               Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
               Depends: libwnck22 (>= 1:2.22) but it is not installed
               Depends: python-gtk2 but it is not installed
 python-xkit : Depends: python-central (>= 0.6.11) but it is not installed
 python-zope.interface : Depends: python-central (>= 0.6.11) but it is not installed
                         Depends: libc6 (>= 2.3.6-6~) but it is not installed
 python2.7 : Depends: python2.7-minimal (= 2.7.1-5ubuntu2) but it is not installed
             Depends: mime-support but it is not installed
             Depends: libbz2-1.0 but it is not installed
             Depends: libc6 (>= 2.11) but it is not installed
             Depends: libdb4.8 but it is not installed
             Depends: libncursesw5 (>= 5.6+20070908) but it is not installed
 rfkill : Depends: libc6 (>= 2.4) but it is not installed
 rsync : Depends: libacl1 (>= 2.2.11-1) but it is not installed
         Depends: libc6 (>= 2.8) but it is not installed
 sane-utils : Depends: libavahi-client3 (>= 0.6.16) but it is not installed
              Depends: libavahi-common3 (>= 0.6.16) but it is not installed
              Depends: libc6 (>= 2.4) but it is not installed
 seahorse : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
            Depends: libavahi-client3 (>= 0.6.16) but it is not installed
            Depends: libavahi-common3 (>= 0.6.16) but it is not installed
            Depends: libc6 (>= 2.7) but it is not installed
            Depends: libcryptui0 (>= 2.27.5) but it is not installed
            Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
            Depends: libgnome-keyring0 (>= 2.25.5) but it is not installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
            Depends: libldap-2.4-2 (>= 2.4.7) but it is not installed
            Depends: gconf2 (>= 2.28.1-2) but it is not installed
            Depends: gnupg (>= 1.4.7) but it is not installed
            Recommends: openssh-client but it is not installed
 shared-mime-info : Depends: libc6 (>= 2.3) but it is not installed
                    Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 shotwell : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
            Depends: libc6 (>= 2.7) but it is not installed
            Depends: libexiv2-10 but it is not installed
            Depends: libgee2 (>= 0.5.2) but it is not installed
            Depends: libgexiv2-0 (>= 0.0.91) but it is not installed
            Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
            Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installed
            Depends: libgomp1 (>= 4.2.1) but it is not installed
            Depends: libgphoto2-2 (>= 2.4.10.1) but it is not installed
            Depends: libgphoto2-port0 (>= 2.4.10.1) but it is not installed
            Depends: libgstreamer0.10-0 (>= 0.10.28) but it is not installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
            Depends: liblcms1 (>= 1.15-1) but it is not installed
            Depends: libpango1.0-0 (>= 1.18.0) but it is not installed
            Depends: libstdc++6 (>= 4.4.0) but it is not installed
            Depends: libunique-1.0-0 (>= 1.0.0) but it is not installed
            Depends: librsvg2-common but it is not installed
            Depends: dbus-x11 but it is not installed
 simple-scan : Depends: libc6 (>= 2.4) but it is not installed
               Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
               Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
               Depends: gnome-icon-theme but it is not installed
               Depends: xdg-utils but it is not installed
               Depends: gconf2 (>= 2.28.1-2) but it is not installed
 software-center : Depends: python-central (>= 0.6.11) but it is not installed
                   Depends: humanity-icon-theme but it is not installed
                   Depends: python-xapian but it is not installed
                   Depends: python-apt (>= 0.7.93.1) but it is not installed
                   Depends: python-aptdaemon-gtk but it is not installed
                   Depends: policykit-1 but it is not installed
                   Depends: python-gtk2 but it is not installed
                   Depends: python-webkit but it is not installed
                   Depends: python-xdg but it is not installed
                   Depends: python-gconf but it is not installed
                   Depends: aptdaemon (>= 0.40) but it is not installed
                   Depends: python-lazr.restfulclient but it is not installed
                   Depends: python-piston-mini-client (>= 0.1+bzr29) but it is not installed
                   Recommends: update-notifier but it is not installed
                   Recommends: software-properties-gtk but it is not installed
                   Recommends: sessioninstaller but it is not installed
 ssh-askpass-gnome : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: libx11-6 but it is not installed
                     Depends: openssh-client but it is not installed or
                              ssh (>= 1:1.2pre7-4) but it is not installed or
                              ssh-krb5 but it is not installable
 sudo : Depends: libc6 (>= 2.11) but it is not installed
 system-config-printer-gnome : Depends: system-config-printer-common but it is not installed
                               Depends: python-gtk2 but it is not installed
                               Depends: python-notify but it is not installed
                               Depends: python-gobject but it is not installed
                               Depends: gnome-icon-theme but it is not installed
                               Depends: python-libxml2 but it is not installed
                               Depends: python-gnomekeyring but it is not installed
 system-config-printer-udev : Depends: libc6 (>= 2.4) but it is not installed
                              Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                              Depends: python-cups (>= 1.9.46) but it is not installed
                              Depends: python-cupshelpers but it is not installed
 system-tools-backends : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                         Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                         Depends: libnet-dbus-perl but it is not installed
 sysv-rc : Depends: sysvinit-utils (>= 2.86.ds1-62) but it is not installed
           Depends: insserv (> 1.12.0-10) but it is not installed
 tar : PreDepends: libc6 (>= 2.8) but it is not installed
 tcl8.4 : Depends: libc6 (>= 2.7) but it is not installed
 tcpd : Depends: libc6 (>= 2.4) but it is not installed
        Depends: libwrap0 (>= 7.6-4~) but it is not installed
 telepathy-butterfly : Depends: python-central (>= 0.6.11) but it is not installed
                       Depends: python-gobject but it is not installed
                       Depends: python-telepathy (>= 0.15.19) but it is not installed
 telepathy-gabble : Depends: libc6 (>= 2.7) but it is not installed
                    Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
                    Depends: libgnutls26 (>= 2.7.14-0) but it is not installed
 telepathy-haze : Depends: libc6 (>= 2.4) but it is not installed
                  Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 telepathy-mission-control-5 : Depends: libc6 (>= 2.4) but it is not installed
                               Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
                               Depends: libgnome-keyring0 (>= 2.22.2) but it is not installed
 telnet : Depends: libc6 (>= 2.11) but it is not installed
          Depends: libstdc++6 (>= 4.1.1) but it is not installed
 thunderbird-globalmenu : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
                          Depends: libc6 (>= 2.4) but it is not installed
                          Depends: libdbusmenu-gtk3 (>= 0.4.2) but it is not installed
                          Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
                          Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                          Depends: libstdc++6 (>= 4.1.1) but it is not installed
                          Depends: thunderbird (= 3.1.13+build1+nobinonly-0ubuntu0.11.04.1) but it is not installed
 totem : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
         Depends: libc6 (>= 2.7) but it is not installed
         Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
         Depends: libgstreamer0.10-0 (>= 0.10.30) but it is not installed
         Depends: libice6 (>= 1:1.0.0) but it is not installed
         Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
         Depends: libnautilus-extension1 (>= 2.30) but it is not installed
         Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
         Depends: libsm6 but it is not installed
         Depends: libunique-1.0-0 (>= 1.0.0) but it is not installed
         Depends: libx11-6 but it is not installed
         Depends: libxtst6 but it is not installed
         Depends: libxxf86vm1 but it is not installed
         Depends: gstreamer0.10-plugins-base (>= 0.10.30) but it is not installed
         Depends: gstreamer0.10-alsa but it is not installed or
                  gstreamer0.10-audiosink
         Depends: gstreamer0.10-plugins-good (>= 0.10.7) but it is not installed
         Depends: gstreamer0.10-x but it is not installed
         Depends: gnome-icon-theme (>= 2.15.90) but it is not installed
         Depends: totem-common (>= 2.32) but it is not installed
         Depends: totem-common (< 2.33) but it is not installed
         Recommends: totem-plugins (>= 2.32.0-0ubuntu10) but it is not installed
 totem-mozilla : Depends: libc6 (>= 2.4) but it is not installed
                 Depends: libglib2.0-0 (>= 2.25.11) but it is not installed
                 Depends: libstdc++6 (>= 4.1.1) but it is not installed
                 Depends: libx11-6 but it is not installed
                 Depends: dbus-x11 (>= 0.61) but it is not installed
                 Recommends: epiphany-browser but it is not installable or
                             www-browser
 ttf-ubuntu-font-family : Depends: defoma but it is not installed
 ubuntu-artwork : Depends: light-themes but it is not installed
                  Depends: ubuntu-wallpapers but it is not installed
 ubuntu-extras-keyring : Depends: gnupg but it is not installed
 ubuntu-sso-client : Depends: python-gtk2 but it is not installed
                     Depends: python-lazr.restfulclient but it is not installed
                     Depends: python-oauth but it is not installed
                     Depends: python-twisted-core but it is not installed
                     Depends: python-webkit but it is not installed
                     Depends: python-xdg but it is not installed
                     PreDepends: dpkg (>= 1.15.7.2) but it is not installed
 ubuntu-standard : Depends: at but it is not installed
                   Depends: busybox-static but it is not installed
                   Depends: cpio but it is not installed
                   Depends: cron but it is not installed
                   Depends: dosfstools but it is not installed
                   Depends: ftp but it is not installed
                   Depends: hdparm but it is not installed
                   Depends: info but it is not installed
                   Depends: iptables but it is not installed
                   Depends: language-selector-common but it is not installed
                   Depends: lshw but it is not installed
                   Depends: lsof but it is not installed
                   Depends: ltrace but it is not installed
                   Depends: mime-support but it is not installed
                   Depends: popularity-contest but it is not installed
                   Depends: strace but it is not installed
                   Depends: time but it is not installed
                   Depends: usbutils but it is not installed
                   Depends: wget but it is not installed
                   Recommends: apparmor-utils but it is not installed
                   Recommends: bash-completion but it is not installed
                   Recommends: command-not-found but it is not installed
                   Recommends: friendly-recovery but it is not installed
                   Recommends: iputils-tracepath but it is not installed
                   Recommends: irqbalance but it is not installed
                   Recommends: mlocate but it is not installed
                   Recommends: nano but it is not installed
                   Recommends: openssh-client but it is not installed
                   Recommends: plymouth but it is not installed
                   Recommends: plymouth-theme-ubuntu-text but it is not installed
                   Recommends: pppoeconf but it is not installed
                   Recommends: tcpdump but it is not installed
                   Recommends: ufw but it is not installed
                   Recommends: uuid-runtime but it is not installed
 ubuntuone-client : Depends: gconf2 (>= 2.28.1-2) but it is not installed
                    Depends: python-configglue but it is not installed
 ubuntuone-client-gnome : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
                          Depends: libc6 (>= 2.3.6-6~) but it is not installed
                          Depends: libcamel1.2-19 (>= 2.32) but it is not installed
                          Depends: libcamel1.2-19 (< 2.33) but it is not installed
                          Depends: libglib2.0-0 (>= 2.18.0) but it is not installed
                          Depends: libnautilus-extension1 (>= 2.30) but it is not installed
                          Depends: libnss3 (>= 3.12.2~rc1) but it is not installed
                          Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                          Depends: libsyncdaemon-1.0-1 but it is not installed
                          Depends: python-gtk2 (>= 2.10) but it is not installed
                          Depends: python-simplejson but it is not installed
 ubuntuone-control-panel-gtk : Depends: python-aptdaemon-gtk but it is not installed
                               Depends: python-gobject but it is not installed
                               Depends: python-gtk2 but it is not installed
 unity : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
         Depends: libboost-serialization1.42.0 (>= 1.42.0-1) but it is not installed
         Depends: libc6 (>= 2.4) but it is not installed
         Depends: libdee-1.0-1 (>= 0.5.2) but it is not installed
         Depends: libgl1-mesa-glx but it is not installed or
                  libgl1
         Depends: libglew1.5 (>= 1.5.7.is.1.5.2) but it is not installed
         Depends: libglewmx1.5 (>= 1.5.7.is.1.5.2) but it is not installed
         Depends: libglib2.0-0 (>= 2.28.0) but it is not installed
         Depends: libglibmm-2.4-1c2a (>= 2.28.0) but it is not installed
         Depends: libice6 (>= 1:1.0.0) but it is not installed
         Depends: libindicator3 (>= 0.3.19) but it is not installed
         Depends: libnux-0.9-0 (>= 0.9.42) but it is not installed
         Depends: libpango1.0-0 (>= 1.20.0) but it is not installed
         Depends: libpcre3 (>= 8.10) but it is not installed
         Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
         Depends: libsigc++-2.0-0c2a (>= 2.0.2) but it is not installed
         Depends: libsm6 but it is not installed
         Depends: libstartup-notification0 (>= 0.10) but it is not installed
         Depends: libstdc++6 (>= 4.5) but it is not installed
         Depends: libunity-misc0 (>= 0.2.1) but it is not installed
         Depends: libutouch-geis1 (>= 1.0.8) but it is not installed
         Depends: libwnck22 (>= 1:2.22) but it is not installed
         Depends: libx11-6 but it is not installed
         Depends: libx11-xcb1 but it is not installed
         Depends: libxdamage1 (>= 1:1.1) but it is not installed
         Depends: libxfixes3 (>= 1:4.0.1) but it is not installed
         Depends: libxxf86vm1 but it is not installed
         Depends: gconf2 (>= 2.28.1-2) but it is not installed
         Depends: compiz-plugins-main but it is not installed
         Depends: libglib2.0-bin but it is not installed
         Depends: nux-tools but it is not installed
         Recommends: unity-place-files but it is not installed
         Recommends: indicator-application but it is not installed
         Recommends: indicator-sound but it is not installed
         Recommends: indicator-datetime but it is not installed
         Recommends: indicator-messages but it is not installed
 unity-asset-pool : Depends: gnome-icon-theme but it is not installed
 unity-place-applications : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                            Depends: libdee-1.0-1 (>= 0.5.12) but it is not installed
                            Depends: libgee2 (>= 0.5.2) but it is not installed
                            Depends: libglib2.0-0 (>= 2.28.0) but it is not installed
                            Depends: libgnome-menu2 (>= 2.27.92) but it is not installed
                            Depends: libstdc++6 (>= 4.1.1) but it is not installed
                            Depends: libzeitgeist-1.0-1 (>= 0.3.2) but it is not installed
 update-inetd : Depends: libfile-copy-recursive-perl but it is not installed
 update-manager-core : Depends: python-apt (>= 0.7.13.4ubuntu3) but it is not installed
 ure : Depends: uno-libs3 (= 1.7.0+LibO3.3.3-1ubuntu2) but it is not installed
       Depends: libc6 (>= 2.11) but it is not installed
       Depends: libstdc++6 (>= 4.1.1) but it is not installed
       Depends: libstlport4.6ldbl but it is not installed
 usb-creator-common : Depends: syslinux but it is not installed
                      Depends: udisks (>= 1.0~) but it is not installed
                      Depends: udisks (< 1.1) but it is not installed
                      Depends: genisoimage but it is not installed
                      Depends: python-debian but it is not installed
 usb-modeswitch : Depends: libc6 (>= 2.4) but it is not installed
                  Depends: usb-modeswitch-data (>= 20110227-1~) but it is not installed
                  PreDepends: dpkg (>= 1.15.7.2) but it is not installed
 vim-common : Depends: libc6 (>= 2.4) but it is not installed
              Recommends: vim or
                          vim-gnome but it is not installed or
                          vim-gtk but it is not installable or
                          vim-lesstif but it is not installable or
                          vim-nox but it is not installable or
                          vim-tiny but it is not installed
 vinagre : Depends: libavahi-common3 (>= 0.6.16) but it is not installed
           Depends: libavahi-gobject0 (>= 0.6.22) but it is not installed
           Depends: libc6 (>= 2.4) but it is not installed
           Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
           Depends: libgnome-keyring0 (>= 2.20.3) but it is not installed
           Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
           Depends: libvte9 (>= 1:0.24.0) but it is not installed
           Depends: libx11-6 but it is not installed
           Depends: gconf2 (>= 2.28.1-2) but it is not installed
 whiptail : Depends: libc6 (>= 2.4) but it is not installed
            Depends: libnewt0.52 (>= 0.52.11) but it is not installed
            Depends: libslang2 (>= 2.0.7-1) but it is not installed
 whois : Depends: libc6 (>= 2.4) but it is not installed
         Depends: libidn11 (>= 1.13) but it is not installed
 wireless-crda : Depends: udev but it is not installed
 wpasupplicant : Depends: libc6 (>= 2.4) but it is not installed
                 Depends: libpcsclite1 (>= 1.5.5) but it is not installed
 x11-session-utils : Depends: libc6 (>= 2.7) but it is not installed
                     Depends: libice6 (>= 1:1.0.0) but it is not installed
                     Depends: libsm6 but it is not installed
                     Depends: libx11-6 but it is not installed
                     Depends: libxaw7 but it is not installed
                     Depends: libxt6 but it is not installed
                     Depends: cpp but it is not installed
 x11-xkb-utils : Depends: libc6 (>= 2.7) but it is not installed
                 Depends: libx11-6 but it is not installed
                 Depends: libxaw7 but it is not installed
                 Depends: libxt6 but it is not installed
 xdg-user-dirs-gtk : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: xdg-user-dirs but it is not installed
 xfonts-mathml : Depends: xfonts-utils but it is not installed
 xorg : Depends: libgl1-mesa-glx but it is not installed or
                 libgl1
        Depends: xfonts-base (>= 1:1.0.0-1) but it is not installed
        Depends: x11-apps but it is not installed
        Depends: x11-utils but it is not installed
        Depends: x11-xfs-utils but it is not installed
        Depends: x11-xserver-utils but it is not installed
        Depends: xauth but it is not installed
        Depends: xinit but it is not installed
        Depends: xfonts-utils but it is not installed
        Depends: xkb-data but it is not installed
        Depends: xorg-docs-core but it is not installed
        Depends: x11-common but it is not installed
        Depends: xinput but it is not installed
        Recommends: xfonts-scalable (>= 1:1.0.0-1) but it is not installed
 xscreensaver-data : Depends: libc6 (>= 2.7) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: libx11-6 but it is not installed
                     Depends: libxmu6 but it is not installed
                     Depends: libxt6 but it is not installed
 xsensors : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
            Depends: libc6 (>= 2.4) but it is not installed
            Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
            Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
            Depends: libsensors4 (>= 1:3.0.0) but it is not installed
            Recommends: lm-sensors but it is not installable
 xserver-common : Depends: x11-common but it is not installed
                  Depends: xkb-data but it is not installed
                  Recommends: xfonts-base but it is not installed
                  Recommends: xauth but it is not installed
 xserver-xorg : Depends: libc6 (>= 2.7) but it is not installed
                Depends: xkb-data (>= 1.4) but it is not installed
 xserver-xorg-core : Depends: keyboard-configuration but it is not installed
                     Depends: udev (>= 149) but it is not installed
                     Depends: libc6 (>= 2.8) but it is not installed
                     Depends: libpciaccess0 (>= 0.10.7) but it is not installed
                     Depends: libpixman-1-0 (>= 0.15.16) but it is not installed
                     Depends: libxau6 but it is not installed
 xserver-xorg-input-evdev : Depends: libc6 (>= 2.7) but it is not installed
                            Depends: libmtdev1 (>= 1.0.8) but it is not installed
                            Depends: libutouch-grail1 (>= 1.0.19) but it is not installed
 xserver-xorg-input-synaptics : Depends: udev but it is not installed
                                Depends: libc6 (>= 2.4) but it is not installed
                                Depends: libmtdev1 (>= 1.0.8) but it is not installed
                                Depends: libutouch-grail1 (>= 1.0.19) but it is not installed
                                Depends: libx11-6 but it is not installed
                                Depends: libxi6 (>= 2:1.2.0) but it is not installed
 xserver-xorg-input-vmmouse : Depends: libc6 (>= 2.7) but it is not installed
                              Depends: xserver-xorg-input-mouse but it is not installed
                              Depends: udev but it is not installed
 xserver-xorg-input-wacom : Depends: libc6 (>= 2.4) but it is not installed
                            Depends: libx11-6 but it is not installed
                            Depends: libxi6 (>= 2:1.2.0) but it is not installed
 xserver-xorg-video-all : Depends: xserver-xorg-video-ark but it is not installed
                          Depends: xserver-xorg-video-ati but it is not installed
                          Depends: xserver-xorg-video-chips but it is not installed
                          Depends: xserver-xorg-video-cirrus but it is not installed
                          Depends: xserver-xorg-video-geode but it is not installed
                          Depends: xserver-xorg-video-i128 but it is not installed
                          Depends: xserver-xorg-video-i740 but it is not installed
                          Depends: xserver-xorg-video-intel but it is not installed
                          Depends: xserver-xorg-video-mga but it is not installed
                          Depends: xserver-xorg-video-neomagic but it is not installed
                          Depends: xserver-xorg-video-nouveau but it is not installed
                          Depends: xserver-xorg-video-s3 but it is not installed
                          Depends: xserver-xorg-video-siliconmotion but it is not installed
                          Depends: xserver-xorg-video-sisusb but it is not installed
                          Depends: xserver-xorg-video-tdfx but it is not installed
                          Depends: xserver-xorg-video-trident but it is not installed
                          Depends: xserver-xorg-video-tseng but it is not installed
 xserver-xorg-video-apm : Depends: libc6 (>= 2.4) but it is not installed
 xserver-xorg-video-fbdev : Depends: libc6 (>= 2.1.3) but it is not installed
 xserver-xorg-video-openchrome : Depends: libc6 (>= 2.4) but it is not installed
                                 Depends: libx11-6 but it is not installed
 xserver-xorg-video-qxl : Depends: libc6 (>= 2.3.4) but it is not installed
 xserver-xorg-video-radeon : Depends: libc6 (>= 2.7) but it is not installed
                             Depends: libpciaccess0 (>= 0.10.2) but it is not installed
                             Depends: libpixman-1-0 but it is not installed
 xserver-xorg-video-rendition : Depends: libc6 (>= 2.4) but it is not installed
 xserver-xorg-video-s3virge : Depends: libc6 (>= 2.1.3) but it is not installed
 xserver-xorg-video-savage : Depends: libc6 (>= 2.3.4) but it is not installed
 xserver-xorg-video-sis : Depends: libc6 (>= 2.7) but it is not installed
 xserver-xorg-video-vesa : Depends: libc6 (>= 2.1.3) but it is not installed
 xserver-xorg-video-vmware : Depends: libc6 (>= 2.4) but it is not installed
                             Depends: libx11-6 but it is not installed
 xserver-xorg-video-voodoo : Depends: libc6 (>= 2.1.3) but it is not installed
 xterm : Depends: xbitmaps but it is not installed
         Depends: libc6 (>= 2.11) but it is not installed
         Depends: libice6 (>= 1:1.0.0) but it is not installed
         Depends: libx11-6 but it is not installed
         Depends: libxaw7 but it is not installed
         Depends: libxft2 (> 2.1.1) but it is not installed
         Depends: libxmu6 but it is not installed
         Depends: libxt6 but it is not installed
         Recommends: x11-utils but it is not installed
 zeitgeist : Depends: zeitgeist-datahub but it is not installed
 zeitgeist-core : Depends: python-xdg but it is not installed
                  Depends: python-gobject (>= 2.16.0) but it is not installed
 zeitgeist-extension-fts : Depends: python-xapian but it is not installed
                           Depends: python-xdg but it is not installed
 zlib1g : Depends: libc6 (>= 2.4) but it is not installed
          PreDepends: multiarch-support but it is not installed
E: Unmet dependencies. Try using -f.




Hmmn do I need a fresh re-install??

Regards & thanks in advance you wonderful people!

---

### Post by dino99 on 2011-09-20
> **2912pwil said:**
> Many thanks morgaes , apologies for the delay, been otherwise engaged.

1st 2 commands ran clean...

3rd on gave loads of error messages, couldn't get all of them but here's those I did get - apologies,lots!!!...


Hmmn do I need a fresh re-install??

Regards & thanks in advance you wonderful people!


yeah its done about 30 min

---

### Post by mörgæs on 2011-09-20
Agree. When the package mess is so deep, a fresh install is the fast and safe solution.

---

### Post by 2912pwil on 2011-09-20
Thanks very much Mörgæs, Dino99, what a great service!

---

### Post by 2912pwil on 2012-02-02
Fresh installed 11.10.. (finally...) thanks guys..

---

### Post by mörgæs on 2012-02-02
Good, please mark the thread solved.

---

