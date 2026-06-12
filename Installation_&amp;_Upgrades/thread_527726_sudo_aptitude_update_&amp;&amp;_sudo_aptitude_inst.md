---
title: "sudo aptitude update &amp;&amp; sudo aptitude install kubuntu-desktop"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by RealG187 on 2007-08-16
Okay so I use the method [Here](http://psychocats.net/ubuntu/kde) to install Kubuntu from Ubuntu and it works for me, I like having KDE and GNome and apps from both suites run on my machine.

Problem is bandwidth, I have wireless and internet can cut out (luckily for this is never has) but still on top of that I am limited in Bandwidth and like to have CDs of all the software I download/install, I even keep all my DEBS in /var/cache/apt/archive (I think thats the path).

I was wondering if instead of using my bandwidth for my internet if I could do the same thing with a Kubuntu CD rom, I have both Ubuntu and Kubuntu CD roms, so I could just use the [Gubuntu]("http://bestwikiever.wikidot.com/Gubuntu") CD-ROM to install Ubuntu then use the Kubuntu one to add KDE...

Are the files on Kubuntu CD-Roms capable of doing this , or are the files there made for direct installion and not for adding KDE?

If I cant use a Kubuntu CD, what can I use? Is there an ISO for a CD that will do this? Thanks!

---

### Post by Pumalite on 2007-08-16
This might help; I'm not sure: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by RealG187 on 2007-08-16
So just download like normal and then run this to make a disk? Will it work for KDE, I have most of my DEBs, I dunno which ones are for Kubuntu...

Also will DEBS/Disks from aptoncd from 6.10 work in 7.04 or 7.10? Are the DEBs for specific versions?

---

### Post by RealG187 on 2007-09-19
Can somebody reply, I wanna put Linux on my Laptop but have been waiting like 4 months!

---

### Post by maybeway36 on 2007-09-19
You should be able to add the Kubuntu CD to sources.list with:
```
sudo apt-cdrom add
```

---

### Post by RealG187 on 2007-09-19
> **maybeway36 said:**
> You should be able to add the Kubuntu CD to sources.list with:
```
sudo apt-cdrom add
```
So I can type that then the normal command then it will install of the CD-ROM?

---

### Post by RealG187 on 2008-05-28
I am doing another install of Ubuntu and need to know this.

If I type that command will it use the CD and not internet? Is there a priority system?

---

### Post by maybeway36 on 2008-05-30
I think it will use the newer version, or the CD if the packages are the same version.

---

### Post by RealG187 on 2008-05-30
okay so it will only use the internet is it needs too, and in that case I will get the newer ones anyways!

Or to be safe, if I unplug my USB network card (well it's not really a card, more of a box like thing) and after adding the CD to the repo then running the command will it use the CD since it cant find the internet, or will it give an error saying it cant find the files?

---

### Post by RealG187 on 2008-06-01
I tried and it just kept on saying the same thing, I tired apt-get install kubuntu-desktop and that didnt work either.

> ger_2.1.3ubuntu17.1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-batch_2.1.3ubuntu17.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-batch_2.1.3ubuntu17.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-dev_2.5.1-5ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-dev_2.5.1-5ubuntu5.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pykdeextensions/libpythonize0_0.4.0-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pykdeextensions/libpythonize0_0.4.0-4ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager-kde_0.33.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager-kde_0.33.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-installer_2.1.3ubuntu17.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-installer_2.1.3ubuntu17.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-updater_2.1.3ubuntu17.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-updater_2.1.3ubuntu17.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-notifier_2.1.3ubuntu17.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept-notifier_2.1.3ubuntu17.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept_2.1.3ubuntu17.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/adept/adept_2.1.3ubuntu17.1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libktnef1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libktnef1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkdepim1a_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkdepim1a_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkcal2b_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkcal2b_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.6-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.6-1ubuntu2.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.0-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.0-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.0-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.0-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.4-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.4-2ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.7-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.7-1ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.7-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.7-0ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.6.36-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.6.36-1ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.6.36-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.6.36-1ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby-defaults/ruby_1.8.2-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby-defaults/ruby_1.8.2-1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus-qt3/libdbus-qt-1-1c2_0.62.git.20060814-2build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus-qt3/libdbus-qt-1-1c2_0.62.git.20060814-2build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/libkonq4_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/libkonq4_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdesktop_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdesktop_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-kio-plugins_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-kio-plugins_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libifp/libifp4_1.0.0.2-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libifp/libifp4_1.0.0.2-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.45-1ubuntu3.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnjb/libnjb5_2.2.5-4.1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnjb/libnjb5_2.2.5-4.1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq5_8.2.7-0ubuntu0.7.10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq5_8.2.7-0ubuntu0.7.10_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fftw3/fftw3_3.1.2-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fftw3/fftw3_3.1.2-2ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libo/libofa/libofa0_0.9.3-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libo/libofa/libofa0_0.9.3-2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp5_0.5.3-4ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp5_0.5.3-4ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.7-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.7-0ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.3.2-0ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.3.2-0ubuntu3.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.3.2-0ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.3.2-0ubuntu3.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4_4.3-2ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4_4.3-2ubuntu7.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-qt_0.98_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-qt_0.98_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/arts_1.5.8-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/arts_1.5.8-0ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/libexiv2-0_0.15-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/libexiv2-0_0.15-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libkdcraw/libkdcraw1_0.1.1-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libkdcraw/libkdcraw1_0.1.1-2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libkexiv2/libkexiv2-1_0.1.5-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libkexiv2/libkexiv2-1_0.1.5-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libkipi/libkipi0_0.1.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libkipi/libkipi0_0.1.5-2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/digikam/digikam_0.9.2-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/digikam/digikam_0.9.2-2ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dolphin/dolphin_0.9.2-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dolphin/dolphin_0.9.2-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/enscript/enscript_1.6.4-11build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/enscript/enscript_1.6.4-11build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/ijs/libijs-0.35_0.35-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/ijs/libijs-0.35_0.35-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/ijsgutenprint_5.0.1-0ubuntu8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/ijsgutenprint_5.0.1-0ubuntu8_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/foomatic-db-gutenprint_5.0.1-0ubuntu8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/foomatic-db-gutenprint_5.0.1-0ubuntu8_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi-kde_0.3.2ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi-kde_0.3.2ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pth/libpth20_2.0.7-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pth/libpth20_2.0.7-8_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gnupg-agent_2.0.4-1ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gnupg-agent_2.0.4-1ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libksba/libksba8_1.0.1-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libk/libksba/libksba8_1.0.1-2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gpgsm_2.0.4-1ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnupg2/gpgsm_2.0.4-1ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.18.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.18.3-0ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.18.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.18.3-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk-qt-engine/gtk-qt-engine_0.8~svn-rev36-2ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk-qt-engine/gtk-qt-engine_0.8~svn-rev36-2ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwenview/gwenview_1.4.1-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwenview/gwenview_1.4.1-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-gui_2.7.7.dfsg.1-0ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-gui_2.7.7.dfsg.1-0ubuntu5_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-kde_0.6.11.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-kde_0.6.11.1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac++6_1.1.4-3ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac++6_1.1.4-3ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b2_1.0.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b2_1.0.3-0ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.3-0ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gpgme1.0/libgpgme11_1.1.5-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gpgme1.0/libgpgme11_1.1.5-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkleopatra1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkleopatra1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kaddressbook_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kaddressbook_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine-xine_0.8.5-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine-xine_0.8.5-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine_0.8.5-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine_0.8.5-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kamera_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kamera_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/karm_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/karm_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/katapult/katapult_0.3.2.1-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/katapult/katapult_0.3.2.1-2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kate_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kate_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kbstate_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kbstate_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-data_3.5.8-0ubuntu2.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-data_3.5.8-0ubuntu2.2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kicker_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kicker_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kcontrol_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kcontrol_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kcron_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kcron_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pykdeextensions/pykdeextensions_0.4.0-4ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pykdeextensions/pykdeextensions_0.4.0-4ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-guidance/kde-guidance_0.8.0svn20070928-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-guidance/kde-guidance_0.8.0svn20070928-0ubuntu7_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-guidance/kde-guidance-powermanager_0.8.0svn20070928-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-guidance/kde-guidance-powermanager_0.8.0svn20070928-0ubuntu7_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kde-icons-mono_3.5.8-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kde-icons-mono_3.5.8-0ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kwin_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kwin_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-style-polyester/kde-style-polyester_1.0.1-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-style-polyester/kde-style-polyester_1.0.1-1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-systemsettings/kde-systemsettings_0.0svn20070312-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-systemsettings/kde-systemsettings_0.0svn20070312-0ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kdeadmin-kfile-plugins_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/kdeadmin-kfile-plugins_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libo/libopenobex/libopenobex1_1.3-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libo/libopenobex/libopenobex1_1.3-3ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/libkbluetooth0_1.0~beta8-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/libkbluetooth0_1.0~beta8-0ubuntu5_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4-dbus_4.3-2ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4-dbus_4.3-2ubuntu7.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/kdebluetooth_1.0~beta8-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/kdebluetooth_1.0~beta8-0ubuntu5_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-qt2_0.6-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-qt2_0.6-0ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kdegraphics-kfile-plugins_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kdegraphics-kfile-plugins_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kfile-plugins_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kfile-plugins_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/libkcddb1_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/libkcddb1_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kio-plugins_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kio-plugins_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-suid_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-suid_5.8.8-7ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-filesharing_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-filesharing_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-kfile-plugins_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdenetwork-kfile-plugins_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdepasswd_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdepasswd_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kresources_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kresources_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkmime2_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkmime2_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kio-plugins_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-kio-plugins_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkpimidentities1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkpimidentities1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-wizards_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kdepim-wizards_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poster/poster_19990428-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poster/poster_19990428-8_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-24build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-24build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdeprint_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdeprint_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdesudo/kdesudo_1.1-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdesudo/kdesudo_1.1-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdm_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdm_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdnssd_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kdnssd_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libr/librsync/librsync1_0.9.7-1build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libr/librsync/librsync1_0.9.7-1build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rdiff-backup/rdiff-backup_1.1.14-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rdiff-backup/rdiff-backup_1.1.14-1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/keep/keep_0.4.0-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/keep/keep_0.4.0-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kghostview_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kghostview_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/khelpcenter_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/khelpcenter_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kio-apt/kio-apt_0.13.2-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kio-apt/kio-apt_0.13.2-2ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kio-locate/kio-locate_0.4.5-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kio-locate/kio-locate_0.4.5-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kio-umountwrapper/kio-umountwrapper_0.2-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kio-umountwrapper/kio-umountwrapper_0.2-0ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-5_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.3.0.0debian1-4build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.3.0.0debian1-4build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kipi-plugins/kipi-plugins_0.1.4-1build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kipi-plugins/kipi-plugins_0.1.4-1build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/klipper_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/klipper_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmag_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmag_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libksieve0_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libksieve0_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libmimelib1c2a_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libmimelib1c2a_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pinentry/pinentry-qt_0.7.3-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pinentry/pinentry-qt_0.7.3-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmail_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmail_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kmenuedit_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kmenuedit_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kmilo_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kmilo_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kmix_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kmix_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmousetool_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaccessibility/kmousetool_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kmplayer/kmplayer-base_0.9.4a-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kmplayer/kmplayer-base_0.9.4a-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kmplayer/kmplayer-konq-plugins_0.9.4a-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kmplayer/kmplayer-konq-plugins_0.9.4a-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/knetworkconf_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeadmin/knetworkconf_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/knotes_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/knotes_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg-progs_6b-14_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg-progs_6b-14_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaddons/konq-plugins_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeaddons/konq-plugins_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror-nsplugins_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konqueror-nsplugins_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkpimexchange1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkpimexchange1_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/korganizer_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/korganizer_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kontact_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kontact_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/konversation/konversation_1.0.1-4ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/konversation/konversation_1.0.1-4ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libkscan1_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libkscan1_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kooka_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kooka_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kpdf_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kpdf_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kpf_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kpf_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kppp_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kppp_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krdc_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krdc_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krfb_3.5.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krfb_3.5.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kscreensaver_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kscreensaver_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksmserver_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksmserver_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/ksnapshot_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/ksnapshot_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksplash_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksplash_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/ksplash-engine-moodin/ksplash-engine-moodin_0.4.2-1ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/ksplash-engine-moodin/ksplash-engine-moodin_0.4.2-1ubuntu5_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/ksvg_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/ksvg_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksysguardd_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksysguardd_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksysguard_3.5.8-0ubuntu2.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/ksysguard_3.5.8-0ubuntu2.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/ksystemlog/ksystemlog_0.3.2-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/ksystemlog/ksystemlog_0.3.2-1ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gmp/libgmp3c2_4.2.1+dfsg-5ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.2.1-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.2.1-0ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-default-settings/kubuntu-artwork-usplash_7.10-28_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-default-settings/kubuntu-artwork-usplash_7.10-28_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kwin-style-crystal/kwin-style-crystal_1.0.2-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kwin-style-crystal/kwin-style-crystal_1.0.2-1ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-default-settings/kubuntu-default-settings_7.10-28_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-default-settings/kubuntu-default-settings_7.10-28_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-qt_0.2.9_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-qt_0.2.9_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-5_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/akode/libakode2_2.0.2-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/akode/libakode2_2.0.2-2ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/libarts1-akode_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/libarts1-akode_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebindings/libsmokeqt1_3.5.7-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebindings/libsmokeqt1_3.5.7-1ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libq/libqt-perl/libqt-perl_3.008-2build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libq/libqt-perl/libqt-perl_3.008-2build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qca-tls/qca-tls_1.0-3build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qca-tls/qca-tls_1.0-3build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-kde_0.60_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-kde_0.60_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.1.1-13ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.1.1-13ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-meta/kubuntu-desktop_1.59_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-meta/kubuntu-desktop_1.59_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-docs/kubuntu-docs_7.10-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-docs/kubuntu-docs_7.10-5_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-konqueror-shortcuts/kubuntu-konqueror-shortcuts_0.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-konqueror-shortcuts/kubuntu-konqueror-shortcuts_0.4_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kvkbd/kvkbd_0.4.5-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kvkbd/kvkbd_0.4.5-0ubuntu3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kwalletmanager_3.5.8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kwalletmanager_3.5.8-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0_0.9.16a-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0_0.9.16a-2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libcluceneindex0_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libcluceneindex0_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libsearchclient0_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libsearchclient0_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/skim/libskim0_1.4.5-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/skim/libskim0_1.4.5-2ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstrigihtmlgui0_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstrigihtmlgui0_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/networkstatus_3.5.7enterprise20070926-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/networkstatus_3.5.7enterprise20070926-0ubuntu2.1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/knetworkmanager/network-manager-kde_0.2ubuntu1-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/knetworkmanager/network-manager-kde_0.2ubuntu1-0ubuntu5_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-crystal_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-crystal_2.3.0-1ubuntu5.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-kde_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-kde_2.3.0-1ubuntu5.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/skim/skim_1.4.5-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/skim/skim_1.4.5-2ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim-qtimm/scim-qtimm_0.9.4-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/scim-qtimm/scim-qtimm_0.9.4-2ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/speedcrunch/speedcrunch_0.8-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/speedcrunch/speedcrunch_0.8-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigiapplet/strigi-applet_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigiapplet/strigi-applet_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/strigi-daemon_0.5.6-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/strigi-daemon_0.5.6-0ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-arphic-ukai/ttf-arphic-ukai_0.1.20060928-2.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-arphic-ukai/ttf-arphic-ukai_0.1.20060928-2.2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mpg@Linux:~$ 


---

