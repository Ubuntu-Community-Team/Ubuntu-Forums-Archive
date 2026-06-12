---
title: "cdrom upgrade from 8.04 to 10.04 problem"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Huntz23 on 2010-10-29
I am upgrading to lucid from hardy and I run the command
> kdesudo "sh /cdrom/cdromupgrade"

it starts but when it get to removal of update-manager it hangs telling me that it is marked for removal but is on the blacklist  because of:

* Upgrading to a pre-release version of Ubuntu

* Running the current pre-release version of Ubuntu

* Unofficial software packages not provided by Ubuntu

So is it a bug or am I overlooking something?  any help would be appreciated.

here is my main.log
> 2010-10-29 09:55:37,501 INFO Using config files '['./DistUpgrade.cfg.hardy']'
2010-10-29 09:55:37,502 INFO uname information: 'Linux livingrm 2.6.24-27-generic #1 SMP Fri Mar 12 01:10:31 UTC 2010 i686'
2010-10-29 09:55:37,503 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-10-29 09:55:38,074 INFO release-upgrader version '0.134.7' started
2010-10-29 09:55:39,076 DEBUG svg pixbuf loader failed (Error displaying image)
2010-10-29 09:55:39,077 ERROR html widget
Traceback (most recent call last):
  File "/tmp/tmp.pRCAty6943/DistUpgradeViewGtk.py", line 404, in __init__
    import webkit
ImportError: No module named webkit
2010-10-29 09:55:39,083 DEBUG Using 'DistUpgradeViewGtk' view
2010-10-29 09:55:39,221 DEBUG aufsOptionsAndEnvironmentSetup()
2010-10-29 09:55:39,223 DEBUG using '/tmp/upgrade-rw-K5qtk8' as aufs_rw_dir
2010-10-29 09:55:39,224 DEBUG using '/tmp/upgrade-chroot-Kdune4' as aufs chroot dir
2010-10-29 09:55:39,225 DEBUG enable dpkg --force-overwrite
2010-10-29 09:55:39,580 DEBUG lsb-release: 'hardy'
2010-10-29 09:55:39,590 DEBUG who -m --ips: ''
2010-10-29 09:55:39,592 DEBUG _pythonSymlinkCheck run
2010-10-29 09:55:39,594 DEBUG openCache()
2010-10-29 09:55:46,781 DEBUG /openCache(), new cache size 25580
2010-10-29 09:55:46,782 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'kubuntu-desktop')
2010-10-29 09:55:46,783 DEBUG checkViewDepends()
2010-10-29 09:55:49,228 DEBUG useNetwork: 'False' (selected by user)
2010-10-29 09:55:49,229 DEBUG running doUpdate() (showErrors=False)
2010-10-29 09:55:49,229 DEBUG doUpdate() will not use the network because self.useNetwork==false
2010-10-29 09:55:49,230 DEBUG openCache()
2010-10-29 09:55:57,151 DEBUG /openCache(), new cache size 25580
2010-10-29 09:55:57,151 DEBUG doPostInitialUpdate
2010-10-29 09:55:57,152 DEBUG Plugin modules in ./plugins: remove_lilo_plugin.py kdelibs4to5_plugin.py langpack_manual_plugin.py deb_plugin.py dpkg_status_plugin.py
2010-10-29 09:55:57,153 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2010-10-29 09:55:57,156 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2010-10-29 09:55:57,157 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2010-10-29 09:55:57,160 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2010-10-29 09:55:57,160 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2010-10-29 09:55:57,173 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2010-10-29 09:55:57,173 DEBUG Loading module ./plugins/deb_plugin.py
2010-10-29 09:55:57,175 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2010-10-29 09:55:57,176 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2010-10-29 09:55:57,180 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2010-10-29 09:55:57,180 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2010-10-29 09:55:57,181 DEBUG plugins for condition 'lucidPostInitialUpdate' are '[]'
2010-10-29 09:55:57,181 DEBUG plugins for condition 'from_hardyPostInitialUpdate' are '[]'
2010-10-29 09:55:57,182 DEBUG quirks: running lucidPostInitialUpdate
2010-10-29 09:55:57,182 DEBUG running lucidPostInitialUpdate
2010-10-29 09:56:01,923 DEBUG Foreign: wine-gecko wine-dev medibuntu-keyring libamrnb3 amarok w32codecs libavformat1d libavcodec1d pidgin pidgin-data amarok-xine non-free-codecs libavutil1d mplayer libamrwb3 wine libpostproc1d libpurple0
2010-10-29 09:56:01,924 DEBUG Obsolete: libntfs-3g12 libmtp6 libuniconf4.3 libpci2 xgc libmagick++9c2a libopencdk8 libwvstreams4.3-extras libgsl0 ico libdevmapper1.02 libiw28 libisc11 beforelight cdrecord libjasper-1.701-1 adobe-flashplugin libkdcraw1 libsnmp10 libmagick9 libdns22 xf86dga mkisofs liboggflac3 libwvstreams4.3-base libpoppler1 libgpod2 libsnmp9 bitmap cnijfilter-common libpoppler1-qt libgcj7-0 libisccfg1 libisccc0 liblwres9 libwvstreams4.2-base libwvstreams4.2-extras libbind9-0 libflac7 libflac++5c2 libneon25 libbrlapi1 libldap2 bluez-pin
2010-10-29 09:56:01,927 DEBUG updateSourcesList()
2010-10-29 09:56:02,101 DEBUG rewriteSourcesList()
2010-10-29 09:56:02,102 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse'
2010-10-29 09:56:02,102 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse' updated to new dist
2010-10-29 09:56:02,103 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse'
2010-10-29 09:56:02,104 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse' updated to new dist
2010-10-29 09:56:02,104 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse'
2010-10-29 09:56:02,105 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse' updated to new dist
2010-10-29 09:56:02,105 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse'
2010-10-29 09:56:02,106 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse' updated to new dist
2010-10-29 09:56:02,106 DEBUG examining: 'deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron" deb #WineHQ - Ubuntu 8.04 "Hardy Heron"'
2010-10-29 09:56:02,117 DEBUG entry '# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) lucid main #WineHQ - Ubuntu 8.04 "Hardy Heron" deb #WineHQ - Ubuntu 8.04 "Hardy Heron" disabled on upgrade to lucid' was disabled (unknown mirror)
2010-10-29 09:56:02,118 DEBUG examining: 'deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free'
2010-10-29 09:56:02,129 DEBUG entry '# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid' was disabled (unknown mirror)
2010-10-29 09:56:02,129 DEBUG examining: 'deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) hardy main'
2010-10-29 09:56:02,141 DEBUG entry '# deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid main # disabled on upgrade to lucid' was disabled (unknown mirror)
2010-10-29 09:56:03,932 DEBUG AptCdrom.add() called with '/cdrom'
2010-10-29 09:56:04,021 INFO ignoring missing '/cdrom/dists/lucid/restricted/debian-installer/binary-i386/Packages'
2010-10-29 09:56:04,022 INFO ignoring missing '/cdrom/dists/lucid/restricted/binary-i386/Packages'
2010-10-29 09:56:04,025 INFO ignoring missing '/cdrom/dists/lucid/main/debian-installer/binary-i386/Packages'
2010-10-29 09:56:04,086 INFO ignoring missing '/cdrom/dists/lucid/main/binary-i386/Packages'
2010-10-29 09:56:04,175 DEBUG AptCdrom.add() returned: True
2010-10-29 09:56:04,175 DEBUG running doUpdate() (showErrors=True)
2010-10-29 09:56:04,176 DEBUG doUpdate() will not use the network because self.useNetwork==false
2010-10-29 09:56:04,177 DEBUG openCache()
2010-10-29 09:56:09,747 DEBUG /openCache(), new cache size 2115
2010-10-29 09:56:09,750 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'kubuntu-desktop')
2010-10-29 09:56:22,056 DEBUG Kernel uname: '2.6.24-27-generic' 
2010-10-29 09:56:22,142 DEBUG ./get_kernel_list.sh returns: ['linux-generic', 'linux-image-generic', 'linux-virtual', 'linux-image-virtual', 'linux-rt', 'linux-image-rt', 'linux-generic-pae', 'linux-image-generic-pae', 'linux-xen', 'linux-image-xen', 'linux-386', 'linux-image-386']
2010-10-29 09:56:22,142 DEBUG linux-image-generic kernel already installed
2010-10-29 09:56:22,143 DEBUG nvidiaUpdate()
2010-10-29 09:56:22,240 DEBUG Removing 'nvidia-glx-new-envy' (old nvidia driver)
2010-10-29 09:56:22,511 DEBUG nv.selectDriver() returned 'nvidia-173'
2010-10-29 09:56:22,512 WARNING no 'nvidia-173' found
2010-10-29 09:56:22,513 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2010-10-29 09:56:22,513 DEBUG Removing 'slocate' (Distro PostUpgradeRemove rule)
2010-10-29 09:56:22,786 DEBUG Removing 'gtk-qt-engine' (Distro PostUpgradeRemove rule)
2010-10-29 09:56:23,061 DEBUG Removing 'libparted1.8-12' (Distro PostUpgradeRemove rule)
2010-10-29 09:56:23,062 DEBUG Removing 'usplash' (Distro PostUpgradeRemove rule)
2010-10-29 09:56:23,335 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2010-10-29 09:56:23,607 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2010-10-29 09:56:23,879 DEBUG Purging 'linux-restricted-modules-common' (Distro PostUpgradePurge rule)
2010-10-29 09:56:24,152 DEBUG plugins for condition 'PostDistUpgradeCache' are '[]'
2010-10-29 09:56:24,153 DEBUG plugins for condition 'lucidPostDistUpgradeCache' are '[]'
2010-10-29 09:56:24,153 DEBUG plugins for condition 'from_hardyPostDistUpgradeCache' are '[<kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin object at 0xad2af4c>, <langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin object at 0xad300cc>]'
2010-10-29 09:56:24,154 DEBUG running quirks plugin <kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin object at 0xad2af4c>
2010-10-29 09:56:24,157 DEBUG running quirks plugin <langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin object at 0xad300cc>
2010-10-29 09:56:24,173 DEBUG quirks: running from_hardyPostDistUpgradeCache
2010-10-29 09:56:24,174 DEBUG running from_hardyPostDistUpgradeCache
2010-10-29 09:56:24,174 DEBUG _kernel386TransitionCheck
2010-10-29 09:56:24,175 DEBUG running _usesEvmsInMounts
2010-10-29 09:56:24,175 DEBUG checking for 'wl' module
2010-10-29 09:56:24,186 DEBUG language-support-translations-* transition
2010-10-29 09:56:24,206 DEBUG Installing 'ubuntu-minimal' (base meta package keep installed rule)
2010-10-29 09:56:25,438 DEBUG none of the '['ubuntu-desktop', 'kubuntu-desktop', 'edubuntu-desktop', 'xubuntu-desktop', 'ubuntustudio-desktop', 'ichthux-desktop', 'mythbuntu-desktop', 'kubuntu-kde4-desktop']' meta-pkgs installed
2010-10-29 09:56:25,439 DEBUG guessing 'kubuntu-desktop' as missing meta-pkg
2010-10-29 09:56:26,630 DEBUG markedInstall: 'kubuntu-desktop' -> '1'
2010-10-29 09:56:26,674 DEBUG blacklist expr 'update-manager' matches 'update-manager'
2010-10-29 09:56:26,674 DEBUG The package 'update-manager' is marked for removal but it's in the removal blacklist
2010-10-29 09:57:30,720 ERROR Dist-upgrade failed: 'The package 'update-manager' is marked for removal but it is in the removal blacklist.'
2010-10-29 09:57:30,721 DEBUG abort called
2010-10-29 09:57:30,726 DEBUG openCache()
2010-10-29 09:57:51,229 DEBUG /openCache(), new cache size 25580
2010-10-29 09:57:51,232 DEBUG enabling apt cron job


---

