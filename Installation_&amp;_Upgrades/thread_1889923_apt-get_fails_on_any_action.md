---
title: "apt-get fails on any action"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by mina86 on 2011-12-02
It seems I broke my system beyond repair.

I'm using a Lucid based system (yes, I know, it's a bit old, but bare with me for a sec) but at one point needed a few packages from newer versions (namely armel toolchain) so I've added Oneiric to sources pinning lucid. It worked rather well, but at some other point I've removed the target specification form apt.conf and did an &#8220;apt-get upgrade&#8221; which didn't end that well, and in particular I was missing rxvt-unicode and was unable to install it.

I then tried downgrading my system by specifying &#8220;-t lucid&#8221;, but that didn't quite do the trick. In an act of desperation, I tried commenting out Oneiric from sources and doing an upgrade, but that ended in a disaster.

If I try to install anything, I'm currently getting the following:

```
$ sudo apt-get install rxvt-unicode 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libclass-methodmaker-perl: Depends: perlapi-5.10.0
  libemail-valid-perl: Depends: libnet-dns-perl but it is not going to be installed
  libhtml-parser-perl: Depends: perlapi-5.10.0
  libio-socket-ssl-perl: Depends: libnet-ssleay-perl but it is not going to be installed
  libsub-name-perl: Depends: perlapi-5.10.1
  libterm-readkey-perl: Depends: perlapi-5.10.1
  libtext-charwidth-perl: Depends: perlapi-5.10.0
  libxml-parser-perl: Depends: perlapi-5.10.1
  perl: Depends: perl-modules (>= 5.12.4-4) but 5.10.1-8ubuntu2.1 is to be installed
  rxvt-unicode: Depends: libafterimage0 (>= 2.2.9) but it is not going to be installed
                Depends: libperl5.10 (>= 5.10.1) but it is not going to be installed
  system-tools-backends: Depends: libnet-dbus-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

&#8220;apt-get -f install&#8221; give me some resolution which involves removing half of some core packages, which I don't really want to do. &#8220;aptitude -f install&#8221; gives a more acceptable solution involving downgrading some packages, removing a few, and installing some others, which I'm happy to do except, when it goes to executing the solution, I'm getting:

```
Removing libxml-libxml-perl ...
Can't locate File/Basename.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/share/perl5/XML/SAX.pm line 15.
BEGIN failed--compilation aborted at /usr/share/perl5/XML/SAX.pm line 15.
Compilation failed in require at /usr/bin/update-perl-sax-parsers line 18.
BEGIN failed--compilation aborted at /usr/bin/update-perl-sax-parsers line 18.
dpkg: error processing libxml-libxml-perl (--purge):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 libxml-libxml-perl
Can't locate File/Find.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /usr/bin/debsums line 10.
BEGIN failed--compilation aborted at /usr/bin/debsums line 10.
E: Problem executing scripts DPkg::Post-Invoke 'if [ -x /usr/bin/debsums ]; then /usr/bin/debsums --generate=nocheck -sp /var/cache/apt/archives; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of system-tools-backends:
 system-tools-backends depends on libnet-dbus-perl; however:
  Package libnet-dbus-perl is not installed.
dpkg: error processing system-tools-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libio-socket-ssl-perl:
 libio-socket-ssl-perl depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
dpkg: error processing libio-socket-ssl-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libemail-valid-perl:
 libemail-valid-perl depends on libnet-dns-perl; however:
  Package libnet-dns-perl is not installed.
dpkg: error processing libemail-valid-perl (--configure):
 dependency problems - leaving unconfigured
Setting up udev (173-0ubuntu4) ...
udev start/running, process 28837
info: unrecognized option '--convert-db'
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libnet-smtp-ssl-perl:
 libnet-smtp-ssl-perl depends on libio-socket-ssl-perl; however:
  Package libio-socket-ssl-perl is not configured yet.
dpkg: error processing libnet-smtp-ssl-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane:
 libsane depends on udev (>= 0.88-1); however:
  Package udev is not configured yet.
dpkg: error processing libsane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wireless-crda:
 wireless-crda depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing wireless-crda (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dmraid:
 dmraid depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing dmraid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal:
 hal depends on udev (>= 143); however:
  Package udev is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pcmciautils:
 pcmciautils depends on udev (>= 136-1); however:
  Package udev is not configured yet.
dpkg: error processing pcmciautils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on mountall (>= 2.28); however:
  Package mountall is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of media-player-info:
 media-player-info depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing media-player-info (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-2.6.32-36-generic:
 linux-image-2.6.32-36-generic depends on wireless-crda; however:
  Package wireless-crda is not configured yet.
dpkg: error processing linux-image-2.6.32-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing alsa-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-base:
 alsa-base depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing alsa-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-vmmouse; however:
  Package xserver-xorg-input-vmmouse is not configured yet.
dpkg: error processing xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sane-utils:
 sane-utils depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing sane-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of netbase:
 netbase depends on initscripts; however:
  Package initscripts is not configured yet.
dpkg: error processing netbase (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ifupdown:
 ifupdown depends on initscripts (>= 2.88dsf-13.3); however:
  Package initscripts is not configured yet.
dpkg: error processing ifupdown (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus:
 dbus depends on netbase (>= 4.45ubuntu3); however:
  Package netbase is not configured yet.
dpkg: error processing dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix:
 postfix depends on netbase; however:
  Package netbase is not configured yet.
dpkg: error processing postfix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-36-generic; however:
  Package linux-image-2.6.32-36-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ftp:
 ftp depends on netbase; however:
  Package netbase is not configured yet.
dpkg: error processing ftp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.36.42); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of stunnel4:
 stunnel4 depends on netbase; however:
  Package netbase is not configured yet.
dpkg: error processing stunnel4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lftp:
 lftp depends on netbase; however:
  Package netbase is not configured yet.
dpkg: error processing lftp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on ftp; however:
  Package ftp is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.32.36.42); however:
 libio-socket-ssl-perl
 libemail-valid-perl
 udev
 libnet-smtp-ssl-perl
 xserver-xorg-input-vmmouse
 libsane
 wireless-crda
 dmraid
 mountall
 hal
 pcmciautils
 initscripts
 media-player-info
 linux-image-2.6.32-36-generic
 alsa-utils
 alsa-base
 xserver-xorg-input-all
 sane-utils
 netbase
 ifupdown
 dbus
 postfix
 linux-image-generic
 ftp
 bsd-mailx
 dbus-x11
 linux-generic
 stunnel4
 lftp
 ubuntu-standard
 linux-image
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
```

Is there anything I can do to fix that?

---

### Post by epicoder on 2011-12-02
If I were you, I'd just save /home to an external drive or something and completely reinstall. If you'd rather try to save your current system, then try this:
For each package that aptitude is trying to process, in a root shell:
If it is supposed to be installed or downgraded, download the .deb from [packages.ubuntu.com]("http://packages.ubuntu.com") and run this command.
```
dpkg --force-hold --force-downgrade --force-configure-any -i package.deb
```If it is supposed to be removed, then run this command.
```
dpkg --force-hold --force-depends --purge package
```If dpkg complains about a misconfigured package, then run this command.
```
dpkg --force-hold --configure package
```Be very careful with the force options, as one mistyped option can break your system beyond any hope of repair. Also, do NOT use --force-depends while configuring packages. That can cause the package to be broken when configured.

If you know the exact name of the package you need, then there is a shortcut for downloading it. Go to packages.ubuntu.com/lucid/[i386|amd64]/[package]/download

---

### Post by mina86 on 2011-12-02
> If I were you, I'd just save /home to an external drive or something and completely reinstall.
I'd rather avoid that if possible with not too much struggle.

And with those commands I managed to install perl which let me remove libxml-libxml-perl nicely and resolve most of the other problems (with a “aptitude -f install”).

The only problem that's remaining is that when I try to reconfigure “udev”, I'm getting the following:

```
$ s dpkg --configure udev
Setting up udev (173-0ubuntu4) ...
udev start/running, process 13454
**info: unrecognized option '--convert-db'**
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 udev
```

The “unrecognized option '--convert-db'” message is especially suspicious here. Any idea where it comes from or how could I track it down?

UPDATE: I've downloaded “udev” package for Lucid and installed it with “dpkg -i”. Now everything seems to be in order. Thanks!

---

