---
title: "Problem in upgrading from trusty to vivid"
date: 2015-06-08
forum: Installation &amp; Upgrades
---

### Post by jeyaa on 2015-06-08
I upgraded from trusty to vivid. For some reason kernel version which I get after upgrading is 3.13.x which is same that was in trusty. Due to this I suspect that my ethernet and wireless stopped working.
How can I upgrade my kernel version in vivid without internet.

Plz help me.

---

### Post by Bucky Ball on 2015-06-08
Welcome. Are you absolutely sure the upgrade worked and you are in fact using 15.04? I think you can check that out in System Monitor. 

Just out of curiosity, what persuaded you to upgrade to an interim release supported until January 2016 rather than sticking with an LTS which is supported until 2019?

Please open a terminal and run these commands, one after the other, hitting enter between each:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Please post back any and all errors between [code] tags (see last link in my signature). These commands will NOT upgrade your installed release to the next available release.

---

### Post by jeyaa on 2015-06-08
```

$ uname -a
Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


$ cat /etc/issue
Ubuntu 15.04 \n \l


$ sudo apt-get autoclean 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del libevolution 3.12.10-0ubuntu1~14.10.1 [2,098 kB]
Del firefox 38.0+build3-0ubuntu0.14.10.1 [38.8 MB]
Del libwayland-egl1-mesa 10.3.2-0ubuntu0.1 [6,666 B]
Del libgtk-3-bin 3.12.2-0ubuntu15.2 [18.4 kB]
Del apport 2.14.7-0ubuntu8.5 [184 kB]
Del openssl 1.0.1f-1ubuntu9.5 [492 kB]
Del libgtk-3-0 3.12.2-0ubuntu15.2 [2,071 kB]
Del libmodule-signature-perl 0.73-1ubuntu0.14.10.1 [24.3 kB]
Del libqt4-sql 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [100 kB]
Del libjfreechart-java 1.0.13-5 [1,378 kB]
Del qtcore4-l10n 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [619 kB]
Del libfop-java 1:1.1.dfsg-2ubuntu1 [9,587 kB]
Del account-plugin-jabber 3.8.6-0ubuntu13.1 [8,872 B]
Del postfix 2.11.1-1ubuntu1 [1,107 kB]
Del libgl1-mesa-dri 10.3.2-0ubuntu0.1 [4,089 kB]
Del uuid-runtime 2.25.1-3ubuntu4.1 [24.9 kB]
Del gir1.2-edataserver-1.2 3.12.10-0ubuntu1~14.10.1 [20.1 kB]
Del libqtdbus4 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [192 kB]
Del libuuid1 2.25.1-3ubuntu4.1 [15.2 kB]
Del libgtk-3-common 3.12.2-0ubuntu15.2 [173 kB]
Del evolution-data-server-online-accounts 3.12.10-0ubuntu1~14.10.1 [31.2 kB]
Del python-problem-report 2.14.7-0ubuntu8.5 [9,166 B]
Del libp11-kit-gnome-keyring 3.10.1-1ubuntu7.1 [41.2 kB]
Del xserver-xorg-video-intel 2:2.99.914-1~exp1ubuntu4.4 [693 kB]
Del libqt4-dbus 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [6,502 B]
Del evolution-data-server 3.12.10-0ubuntu1~14.10.1 [436 kB]
Del libmount1 2.25.1-3ubuntu4.1 [111 kB]
Del linux-firmware 1.138.1 [21.4 MB]
Del gvfs-daemons 1.20.2-1ubuntu3 [110 kB]
Del libqt4-sql 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [105 kB]
Del udev 208-8ubuntu8.2 [804 kB]
Del empathy 3.8.6-0ubuntu13.1 [578 kB]
Del python-apport 2.14.7-0ubuntu8.5 [75.5 kB]
Del libedataserver-1.2-18 3.12.10-0ubuntu1~14.10.1 [195 kB]
Del libqt4-script 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [870 kB]
Del unity-settings-daemon 14.04.0+14.10.20141014-0ubuntu1.1 [466 kB]
Del libqt4-sql-sqlite 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [23.5 kB]
Del libqt4-declarative 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,152 kB]
Del libqt4-network 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [594 kB]
Del thunderbird-globalmenu 1:31.7.0+build1-0ubuntu0.14.10.1 [8,286 B]
Del libmagick++5 8:6.7.7.10+dfsg-4ubuntu1 [104 kB]
Del gir1.2-gudev-1.0 1:208-8ubuntu8.2 [5,544 B]
Del ubuntu-session 3.9.90-0ubuntu16.1 [2,690 B]
Del libqtcore4 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,628 kB]
Del gvfs-backends 1.20.2-1ubuntu3 [276 kB]
Del libgdata19 0.16.1-1~ubuntu14.10.1 [238 kB]
Del mount 2.25.1-3ubuntu4.1 [117 kB]
Del firefox-globalmenu 38.0+build3-0ubuntu0.14.10.1 [8,388 B]
Del libqt5opengl5 5.3.0+dfsg-2ubuntu9.1 [130 kB]
Del libssl1.0.0 1.0.1f-1ubuntu9.5 [850 kB]
Del libqt5core5a 5.3.0+dfsg-2ubuntu9.1 [1,968 kB]
Del javahelp2 2.0.05.ds1-7 [886 kB]
Del texlive-omega 2014.20140717-01ubuntu1 [2,095 kB]
Del libblkid1 2.25.1-3ubuntu4.1 [104 kB]
Del libssl1.0.0 1.0.1f-1ubuntu9.5 [863 kB]
Del account-plugin-facebook 0.12+14.10.20140924-0ubuntu2 [2,906 B]
Del libsystemd-journal0 208-8ubuntu8.2 [53.8 kB]
Del libpolkit-backend-1-0 0.105-4ubuntu2.14.10.1 [35.7 kB]
Del libnb-org-openide-util-lookup-java 7.4+dfsg1-1 [76.9 kB]
Del keepass2 2.29+dfsg-1~ubuntu14.10~ppa1 [1,330 kB]
Del libqtcore4 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,569 kB]
Del poppler-utils 0.26.5-0ubuntu2 [126 kB]
Del libwhoopsie0 0.2.39ubuntu0.2 [8,814 B]
Del python3-apport 2.14.7-0ubuntu8.5 [75.6 kB]
Del gnome-keyring 3.10.1-1ubuntu7.1 [577 kB]
Del libqt4-network 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [567 kB]
Del libbatik-java 1.7.ubuntu-8ubuntu2.14.10.1 [3,300 kB]
Del ubuntu-release-upgrader-core 1:14.10.10 [23.9 kB]
Del libqt4-script 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [811 kB]
Del imagemagick 8:6.7.7.10+dfsg-4ubuntu1 [188 kB]
Del spamassassin 3.4.0-3ubuntu2.1 [1,035 kB]
Del libcairo2 1.13.0~20140204-0ubuntu1.1 [535 kB]
Del account-plugin-aim 3.8.6-0ubuntu13.1 [8,870 B]
Del liblog4j1.2-java 1.2.17-4ubuntu3 [383 kB]
Del libqt4-xml 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [102 kB]
Del liboxideqt-qmlplugin 1.7.8-0ubuntu0.14.10.1 [162 kB]
Del libxext6 2:1.3.2-1ubuntu0.1 [31.6 kB]
Del mesa-common-dev 10.3.2-0ubuntu0.1 [286 kB]
Del libwebkitgtk-3.0-0 2.4.7-1~ubuntu14.10.1 [7,576 kB]
Del libqt4-test 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [61.7 kB]
Del gvfs-common 1.20.2-1ubuntu3 [41.6 kB]
Del libqt5network5 5.3.0+dfsg-2ubuntu9.1 [533 kB]
Del libjavascriptcoregtk-1.0-0 2.4.7-1~ubuntu14.10.1 [1,865 kB]
Del libssl-doc 1.0.1f-1ubuntu9.5 [962 kB]
Del libpstoedit0c2a 3.62-2 [311 kB]
Del nautilus 1:3.10.1-0ubuntu15.1 [491 kB]
Del texlive-fonts-recommended 2014.20140717-01ubuntu1 [5,723 kB]
Del libunity-settings-daemon1 14.04.0+14.10.20141014-0ubuntu1.1 [76.2 kB]
Del gnome-session-bin 3.9.90-0ubuntu16.1 [142 kB]
Del libmagickcore5-extra 8:6.7.7.10+dfsg-4ubuntu1 [58.8 kB]
Del account-plugin-yahoo 3.8.6-0ubuntu13.1 [8,874 B]
Del system-config-printer-udev 1.5.1+20141010-0ubuntu2.3 [21.6 kB]
Del libgles1-mesa-dev 10.3.2-0ubuntu0.1 [17.9 kB]
Del libqt4-help 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [205 kB]
Del libpwquality-common 1.2.3-1ubuntu1.2 [5,458 B]
Del linux-headers-generic 3.16.0.38.39 [2,392 B]
Del efibootmgr 0.7.0-2ubuntu0.14.10.1 [31.0 kB]
Del libglapi-mesa 10.3.2-0ubuntu0.1 [21.8 kB]
Del libqt4-designer 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [3,642 kB]
Del libqt5sql5-sqlite 5.3.0+dfsg-2ubuntu9.1 [31.2 kB]
Del deja-dup 32.0-0ubuntu1.1 [288 kB]
Del ruby2.1 2.1.2-2ubuntu1.2 [70.5 kB]
Del evolution-plugins 3.12.10-0ubuntu1~14.10.1 [86.4 kB]
Del libebook-contacts-1.2-0 3.12.10-0ubuntu1~14.10.1 [49.4 kB]
Del libqt4-svg 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [138 kB]
Del nautilus-data 1:3.10.1-0ubuntu15.1 [50.7 kB]
Del libpoppler-qt4-4 0.26.5-0ubuntu2 [110 kB]
Del texlive-metapost 2014.20140717-01ubuntu1 [410 kB]
Del libqt4-scripttools 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [223 kB]
Del gnome-session-common 3.9.90-0ubuntu16.1 [42.5 kB]
Del whoopsie 0.2.39ubuntu0.2 [22.4 kB]
Del libqt4-opengl 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [322 kB]
Del gir1.2-ebookcontacts-1.2 3.12.10-0ubuntu1~14.10.1 [12.9 kB]
Del libgl1-mesa-dev 10.3.2-0ubuntu0.1 [5,324 B]
Del libgail-3-0 3.12.2-0ubuntu15.2 [20.7 kB]
Del libsystemd-login0 208-8ubuntu8.2 [26.5 kB]
Del fop 1:1.1.dfsg-2ubuntu1 [13.5 kB]
Del gvfs 1.20.2-1ubuntu3 [91.5 kB]
Del empathy-common 3.8.6-0ubuntu13.1 [1,520 kB]
Del python3-distupgrade 1:14.10.10 [101 kB]
Del liblightdm-gobject-1-0 1.12.3-0ubuntu1 [35.2 kB]
Del oxideqt-codecs 1.7.8-0ubuntu0.14.10.1 [529 kB]
Del apport-gtk 2.14.7-0ubuntu8.5 [9,574 B]
Del glib-networking-services 2.42.1-0ubuntu1 [15.2 kB]
Del thunderbird 1:31.7.0+build1-0ubuntu0.14.10.1 [30.8 MB]
Del texlive-fonts-recommended-doc 2014.20140717-01ubuntu1 [2,733 kB]
Del libnuma1 2.0.9~rc5-1ubuntu3 [20.3 kB]
Del gir1.2-webkit-3.0 2.4.7-1~ubuntu14.10.1 [60.2 kB]
Del system-config-printer-common 1.5.1+20141010-0ubuntu2.3 [36.6 kB]
Del liboxideqtcore0 1.7.8-0ubuntu0.14.10.1 [25.1 MB]
Del libegl1-mesa-drivers 10.3.2-0ubuntu0.1 [2,537 kB]
Del libuuid1 2.25.1-3ubuntu4.1 [16.4 kB]
Del libwebkitgtk-1.0-common 2.4.7-1~ubuntu14.10.1 [106 kB]
Del texlive-full 2014.20140717-01ubuntu1 [14.6 kB]
Del libpwquality1 1.2.3-1ubuntu1.2 [11.8 kB]
Del bsdutils 1:2.25.1-3ubuntu4.1 [44.7 kB]
Del libqt4-opengl 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [304 kB]
Del rsyslog 7.4.4-1ubuntu11.2 [358 kB]
Del libxext6 2:1.3.2-1ubuntu0.1 [29.4 kB]
Del libgles2-mesa 10.3.2-0ubuntu0.1 [12.5 kB]
Del texlive-pictures 2014.20140717-01ubuntu1 [2,984 kB]
Del libudev1 208-8ubuntu8.2 [34.7 kB]
Del libebook-1.2-14 3.12.10-0ubuntu1~14.10.1 [57.3 kB]
Del libicu52 52.1-6ubuntu0.3 [6,775 kB]
Del unattended-upgrades 0.82.8ubuntu0.2 [26.6 kB]
Del shotwell 0.20.2-0ubuntu0.14.10.2 [1,504 kB]
Del libebackend-1.2-7 3.12.10-0ubuntu1~14.10.1 [122 kB]
Del glib-networking 2.42.1-0ubuntu1 [42.1 kB]
Del libxext-dev 2:1.3.2-1ubuntu0.1 [81.6 kB]
Del icedtea-netx-common 1.5.2-1ubuntu2~14.10 [1,118 kB]
Del libqtgui4 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [4,265 kB]
Del libldap2-dev 2.4.31-1+nmu2ubuntu11.1 [262 kB]
Del thunderbird-gnome-support 1:31.7.0+build1-0ubuntu0.14.10.1 [8,592 B]
Del libgdata-common 0.16.1-1~ubuntu14.10.1 [19.4 kB]
Del procps 1:3.3.9-1ubuntu5.2 [212 kB]
Del ghc-7.8.3 7.8.3-8~utopic [36.4 MB]
Del evolution 3.12.10-0ubuntu1~14.10.1 [50.0 kB]
Del landscape-client-ui-install 14.12-0ubuntu0.14.10 [6,450 B]
Del libopenvg1-mesa 10.3.2-0ubuntu0.1 [12.9 kB]
Del libqt5printsupport5 5.3.0+dfsg-2ubuntu9.1 [174 kB]
Del account-plugin-windows-live 0.12+14.10.20140924-0ubuntu2 [2,088 B]
Del libqtgui4 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [4,470 kB]
Del gvfs-fuse 1.20.2-1ubuntu3 [13.5 kB]
Del python3-cupshelpers 1.5.1+20141010-0ubuntu2.3 [59.0 kB]
Del libpoppler-glib8 0.26.5-0ubuntu2 [105 kB]
Del policykit-1 0.105-4ubuntu2.14.10.1 [51.9 kB]
Del gir1.2-javascriptcoregtk-3.0 2.4.7-1~ubuntu14.10.1 [12.0 kB]
Del libedata-book-1.2-20 3.12.10-0ubuntu1~14.10.1 [118 kB]
Del linux-libc-dev 3.16.0-38.52 [782 kB]
Del shotwell-common 0.20.2-0ubuntu0.14.10.2 [479 kB]
Del sa-compile 3.4.0-3ubuntu2.1 [13.9 kB]
Del libqt5gui5 5.3.0+dfsg-2ubuntu9.1 [2,176 kB]
Del account-plugin-flickr 0.12+14.10.20140924-0ubuntu2 [2,732 B]
Del gir1.2-gdata-0.0 0.16.1-1~ubuntu14.10.1 [34.1 kB]
Del systemd 208-8ubuntu8.2 [1,318 kB]
Del account-plugin-google 0.12+14.10.20140924-0ubuntu2 [3,478 B]
Del libtasn1-6 4.0-2ubuntu0.2 [41.8 kB]
Del qdbus 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [29.0 kB]
Del gvfs-libs 1.20.2-1ubuntu3 [106 kB]
Del libglapi-mesa 10.3.2-0ubuntu0.1 [22.3 kB]
Del linux-headers-3.16.0-38-generic 3.16.0-38.52 [725 kB]
Del libgbm1 10.3.2-0ubuntu0.1 [1,321 kB]
Del libfuse2 2.9.2-4ubuntu4.14.10.1 [89.0 kB]
Del libqt4-dbus 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [6,496 B]
Del texlive-latex-recommended 2014.20140717-01ubuntu1 [7,466 kB]
Del libxatracker2 10.3.2-0ubuntu0.1 [934 kB]
Del gnome-session 3.9.90-0ubuntu16.1 [10.4 kB]
Del fuse 2.9.2-4ubuntu4.14.10.1 [25.3 kB]
Del linux-headers-3.16.0-38 3.16.0-38.52 [9,104 kB]
Del libnb-org-openide-util-java 7.4+dfsg1-1 [158 kB]
Del libcgmanager0 0.32-4ubuntu1.4 [33.4 kB]
Del libssl-dev 1.0.1f-1ubuntu9.5 [1,090 kB]
Del libqt5sql5 5.3.0+dfsg-2ubuntu9.1 [104 kB]
Del ghc-7.8.3-dyn 7.8.3-8~utopic [2,320 B]
Del libqtdbus4 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [183 kB]
Del libwebkitgtk-1.0-0 2.4.7-1~ubuntu14.10.1 [7,579 kB]
Del gir1.2-gtk-3.0 3.12.2-0ubuntu15.2 [177 kB]
Del libsignon-glib1 1.10daily13.06.25-0ubuntu3.1 [33.9 kB]
Del latex-beamer 2014.20140717-01ubuntu1 [13.8 kB]
Del libyaml-0-2 0.1.6-1ubuntu0.1 [47.6 kB]
Del ubuntu-release-upgrader-gtk 1:14.10.10 [9,356 B]
Del libcairo-gobject2 1.13.0~20140204-0ubuntu1.1 [17.2 kB]
Del libgl1-mesa-glx 10.3.2-0ubuntu0.1 [148 kB]
Del libaccount-plugin-google 0.12+14.10.20140924-0ubuntu2 [5,540 B]
Del gir1.2-signon-1.0 1.10daily13.06.25-0ubuntu3.1 [5,438 B]
Del libpolkit-agent-1-0 0.105-4ubuntu2.14.10.1 [15.2 kB]
Del libegl1-mesa 10.3.2-0ubuntu0.1 [66.6 kB]
Del pstoedit 3.62-2 [106 kB]
Del libpam-gnome-keyring 3.10.1-1ubuntu7.1 [36.2 kB]
Del libqt5test5 5.3.0+dfsg-2ubuntu9.1 [77.6 kB]
Del texlive-luatex 2014.20140717-01ubuntu1 [8,222 kB]
Del libaccount-plugin-generic-oauth 0.12+14.10.20140924-0ubuntu2 [5,178 B]
Del libpoppler46 0.26.5-0ubuntu2 [752 kB]
Del libudev1 208-8ubuntu8.2 [38.4 kB]
Del libwebkitgtk-3.0-common 2.4.7-1~ubuntu14.10.1 [107 kB]
Del gvfs-bin 1.20.2-1ubuntu3 [50.3 kB]
Del evolution-common 3.12.10-0ubuntu1~14.10.1 [1,084 kB]
Del libqt4-xmlpatterns 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,059 kB]
Del evolution-data-server-common 3.12.10-0ubuntu1~14.10.1 [116 kB]
Del libqt5dbus5 5.3.0+dfsg-2ubuntu9.1 [181 kB]
Del cgmanager 0.32-4ubuntu1.4 [68.6 kB]
Del mcp-account-manager-uoa 3.8.6-0ubuntu13.1 [25.3 kB]
Del libsystemd-daemon0 208-8ubuntu8.2 [10.4 kB]
Del t1utils 1.37-2.1ubuntu0.1 [51.7 kB]
Del libqt5xml5 5.3.0+dfsg-2ubuntu9.1 [93.0 kB]
Del account-plugin-salut 3.8.6-0ubuntu13.1 [8,904 B]
Del libruby2.1 2.1.2-2ubuntu1.2 [3,071 kB]
Del libedata-cal-1.2-23 3.12.10-0ubuntu1~14.10.1 [67.9 kB]
Del texlive-metapost-doc 2014.20140717-01ubuntu1 [26.9 MB]
Del libqt4-xmlpatterns 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,093 kB]
Del libecal-1.2-16 3.12.10-0ubuntu1~14.10.1 [100 kB]
Del libqt4-xml 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [97.4 kB]
Del libtinfo-dev 5.9+20140712-2ubuntu1 [76.3 kB]
Del gir1.2-ebook-1.2 3.12.10-0ubuntu1~14.10.1 [7,868 B]
Del libqt5widgets5 5.3.0+dfsg-2ubuntu9.1 [2,273 kB]
Del texlive-latex-recommended-doc 2014.20140717-01ubuntu1 [34.8 MB]
Del libpam-systemd 208-8ubuntu8.2 [23.0 kB]
Del libncurses5-dev 5.9+20140712-2ubuntu1 [174 kB]
Del libgudev-1.0-0 1:208-8ubuntu8.2 [14.3 kB]
Del util-linux 2.25.1-3ubuntu4.1 [806 kB]
Del liboxideqtquick0 1.7.8-0ubuntu0.14.10.1 [248 kB]
Del libcgmanager0 0.32-4ubuntu1.4 [30.7 kB]
Del firefox-locale-en 38.0+build3-0ubuntu0.14.10.1 [642 kB]
Del libldap-2.4-2 2.4.31-1+nmu2ubuntu11.1 [154 kB]
Del libjavascriptcoregtk-3.0-0 2.4.7-1~ubuntu14.10.1 [1,865 kB]
Del libgles1-mesa 10.3.2-0ubuntu0.1 [9,980 B]
Del lightdm 1.12.3-0ubuntu1 [109 kB]
Del texlive-generic-recommended 2014.20140717-01ubuntu1 [2,108 kB]
Del libprocps3 1:3.3.9-1ubuntu5.2 [31.8 kB]
Del libqt4-sql-mysql 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [31.4 kB]
Del account-plugin-twitter 0.12+14.10.20140924-0ubuntu2 [2,416 B]
Del libpolkit-gobject-1-0 0.105-4ubuntu2.14.10.1 [35.5 kB]
Del libnautilus-extension1a 1:3.10.1-0ubuntu15.1 [52.5 kB]
Del libgl1-mesa-glx 10.3.2-0ubuntu0.1 [155 kB]
Del libqt4-declarative 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,098 kB]
Del flashplugin-installer 11.2.202.460ubuntu0.14.10.1 [7,158 B]
Del libgl1-mesa-dri 10.3.2-0ubuntu0.1 [3,352 kB]
Del libjcommon-java 1.0.16-3 [459 kB]
Del python3-problem-report 2.14.7-0ubuntu8.5 [9,248 B]
Del system-config-printer-gnome 1.5.1+20141010-0ubuntu2.3 [138 kB]
Del libsmartcols1 2.25.1-3ubuntu4.1 [60.4 kB]
Del libtasn1-6 4.0-2ubuntu0.2 [43.7 kB]
Del texlive 2014.20140717-01ubuntu1 [14.3 kB]
Del libcamel-1.2-49 3.12.10-0ubuntu1~14.10.1 [465 kB]
Del spamc 3.4.0-3ubuntu2.1 [51.8 kB]
Del libegl1-mesa-dev 10.3.2-0ubuntu0.1 [17.9 kB]
Del glib-networking-common 2.42.1-0ubuntu1 [10.3 kB]


$ sudo apt-get clean


$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get update 
Err http://archive.ubuntu.com vivid InRelease
  
Err http://archive.ubuntu.com vivid-updates InRelease
  
Err http://archive.canonical.com vivid InRelease
  
Err http://archive.canonical.com vivid InRelease
  
Err http://archive.ubuntu.com vivid-backports InRelease
  
Err http://archive.ubuntu.com vivid-security InRelease
  
Err http://archive.canonical.com vivid Release.gpg
  Could not resolve 'archive.canonical.com'
Err http://archive.ubuntu.com vivid Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com vivid-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com vivid-backports Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com vivid-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com vivid Release.gpg
  Could not resolve 'archive.canonical.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-backports/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-security/InRelease  


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/vivid/InRelease  


W: Failed to fetch http://archive.canonical.com/dists/vivid/InRelease  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid/Release.gpg  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/vivid/Release.gpg  Could not resolve 'archive.canonical.com'


W: Failed to fetch http://archive.canonical.com/dists/vivid/Release.gpg  Could not resolve 'archive.canonical.com'


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-backports/Release.gpg  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/vivid-security/Release.gpg  Could not resolve 'archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.


$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$


```

---

### Post by Bucky Ball on 2015-06-08
The Linux 3.13.0-40-generic kernel is old, even for 14.04 LTS, so even though it's showing 15.04, things look fairly shot by your output. Do you have valuable data backed up?

Did you do a full update/upgrade of 14.04 LTS before doing the net upgrade to 15.04? I'm guess not by the version of your kernel. That could be at the bottom of your issue because things look pretty shot. I'm running Linux 3.13.0-40-generic on 14.04. Updating the older release prior to upgrading to another release is essential. 

Is the machine online with a cable? If not, it needs to be online somehow to update/upgrade.

---

### Post by jeyaa on 2015-06-08
Thanks for quick reply. Can't I create an offline repository and do system upgrade.

---

### Post by Bucky Ball on 2015-06-08
I believe so, but can't help you there. You don't have an ethernet cable available? What are you planning to do? Down load the repo on another machine, put it on a hard drive, connect it to the problem machine and update from that?

Ethernet cable MUCH easier and quicker if possible ...

---

### Post by jeyaa on 2015-06-08
ethernet is also not working:(. When i connect the cable, ubuntu shows in top right corner that it is connecting but never connects. I have Qualcomm ethernet adapter.
That is the reason I was thinking of creating offline repo

---

### Post by Bucky Ball on 2015-06-08
Ah. Got ya. ;)

You should find quite a bit of info re. offline repos with a bit of digging. There are a few threads here, but also 'create offline repo ubuntu' in a search engine should get you going.

To be honest, it looks a bit of a mess in there. If you have valuable data backed up, perhaps reinstall 14.04 LTS or 15.04 might be easier. On the other hand, you'll learn a few things about Ubuntu trying to figure this out. Good luck. :)

PS: Not having updated 14.04 prior to doing the release upgrade may have seriously screwed things. The upgrade completed with no errors when you did it then you rebooted the machine to chaos or things stalled part way?

PPS: If you are using regular Ubuntu with Unity, what happens when you issue this in a terminal:

```
sudo service lightdm restart
```

---

### Post by jeyaa on 2015-06-09
my problem got solved after updating kernel 3.19.x. Everything is working now. I copied the linux 3.19.X packages to my sytem and installed them. after reboot everything worked. Thanks for tips

---

### Post by Bucky Ball on 2015-06-09
Fantastic news and well done. Please mark the thread as solved (see second link in my signature). Would be nice if you could share how you fixed with the community (links to any pages you followed). Cheers. 

Can you run:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... with no issue? If so, things are looking good. :)

---

