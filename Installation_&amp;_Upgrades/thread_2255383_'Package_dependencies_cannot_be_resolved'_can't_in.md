---
title: "'Package dependencies cannot be resolved' can't install codecs or other software?"
date: 2014-12-04
forum: Installation &amp; Upgrades
---

### Post by isla on 2014-12-04
I may have put the wrong title in because I don't know what my ubuntu is doing. I'm a newbie :-(
I am struggling to use the new ubuntu horse package - it is running slowly. but it also wont install programs or play some videos without these messages. I followed the instructions on this link, '10 things to do after you install ubuntu 14.10'....  I probably did it wrong. 
This is the link, [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-10-utopic-unicorn](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-10-utopic-unicorn)
and it says how to 
Enable Partner repositories, Getdeb and playdeb, add personal package archives, check for updates, upgrade packages, major upgrades, install essentials, install additional drivers, chrome (i didn't do that), Clean up.

Can anybody point me in the right direction? I struggle with terminology because I'm  'u.s.c.w.a.paddle'
thankyou for any assistance, 
isla x:lolflag:

---------------------

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

 The following packages have unmet dependencies:

gstreamer1.0-plugins-bad: Depends: libc6 (>= 2.15) but 2.19-10ubuntu2.1 is to be installed
                          Depends: libcurl3-gnutls (>= 7.16.2) but 7.37.1-1ubuntu3.1 is to be installed
                          Depends: libdvdnav4 (>= 4.1.3) but 5.0.1-1 is to be installed
                          Depends: libdvdread4 (>= 4.1.3) but 5.0.0-1ubuntu1 is to be installed
                          Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-16ubuntu6 is to be installed
                          Depends: libglib2.0-0 (>= 2.37.3) but 2.42.1-1~ubuntu1 is to be installed
                          Depends: libgstreamer-plugins-bad1.0-0 (= 1.4.3-1ubuntu1) but 1.4.3-1ubuntu1 is to be installed
                          Depends: libgudev-1.0-0 (>= 146) but 1:208-8ubuntu8 is to be installed
                          Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed
                          Depends: libmpg123-0 (>= 1.6.2) but 1.18.0-1ubuntu1 is to be installed
                          Depends: libopenal1 (>= 1.14) but 1:1.15.1-5 is to be installed
                          Depends: libopenexr6 (>= 1.6.1) but 1.6.1-7ubuntu1 is to be installed
                          Depends: liborc-0.4-0 (>= 1:0.4.20) but 1:0.4.22-1 is to be installed
                          Depends: librsvg2-2 (>= 2.36) but 2.40.4-1 is to be installed
                          Depends: librtmp1 (>= 2.3) but 2.4+20131018.git79459a2-4 is to be installed
                          Depends: libsoundtouch0 (>= 1.8.0) but 1.8.0-1 is to be installed
                          Depends: libstdc++6 (>= 4.9) but 4.9.1-16ubuntu6 is to be installed
                          Depends: libusb-1.0-0 (>= 2:1.0.8) but 2:1.0.17-1ubuntu2 is to be installed
                          Depends: libxml2 (>= 2.7.4) but 2.9.1+dfsg1-4ubuntu1 is to be installed
                          Depends: gstreamer1.0-plugins-bad-videoparsers (= 1.4.3-1ubuntu1) but 1.4.3-1ubuntu1 is to be installed
                          Depends: gstreamer1.0-plugins-bad-faad (= 1.4.3-1ubuntu1) but 1.4.3-1ubuntu1 is to be installed
gstreamer1.0-plugins-bad:i386: Depends: libc6 (>= 2.15) but 2.19-10ubuntu2.1 is to be installed
                               Depends: libcurl3-gnutls (>= 7.16.2) but 7.37.1-1ubuntu3.1 is to be installed
                               Depends: libdvdnav4 (>= 4.1.3) but 5.0.1-1 is to be installed
                               Depends: libdvdread4 (>= 4.1.3) but 5.0.0-1ubuntu1 is to be installed
                               Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-16ubuntu6 is to be installed
                               Depends: libglib2.0-0 (>= 2.37.3) but 2.42.1-1~ubuntu1 is to be installed
                               Depends: libgstreamer-plugins-bad1.0-0 (= 1.4.3-1ubuntu1) but 1.4.3-1ubuntu1 is to be installed
                               Depends: libgudev-1.0-0 (>= 146) but 1:208-8ubuntu8 is to be installed
                               Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed
                               Depends: libmpg123-0 (>= 1.6.2) but 1.18.0-1ubuntu1 is to be installed
                               Depends: libopenal1 (>= 1.14) but 1:1.15.1-5 is to be installed
                               Depends: libopenexr6 (>= 1.6.1) but 1.6.1-7ubuntu1 is to be installed
                               Depends: liborc-0.4-0 (>= 1:0.4.20) but 1:0.4.22-1 is to be installed
                               Depends: librsvg2-2 (>= 2.36) but 2.40.4-1 is to be installed
                               Depends: librtmp1 (>= 2.3) but 2.4+20131018.git79459a2-4 is to be installed
                               Depends: libsoundtouch0 (>= 1.8.0) but 1.8.0-1 is to be installed
                               Depends: libstdc++6 (>= 4.9) but 4.9.1-16ubuntu6 is to be installed
                               Depends: libusb-1.0-0 (>= 2:1.0.8) but 2:1.0.17-1ubuntu2 is to be installed
                               Depends: libxml2 (>= 2.7.4) but 2.9.1+dfsg1-4ubuntu1 is to be installed
                               Depends: gstreamer1.0-plugins-bad-videoparsers (= 1.4.3-1ubuntu1) but 1.4.3-1ubuntu1 is to be installed
                               Depends: gstreamer1.0-plugins-bad-faad (= 1.4.3-1ubuntu1) but 1.4.3-1ubuntu1 is to be installed


--------------------------------------------------------------------------

---

### Post by nerdtron on 2014-12-04
Up to which part did you finish before getting that error? What is the command did you use on that?

---

### Post by MAFoElffen on 2014-12-04
> **nerdtron said:**
> Up to which part did you finish before getting that error? What is the command did you use on that?
That's what I was wondering and what was missing from the OP's post, but... (Now refering to the OP)

Here is the logic of what you were doing. An LTS version is a stable release. Releases between are intermediate and considered less stable. 

Then there are the repository's. The Main repo's go through a testing process to be considered as Stable. What you were doing was installing packages that change those repositories to other test repos. Meaning that they might be pre-release packages or to someone's PPA. Before doing that, you probably should have backed up your sources.list, so you had something to fall back to. No matter now.

Having experience with dev testing, I just expect that dev code will not be perfect. For me to expect things to break as a regular occurrence may sound like living on the edge... but that is the same as what you implemented. That article describing newer code left out that there are other factors in the timeline to get code approved and moved to the main repos, besides red tape.

Please answer what command you were at... then the answer will probably be in if the PPA or repo was properly changed before you updated and upgraded. The answer will probably show in the current software sources (/etc/apt/sources.list) and in the apt logs (/var/log/apt/history.log). Please post those 2 files... but this time when you post them, please paste them inside of Code tags ('#" icon in the advanced post toolbar).

---

