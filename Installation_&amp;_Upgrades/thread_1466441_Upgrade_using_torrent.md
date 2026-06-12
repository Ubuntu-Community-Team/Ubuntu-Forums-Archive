---
title: "Upgrade using torrent?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Defrector on 2010-04-30
Is it possible to upgrade 9.10->10.04 by downloading a .tar.gz via torrent and invoking ubuntu to upgrade using the downloaded file?

I am in the download step of a dist upgrade and it seems to be choking a little bandwidth-wise (most likely not on my end.)

---

### Post by RobertSwipe on 2010-04-30
Be careful if you're downloading the Alternate ISO - see my earlier post "Beware upgrading to 10.04 from i386 Alternate CD".

---

### Post by Defrector on 2010-04-30
Thanks for the heads-up; I looked at your thread and am definitely not going to try booting off the CD to upgrade.

I am using 
```
update-manager -d
```

... to upgrade. The choppy downloading bandwidth in its upgrading process made me wonder if I could download a torrent with the most relevant packages, tell the updater to use those downloaded packages and then it would download any remaining extras which might not be on the torrent in the old fashioned way.

The thought of how many people might be downloading from ubuntu/mirrors for upgrading kind of amazes me, with this being a ~1.7GB download, according to the upgrade app.

---

### Post by RobertSwipe on 2010-04-30
The upgrade ISO is around 660Mb, and roughly the same for the install CD.

I used the torrent download, but had to burn this to a CD as the instructions on the Ubuntu site for mounting the ISO directly were incorrect. (One line reads "cdrom0" and another reads "cdrom". When I tried this it simply got confused with my real CDRom and I had to reboot. So I burnt a CD and avoided the problem.)

I know these issues are fairly minor on the general scheme of things, but they do make it a more tiresome experience.

Worth it in the end though!

---

### Post by Defrector on 2010-04-30
I downloaded the ISO torrent (very quickly) and ran the upgrade script from the ISO mounted. It was a lot farther along than originally. 

Even when asserting not to use the network it insists on downloading 167MB of packages. When this happens things go very slowly and it eventually gives up, stating "Could not download the upgrades"
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9~rc2-0ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/u/unison/unison_2.27.57-2ubuntu2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/u/unison/unison-gtk_2.27.57-2ubuntu2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-21_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kubuntu-notification-helper/update-notifier-kde_10.04ubuntu4_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-qt_3.1.6-dfsg-2ubuntu2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose_3.1.6-dfsg-2ubuntu2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-source_3.1.6-dfsg-2ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-dkms_3.1.6-dfsg-2ubuntu2_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.2.0-6build1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/whois/whois_5.0.0ubuntu3_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxmaxima/wxmaxima_0.8.4-1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-gme_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-id3v2_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-alsa_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-mad_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-sid_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-vorbis_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-pulse_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-plugin-modplug_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-core_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-icon_0.7DrNo-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2_0.7DrNo-4ubuntu1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xmms2/xmms2-client-nycli_0.7DrNo-4ubuntu1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_5.10-3ubuntu4_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-gl_5.10-3ubuntu4_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xscreensaver/xscreensaver-gl-extra_5.10-3ubuntu4_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xutils-dev/xutils-dev_7.5+2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/c/create-resources/create-resources_0.1.3-2.1build1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fastjar/fastjar_0.98-1build1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde-style-qtcurve/kde-style-qtcurve_1.0.2-1ubuntu2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/konq-plugins/konq-plugins-l10n_4.4.0-0ubuntu5_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/konq-plugins/konqueror-plugins_4.4.0-0ubuntu5_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/multipath-tools/kpartx_0.4.8-14ubuntu4_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.6-0ubuntu4_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.11.753-1_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc3+svn20090426-1ubuntu16_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mesa/mesa-utils_7.7.1-1ubuntu2_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nmap/nmap_5.00-3_amd64.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/p/phpmyadmin/phpmyadmin_3.3.2-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-jsmath/ttf-jsmath_0.090709-1_all.deb Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.15 80]
```
This happens repeatedly aborting, though progressing a little each time. From what I've read, the official DVDs just have extra languages. Is there a "kitchen sink" DVD image/tar.gz out there available as a torrent with more packages available?

---

