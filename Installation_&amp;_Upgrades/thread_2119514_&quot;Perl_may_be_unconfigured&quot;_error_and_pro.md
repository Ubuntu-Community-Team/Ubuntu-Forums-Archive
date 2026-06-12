---
title: "&quot;Perl may be unconfigured&quot; error and problems with installation"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by Zevaka on 2013-02-24
Dear all,

Let me share my problem and I have high hopes that I can find help here.

Lately during apps installation / upgrade I get the following error (whether doing this from software manager / update manager or via terminal - all the same):

```
installArchives() failed: debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ... 
dpkg: warning: files list file for package 'gnome-power-manager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-cherrypy3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed

<here is the list of another 1,000 packages with the same dpkg error>

dpkg: warning: files list file for package 'libgwibber-gtk3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-vmmouse' missing; assuming package has no files currently installed
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 804 files and directories currently installed.)
Preparing to replace linux-image-3.5.0-25-generic 3.5.0-25.38 (using .../linux-image-3.5.0-25-generic_3.5.0-25.38_amd64.deb) ...
Can't locate Debconf/Client/ConfModule.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /var/lib/dpkg/tmp.ci/preinst line 20.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/preinst line 20.
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-25-generic_3.5.0-25.38_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/lib/perl/5.14/Cwd.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.14/Cwd.pm line 3.
Compilation failed in require at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-25-generic:
 linux-image-extra-3.5.0-25-generic depends on linux-image-3.5.0-25-generic; however:
  Package linux-image-3.5.0-25-generic is not installed.

dpkg: error processing linux-image-extra-3.5.0-25-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-25-generic; however:
  Package linux-image-3.5.0-25-generic is not installed.
 linux-image-generic depends on linux-image-extra-3.5.0-25-generic; however:
  Package linux-image-extra-3.5.0-25-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
```

I tried unsuccessfully:
sudo apt-get install perl --reinstall
sudo dpkg --configure -a
sudo apt-get install -f

Thank you!

---

### Post by ahallubuntu on 2013-02-24
~

---

