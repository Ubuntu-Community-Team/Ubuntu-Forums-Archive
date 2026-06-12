---
title: "Unable to upgrade from 8.10 to 9.04"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by DThurman on 2009-12-23
I have seemingly been able to upgrade from 8.04 to 8.10
but I am unable to upgrade from 8.10 to 9.04 and plan to
keep upgrading to the latest releases.

When I select 9.04 for upgrading, it says that it is
unable to `calculate the changes', pops up a message
that says:

'
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
'

and then it quits.

I looked at two files:

Main.log:
======================================================================
2009-12-23 08:03:11,383 INFO Using config files '['./DistUpgrade.cfg']'
2009-12-23 08:03:11,384 INFO release-upgrader version '0.111.8' started
2009-12-23 08:03:11,663 DEBUG svg pixbuf loader failed (Error displaying image)
2009-12-23 08:03:11,791 DEBUG Using 'DistUpgradeViewGtk' view
2009-12-23 08:03:11,831 DEBUG aufsOptionsAndEnvironmentSetup()
2009-12-23 08:03:11,832 DEBUG using '/tmp/upgrade-rw-ldjgXH' as aufs_rw_dir
2009-12-23 08:03:11,832 DEBUG using '/tmp/upgrade-chroot-J-jU6b' as aufs chroot dir
2009-12-23 08:03:11,832 DEBUG enable dpkg --force-overwrite
2009-12-23 08:03:11,891 DEBUG lsb-release: 'intrepid'
2009-12-23 08:03:11,895 DEBUG who -m --ips: ''
2009-12-23 08:03:11,895 DEBUG _pythonSymlinkCheck run
2009-12-23 08:03:11,895 DEBUG openCache()
2009-12-23 08:03:12,775 DEBUG /openCache()
2009-12-23 08:03:12,775 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2009-12-23 08:03:12,775 DEBUG checkViewDepends()
2009-12-23 08:03:12,775 DEBUG running doUpdate() (showErrors=False)
2009-12-23 08:03:14,415 DEBUG openCache()
2009-12-23 08:03:15,492 DEBUG /openCache()
2009-12-23 08:03:15,492 DEBUG doPostInitialUpdate
2009-12-23 08:03:15,492 DEBUG Plugin modules in ./plugins: deb_plugin.py remove_lilo_plugin.py langpack_manual_plugin.py dpkg_status_plugin.py kdelibs4to5_plugin.py
2009-12-23 08:03:15,492 DEBUG Loading module ./plugins/deb_plugin.py
2009-12-23 08:03:15,493 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2009-12-23 08:03:15,493 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2009-12-23 08:03:15,494 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2009-12-23 08:03:15,494 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2009-12-23 08:03:15,495 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2009-12-23 08:03:15,495 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2009-12-23 08:03:15,496 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2009-12-23 08:03:15,496 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2009-12-23 08:03:15,497 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2009-12-23 08:03:15,497 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2009-12-23 08:03:15,497 DEBUG plugins for condition 'jauntyPostInitialUpdate' are '[]'
2009-12-23 08:03:15,497 DEBUG plugins for condition 'from_intrepidPostInitialUpdate' are '[]'
2009-12-23 08:03:15,497 DEBUG quirks: running jauntyPostInitialUpdate
2009-12-23 08:03:15,497 DEBUG running jauntyPostInitialUpdate
2009-12-23 08:03:18,204 DEBUG Foreign: 
2009-12-23 08:03:18,204 DEBUG Obsolete: linux-headers-2.6.24-21-generic keurocalc-kde4-data linuxtrade kbattleship-kde4 libdns32 kpilot libswscale1d libavcodec1d kghostview libexiv2-2 libassa3.4-0 kinfocenter-kde4 libpostproc1d kdegames-mahjongg-data-kde4 kdiff3 libtotem-plparser10 ksig kppp-kde4 kviewshell kiten-kde4 libisc32 libisc35 libkscan1 ksmiletris kreversi-kde4 kapptemplate-kde4 libgnutls13 kregexpeditor ktuberling-kde4 boson kfaxview libpigment0.3-4 kview ksnake kjots-kde4 kdelirc kbruch-kde4 sweeper-kde4 gnustep-back0.12-art libdjvulibre15 kconfigure linux-headers-2.6.24-22-generic authtool-gtk ksysv libguichan2 kpackage-kde4 libparted1.7-1 kayak libgnustep-base1.14 kdf-kde4 kenolaba kruler-kde4 kwin4 kolf-kde4 libmapnik1d keurocalc-kde4 kwin-kde4 artsbuilder kasteroids opera libavformat1d linux-ubuntu-modules-2.6.24-22-generic linux-ubuntu-modules-2.6.24-19-generic libetpan11 ksudoku-kde4 kuiviewer-kde4 libccrtp1-1.6-0 libkdepim1a kcharselect-kde4 linux-restricted-modules-2.6.24-21-generic libkleopatra1 hwdb-client-kde libmtp7 ksayit lingoteach-ui kalgebra-kde4 gnustep-back0.12 libkmime2 libnb-java1-java firefox-2 libnb-ide8-java klatin gfa kiriki-kde4 parallels reportbug-ng ksokoban vipec juk-kde4 starfighter libgnome-desktop-2 libmimelib1c2a authtool libkcddb4-kde4 libcamel1.2-11 libhdf5-serial-1.6.5-0 umbrello-kde4 libkdegames4-kde4 bovo-kde4 libisccc30 kcachegrind-kde4 parallels-modules-2.6.24-19-generic kompare-kde4 hwdb-client-common libzrtpcpp-0.9.2deb0 kbackgammon schafkopf libopenexr2ldbl libksieve0 kwordquiz-kde4 libgnomecupsui1.0-1c2a kmilo-kde4 libkdeedu4-kde4 ksquares-kde4 knetwalk-kde4 kdict kanagram-kde4 kfouleggs kbabel libpoppler-qt4-2 libwfut-0.1-0 libgpmg1 kig-kde4 kfourinline-kde4 libwebkitgtk1d libkcal2b khexedit libmono-mozilla0.1-cil klines-kde4 libx264-57 libbluetooth2 kwikdisk-kde4 lphoto libntfs-3g23 libdns35 liblwres30 parley-data-kde4 kmines-kde4 libcvsservice0 boson-data libedataserver1.2-9 klickety kgoldrunner-kde4 khalkhi-data pimppa neutrino liblingoteach4 kpoker libkhalkhi0 4digits o3read fglrx-control katomic-kde4 kmid kooka dhcdbd librss1 kverbos libkonq4 libopenal0a kblackbox-kde4 libkdegames1 katapult strigi-applet khalkhi-cards libisccfg30 ksirc networkstatus ktimer-kde4 kpdf linux-headers-2.6.24-22 kfloppy-kde4 kbounce-kde4 linux-headers-2.6.24-21 kgpg-kde4 kcolorchooser-kde4 libpoppler2 kandy kturtle-kde4 falconseye-data kdat libkiten4-kde4 atlantik parallels-modules libxerces27 linux-image-2.6.24-21-generic kwifimanager libhunspell-1.1-0 gcc-3.3-base libopencdk10 kaboodle kmahjongg-kde4 libltdl3 canoe kdeedu-data keduca starfighter-data hwdb-client-gnome kpercentage-kde4 kdepim-kio-plugins krec kcalc-kde4 libnb-platform7-java cervisia-kde4 libbind9-30 firefox-themes-ubuntu kpager falconseye libosip2-2 videomanager linux-ubuntu-modules-2.6.24-21-generic kvoctrain khangman-kde4 konquest-kde4 kjumpingcube-kde4 libxml++2.6c2a lib3ds-1.2 libavutil1d libvlc0 kshisen-kde4 kscd-kde4 ksirtet qgrubeditor linux-image-2.6.24-19-generic libkpimexchange1 bluez-audio linux-restricted-modules-2.6.24-19-generic libgucharmap6 libkcddb1 atlantikdesigner libkpimidentities1 libyaz2 libkbluetooth0 libgnustep-gui0.12 ktron linux-restricted-modules-2.6.24-22-generic upstreamdev db2exc zdesktop kbugbuster-kde4 noatun libfile-temp-perl kspaceduel-kde4 kcron-kde4 libpoppler-glib2 codeine knetworkconf-kde4 kitchensync linux-image-2.6.24-22-generic libktnef1 ksame-kde4 libsmbios1 blinken-kde4 kmplot-kde4 ktouch-kde4 kdeprint libopenbabel2 libkdeedu3
2009-12-23 08:03:18,205 DEBUG updateSourcesList()
2009-12-23 08:03:18,248 DEBUG rewriteSourcesList()
2009-12-23 08:03:18,250 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted'
2009-12-23 08:03:18,250 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted' updated to new dist
2009-12-23 08:03:18,250 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted'
2009-12-23 08:03:18,250 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted' updated to new dist
2009-12-23 08:03:18,250 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted'
2009-12-23 08:03:18,250 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted' updated to new dist
2009-12-23 08:03:18,251 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted'
2009-12-23 08:03:18,251 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted' updated to new dist
2009-12-23 08:03:18,251 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe'
2009-12-23 08:03:18,251 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe' updated to new dist
2009-12-23 08:03:18,251 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe'
2009-12-23 08:03:18,251 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe' updated to new dist
2009-12-23 08:03:18,251 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe'
2009-12-23 08:03:18,251 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe' updated to new dist
2009-12-23 08:03:18,251 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe'
2009-12-23 08:03:18,251 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe' updated to new dist
2009-12-23 08:03:18,252 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse'
2009-12-23 08:03:18,252 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse' updated to new dist
2009-12-23 08:03:18,252 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse'
2009-12-23 08:03:18,252 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse' updated to new dist
2009-12-23 08:03:18,252 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse'
2009-12-23 08:03:18,252 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse' updated to new dist
2009-12-23 08:03:18,252 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse'
2009-12-23 08:03:18,252 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse' updated to new dist
2009-12-23 08:03:18,252 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted'
2009-12-23 08:03:18,252 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted' updated to new dist
2009-12-23 08:03:18,253 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted'
2009-12-23 08:03:18,253 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted' updated to new dist
2009-12-23 08:03:18,253 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe'
2009-12-23 08:03:18,253 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe' updated to new dist
2009-12-23 08:03:18,253 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe'
2009-12-23 08:03:18,253 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe' updated to new dist
2009-12-23 08:03:18,253 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse'
2009-12-23 08:03:18,253 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse' updated to new dist
2009-12-23 08:03:18,253 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse'
2009-12-23 08:03:18,253 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse' updated to new dist
2009-12-23 08:03:18,253 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner'
2009-12-23 08:03:18,254 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner' updated to new dist
2009-12-23 08:03:18,254 INFO fixing components inconsistency from 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted'
2009-12-23 08:03:18,254 INFO to new entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted'
2009-12-23 08:03:18,254 INFO fixing components inconsistency from 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted'
2009-12-23 08:03:18,254 INFO to new entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted'
2009-12-23 08:03:18,260 DEBUG running doUpdate() (showErrors=True)
2009-12-23 08:03:59,220 DEBUG openCache()
2009-12-23 08:04:02,140 DEBUG /openCache()
2009-12-23 08:04:57,888 DEBUG Running KeepInstalledSection rules
2009-12-23 08:04:57,952 DEBUG Kernel uname: '2.6.27-16-generic' 
2009-12-23 08:04:57,961 DEBUG nvidiaUpdate()
2009-12-23 08:04:57,987 INFO no old nvidia driver installed, installing no new
2009-12-23 08:04:57,987 DEBUG Installing 'dontzap' (kubuntu-desktop PostUpgradeInstall rule)
2009-12-23 08:04:58,386 DEBUG Upgrading 'brasero' (Distro PostUpgradeUpgrade rule)
2009-12-23 08:04:58,752 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2009-12-23 08:04:58,753 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2009-12-23 08:04:59,118 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2009-12-23 08:04:59,483 DEBUG Removing 'powermanagement-interface' (ubuntu-desktop PostUpgradeRemove rule)
2009-12-23 08:04:59,852 DEBUG Removing 'powermanagement-interface' (kubuntu-desktop PostUpgradeRemove rule)
2009-12-23 08:05:00,219 DEBUG Removing 'guidance-power-manager' (kubuntu-desktop PostUpgradeRemove rule)
2009-12-23 08:05:00,585 DEBUG Removing 'kde-guidance-powermanager' (kubuntu-desktop PostUpgradeRemove rule)
2009-12-23 08:05:00,953 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2009-12-23 08:05:00,954 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2009-12-23 08:05:00,954 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2009-12-23 08:05:01,333 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2009-12-23 08:05:01,710 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2009-12-23 08:05:01,711 DEBUG plugins for condition 'PostDistUpgradeCache' are '[]'
2009-12-23 08:05:01,711 DEBUG plugins for condition 'jauntyPostDistUpgradeCache' are '[<remove_lilo_plugin.RemoveLiloPlugin object at 0xd639dec>]'
2009-12-23 08:05:01,711 DEBUG running quirks plugin <remove_lilo_plugin.RemoveLiloPlugin object at 0xd639dec>
2009-12-23 08:05:01,711 DEBUG plugins for condition 'from_intrepidPostDistUpgradeCache' are '[]'
2009-12-23 08:05:01,712 DEBUG quirks: running jauntyPostDistUpgradeCache
2009-12-23 08:05:01,712 DEBUG running jauntyPostDistUpgradeCache
2009-12-23 08:05:01,712 DEBUG forcing 'gwenview' upgrade
2009-12-23 08:05:47,222 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2009-12-23 08:05:47,223 DEBUG openCache()
2009-12-23 08:05:47,801 DEBUG /openCache()
======================================================================

term.log (0 length file)


What do I need to do?

Thanks!

---

### Post by DThurman on 2009-12-23
[SOLVED]

Never mind!

I solved it: I removed: gwenview!
Sorry for posting this message!

---

### Post by DThurman on 2009-12-23
Ok... we'll see if upgrades to 9.10 works...

=================================================
[SOLVED]:
1) apt-get autoremove
2) Software Updates->Install updates
   geez... 3501 files to update!
-------------------------------------------------
The UPDATE WORKED.... however....

I am still trying to figure out why updates
fail to calculate again....  seems to happen
often after an upgrade....

This is the error message:
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

How to fix this???




=================================================
[SOLVED]
I guess I have GOT to stop freaking out ;)

Solution is to remove the fglrx driver:
sudo apt-get remove xorg-driver-fglrx
-------------------------------------------------
Gah!

Unfortunately, the upgrade from 8.10 to 9.04 has a
problem...  it boots but... the graphics screen is
a bit messed up! Note that 8.10 graphics worked perfectly.

What was added (somehow) was this `fglrx' - how can I
get a SANE xorg screen or better yet - how can I remove
this fglrx driver?  Is this an NVida thing - my system
is an Intel graphics 945 chipset...

I tried "nomodeset" in the boot-kernel line - no go....
is there something I could add for a "fail-safe" mode to
the boot-kernel line?

Thanks!
=======================================================

---

