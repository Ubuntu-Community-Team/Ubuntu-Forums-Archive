---
title: "Help upgrading from 7.10 to 8.04"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by rajkhand on 2008-04-28
I initially tried downloading the upgrade directly from the internet and it failed after downloading some 850 packages as the servers got choked. So based on some guide I download the the alternate CD image.
The downloaded iso was burned on a cd and mdm5sum was checked and verified to be correct.

I inserted the CD and when it was recognised as the upgrade CD I clicked un the upgrade. When getting the packeges in the 3rd step I get the following errors

Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-dbg_2.5.2-2ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-dbg_2.5.2-2ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/g/giflib/libungif4g_4.1.6-3_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/g/giflib/libungif4g_4.1.6-3_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/g/giflib/libgif4_4.1.6-3_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/g/giflib/libgif4_4.1.6-3_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc2-0ubuntu12_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc2-0ubuntu12_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-0ubuntu1_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-0ubuntu1_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.9-0ubuntu6_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.9-0ubuntu6_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.9-0ubuntu6_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.9-0ubuntu6_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.12-15.33_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.12-15.33_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_8.04+20080325_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_8.04+20080325_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en-base/language-pack-kde-en-base_8.04+20080325_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en-base/language-pack-kde-en-base_8.04+20080325_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-05-0ubuntu1_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-05-0ubuntu1_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-05-0ubuntu1_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-05-0ubuntu1_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.4.0-3ubuntu1_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.4.0-3ubuntu1_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-en-gb_2.0.0.7+1-0ubuntu3_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-en-gb_2.0.0.7+1-0ubuntu3_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-filter-mobiledev_2.4.0-3ubuntu1_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-filter-mobiledev_2.4.0-3ubuntu1_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.11.1-1ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.11.1-1ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.11.1-1ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.11.1-1ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/x/xine-lib/libxine1-ffmpeg_1.1.11.1-1ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/x/xine-lib/libxine1-ffmpeg_1.1.11.1-1ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.11.1-1ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.11.1-1ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.11.1-1ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.11.1-1ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/x/xine-lib/libxine1-plugins_1.1.11.1-1ubuntu2_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/x/xine-lib/libxine1-plugins_1.1.11.1-1ubuntu2_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.8-0ubuntu5_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.8-0ubuntu5_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.8-0ubuntu5_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.8-0ubuntu5_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/bittorrent_3.4.2-11ubuntu4_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/bittorrent_3.4.2-11ubuntu4_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/python-bittorrent_3.4.2-11ubuntu4_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/python-bittorrent_3.4.2-11ubuntu4_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc2-0ubuntu12_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc2-0ubuntu12_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration0_0.1.16_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration0_0.1.16_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu3_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu3_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin-kde3_3.5.9-0ubuntu6_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin-kde3_3.5.9-0ubuntu6_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin_3.5.9-0ubuntu6_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kdebase-bin_3.5.9-0ubuntu6_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.3.4-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.3.4-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/qt4-dev-tools_4.3.4-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/qt4-dev-tools_4.3.4-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.3.4-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.3.4-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.3.4-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.3.4-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.3.4-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.3.4-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.0.3~rc2-1ubuntu2_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.0.3~rc2-1ubuntu2_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_7.0.3~rc2-1ubuntu2_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_7.0.3~rc2-1ubuntu2_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-pkg-resources_0.6c8-0ubuntu1_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-pkg-resources_0.6c8-0ubuntu1_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c8-0ubuntu1_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c8-0ubuntu1_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/p/python-xml/python-xml_0.8.4-10ubuntu1_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/p/python-xml/python-xml_0.8.4-10ubuntu1_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-doc_4.3.4-0ubuntu2_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-doc_4.3.4-0ubuntu2_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/qt4-qtconfig_4.3.4-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/qt4-qtconfig_4.3.4-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.9.9-0ubuntu1_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/s/soundconverter/soundconverter_0.9.9-0ubuntu1_all.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu2_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu2_i386.deb) 404 Not Found [IP: 212.219.56.153 80]
Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibmesa-gl-dev_7.3+10ubuntu7_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibmesa-gl-dev_7.3+10ubuntu7_all.deb) 404 Not Found [IP: 212.219.56.153 80]


and the upgreade process stopped. If I remember correctly mplayer, qt4 were installed from source.

 I am about 2 months old using 7.10 and was quit happy with it.

Please help.

TIA

Raj

---

### Post by Jammin80503 on 2008-04-28
Looks to me like their server failed. Try again soon, its just loaded up with all the people upgrading.

---

### Post by rajkhand on 2008-04-28
I am able to go to this site from my browser so the problem is somewhere else. 

Please help

---

### Post by Peter09 on 2008-04-28
Can you do a normal upgrade over the internet now, perhaps the servers are not so busy?

PC

---

### Post by c4v3m4n on 2008-04-28
The servers are still probably busy.  I've been having the same problem also, just wait it out.

---

### Post by rajkhand on 2008-04-28
How it can be a server issue when I am doing the upgrade from the alternate cd?

---

### Post by Peter09 on 2008-04-28
Looks like it tried a internet upgrade from your post.

PC

---

### Post by pommattski on 2008-04-28
> **rajkhand said:**
> How it can be a server issue when I am doing the upgrade from the alternate cd?

The CD does not / cannot contain every package your system may need to complete the upgrade.
If you had installed any additional software into Gutsy from the repositories, it is very likely that the upgrades for these will need to to come from on-line repositories also.

---

