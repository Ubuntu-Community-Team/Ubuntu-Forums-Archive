---
title: "Some Packages+Dependencies for Ubuntu/Kubuntu/Xubuntu (i386)"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by nucleuskore on 2008-05-15
[SIZE="5"]This post is outdated, scroll down for updated version.[/SIZE]
OR
click here for
[June 2011 - System upgrade](http://ubuntuforums.org/showthread.php?t=795859&page=4#37)

[SIZE="4"]Hi everybody,[/SIZE]

   This is my first post on Ubuntu forums. I live in India, in one of the bigger cities Mangalore, and am fortunate to have access to an always on 256 kpbs DSL connection.  

   Enabling multimedia and restricted formats in systems not connected to the internet can be a pain with any linux distro with a lot of dependency   problems. This is more so a problem for people in smaller cities with slow dial up connections or worse, no internet access at all. Being primarily a OpenSuSE user, I started redistributing OSS rpms of select software with their dependencies as zip archives in the month of December last year, and usually release updates every month, time permitting. 

   The response has been fairly good. What I and many users realised that this helps not only those who do not have access to internet at home, but also regular users who want to set up their system quickly after a format, or set up multiple PCs, saving bandwidth. 

   I decided to start the same work for Ubuntu 8.04, and will be redistributing the packages and dependencies through **AptOnCD**. I have selected a few software which may be required on home PCs. This list is in no way complete, but just represents what I think may be the bare minimum one would like to have on a multimedia desktop PC.

   I have compiled a collection of applications and their dependencies for Ubuntu 8.04 (i386) for installation to PCs not connected to the internet and for quick multimedia setup.

**Application list:**
mplayer and w32codecs
mozilla-mplayer plugin
audacious
k3b
devede
audacity
avidemux
ffmpeg
transcode
ntfs-config
vlc
libdvdcss
peazip

**Instructions:**
1. Download [this](http://www.mediafire.com/?9gmknmnuwnr) iso file.
2. Burn iso to a cd. **
3. Insert cd, it will open in nautilus along with this prompt

[[IMG]http://img405.imageshack.us/img405/1/aptoncd1bh5.th.png[/IMG]](http://img405.imageshack.us/my.php?image=aptoncd1bh5.png)

4. Click start package manager, when you do that you will be prompted for your password

[[IMG]http://img207.imageshack.us/img207/4276/aptoncd2ey6.th.png[/IMG]](http://img207.imageshack.us/my.php?image=aptoncd2ey6.png)

Key in your password and press ENTER

5. CLose the quick introduction dialog box

[[IMG]http://img405.imageshack.us/img405/1936/aptoncd3rv6.th.png[/IMG]](http://img405.imageshack.us/my.php?image=aptoncd3rv6.png)

6. Now you will see the Synaptic Package Manager. Click the search button and search for each of these applications. When you find them click and mark for installation.

mplayer
mozilla-mplayer
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
transcode
ntfsconfig
vlc
libdvdcss
w32codecs
peazip

As you mark them you will see dependency warning dialog boxes, select mark

[[IMG]http://img118.imageshack.us/img118/5646/aptoncd4vk6.th.png[/IMG]](http://img118.imageshack.us/my.php?image=aptoncd4vk6.png)

7. Click Apply. The installation will proceed

[[IMG]http://img118.imageshack.us/img118/7209/aptoncd5nl6.th.png[/IMG]](http://img118.imageshack.us/my.php?image=aptoncd5nl6.png)

8. After everything is installed click Close

[[IMG]http://img118.imageshack.us/img118/9358/aptoncd6ai4.th.png[/IMG]](http://img118.imageshack.us/my.php?image=aptoncd6ai4.png)

Enjoy your Ubuntu !

** If you are feeling **very geeky** replace the second step with the following
a. Open a terminal
b. Assuming the iso is in your home folder, type

sudo mkdir /mnt/isofile

sudo mount -o loop -t iso9660 aptoncd-20080514-CD1.iso /mnt/isofile

c. Continue from Step 3

[My Original Post](http://www.thinkdigit.com/forum/showthread.php?t=87790)

---

### Post by osnewbie on 2008-05-16
Thanks this looks great..
i've been searching without much success for a guide to installing without an internet connection. Quick question though I don't see any gui-lik application. i would like to have ubuntu-desktop or some gui capability for my server

---

### Post by nucleuskore on 2008-05-16
Sorry I cannot understand you. Ubuntu installs with a GUI, unless you chose to do a special text based inatall.

---

### Post by nucleuskore on 2008-05-17
[SIZE="4"]Hi everybody,[/SIZE]

After my last post, I was wondering if I could extend this work to Kubuntu and Xubuntu, making a single iso which can be deployed to all three Ubuntu, Kubuntu and Xubuntu. So I got cracking and here's the result. I have included two new packages, kchmviewer and evince and used AptOnCD for this work.

Here is the updated list of applications

**Application list:**
kchmviewer
evince
mplayer
kmplayer
mozilla-mplayer plugin
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
ffmpegthumbnailer
transcode
ntfsconfig
vlc
libdvdcss
w32codecs
peazip

**Instructions:**
1. Download this iso file.
Mirror 1:[Filefactory (http)](http://www.filefactory.com/file/46a15c/)
Mirror 2: [BitTorrent](http://www.linuxrocks.in/torrents/UbuKuXu-aptoncd-20080518-CD1.iso.4193506.TPB.torrent)
(md5sum e78593c5643210c8e2e9c39d37d1c270)

2. Burn iso to a cd. **

**Ubuntu specific instructions:**

3. Insert cd, it will open in nautilus along with this prompt

[[IMG]http://img405.imageshack.us/img405/1/aptoncd1bh5.th.png[/IMG]](http://img405.imageshack.us/my.php?image=aptoncd1bh5.png)

4. Click start package manager, when you do that you will be prompted for your password

[[IMG]http://img207.imageshack.us/img207/4276/aptoncd2ey6.th.png[/IMG]](http://img207.imageshack.us/my.php?image=aptoncd2ey6.png)

Key in your password and press ENTER

5. CLose the quick introduction dialog box

[[IMG]http://img405.imageshack.us/img405/1936/aptoncd3rv6.th.png[/IMG]](http://img405.imageshack.us/my.php?image=aptoncd3rv6.png)

6. Now you will see the Synaptic Package Manager. Click the search button and search for each of these applications. When you find them click and mark for installation.

kchmviewer
mplayer
mozilla-mplayer plugin
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
ffmpegthumbnailer
transcode
ntfs-config
vlc
libdvdcss2
w32codecs
peazip

As you mark them you will see dependency warning dialog boxes, select mark

[[IMG]http://img118.imageshack.us/img118/5646/aptoncd4vk6.th.png[/IMG]](http://img118.imageshack.us/my.php?image=aptoncd4vk6.png)

7. Click Apply. The installation will proceed

[[IMG]http://img118.imageshack.us/img118/7209/aptoncd5nl6.th.png[/IMG]](http://img118.imageshack.us/my.php?image=aptoncd5nl6.png)

8. After everything is installed click Close

[[IMG]http://img118.imageshack.us/img118/9358/aptoncd6ai4.th.png[/IMG]](http://img118.imageshack.us/my.php?image=aptoncd6ai4.png)

Enjoy your Ubuntu !

---

### Post by nucleuskore on 2008-05-17
**Xubuntu specific instructions:**

3. Insert cd, it will open in Thunar along with this prompt

[[IMG]http://img119.imageshack.us/img119/4530/xub1vi7.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xub1vi7.png)

4. Click start package manager, when you do that you will be prompted for your password

[[IMG]http://img521.imageshack.us/img521/4166/xub2rt4.th.png[/IMG]](http://img521.imageshack.us/my.php?image=xub2rt4.png)

Key in your password and press ENTER

5. CLose the quick introduction dialog box

[[IMG]http://img104.imageshack.us/img104/5638/xub3jn9.th.png[/IMG]](http://img104.imageshack.us/my.php?image=xub3jn9.png)

6. Now you will see the Synaptic Package Manager. Click the search button and search for each of these applications. When you find them click and mark for installation.

[[IMG]http://img104.imageshack.us/img104/5040/xub4ih9.th.png[/IMG]](http://img104.imageshack.us/my.php?image=xub4ih9.png) [[IMG]http://img104.imageshack.us/img104/8514/xub5ci4.th.png[/IMG]](http://img104.imageshack.us/my.php?image=xub5ci4.png) [[IMG]http://img104.imageshack.us/img104/6522/xub6ik3.th.png[/IMG]](http://img104.imageshack.us/my.php?image=xub6ik3.png)

kchmviewer
mplayer
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
ffmpegthumbnailer
transcode
ntfs-config
vlc
libdvdcss2
w32codecs
peazip

As you mark them you will see dependency warning dialog boxes, select mark

[[IMG]http://img119.imageshack.us/img119/9140/xub7pt7.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xub7pt7.png)

---

### Post by nucleuskore on 2008-05-17
7. Click Apply. The installation will proceed

[[IMG]http://img104.imageshack.us/img104/3377/xub8an0.th.png[/IMG]](http://img104.imageshack.us/my.php?image=xub8an0.png) [[IMG]http://img104.imageshack.us/img104/2615/xub9ng2.th.png[/IMG]](http://img104.imageshack.us/my.php?image=xub9ng2.png) [[IMG]http://img521.imageshack.us/img521/9564/xub10ac1.th.png[/IMG]](http://img521.imageshack.us/my.php?image=xub10ac1.png) [[IMG]http://img119.imageshack.us/img119/1174/xub11xn4.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xub11xn4.png)

8. After everything is installed click Close

[[IMG]http://img119.imageshack.us/img119/9797/xub12oa6.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xub12oa6.png)

Enjoy your Xubuntu !

---

### Post by nucleuskore on 2008-05-17
**Kubuntu specific instructions:**

3. Insert cd, you will see a prompt onscreen

[[IMG]http://img513.imageshack.us/img513/2430/kub12zr9.th.png[/IMG]](http://img513.imageshack.us/my.php?image=kub12zr9.png)

Select Open in new window; a new window opens as below

[[IMG]http://img513.imageshack.us/img513/682/kub13mi2.th.png[/IMG]](http://img513.imageshack.us/my.php?image=kub13mi2.png)

Minimise it.

4. Click start (KMenu) -> System -> Adept Manager, when you do that you will be prompted for your password

[[IMG]http://img179.imageshack.us/img179/6349/kub1it9.th.png[/IMG]](http://img179.imageshack.us/my.php?image=kub1it9.png)

Key in your password and press ENTER

5. Now you will see the Adept Package Manager. 
[[IMG]http://img507.imageshack.us/img507/8140/kub2dm4.th.png[/IMG]](http://img507.imageshack.us/my.php?image=kub2dm4.png)

6. Click Adept -> Manage Repositories
[[IMG]http://img390.imageshack.us/img390/5558/kub3dh8.th.png[/IMG]](http://img390.imageshack.us/my.php?image=kub3dh8.png)

7. You will see this
[[IMG]http://img507.imageshack.us/img507/831/kub4yn3.th.png[/IMG]](http://img507.imageshack.us/my.php?image=kub4yn3.png)

8. Click on the,"Third-Party Software" tab, and click Add CD-ROM
[[IMG]http://img513.imageshack.us/img513/6890/kub5ld9.th.png[/IMG]](http://img513.imageshack.us/my.php?image=kub5ld9.png)

You will see this dialog box

[[IMG]http://img388.imageshack.us/img388/4984/kub6wq9.th.png[/IMG]](http://img388.imageshack.us/my.php?image=kub6wq9.png)

---

### Post by nucleuskore on 2008-05-17
Insert the CD you made in step 2; the following gets added automatically

[[IMG]http://img507.imageshack.us/img507/1344/kub7vv3.th.png[/IMG]](http://img507.imageshack.us/my.php?image=kub7vv3.png)

In the search box type and search for each of these applications. When you find them right click and mark for installation.

[[IMG]http://img390.imageshack.us/img390/3953/kub8lo9.th.png[/IMG]](http://img390.imageshack.us/my.php?image=kub8lo9.png)

kchmviewer
evince
kmplayer
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
ffmpegthumbnailer
transcode
ntfs-config
vlc
libdvdcss2
w32codecs
peazip

9. Click Apply. The installation will proceed

[[IMG]http://img390.imageshack.us/img390/512/kub9ik9.th.png[/IMG]](http://img390.imageshack.us/my.php?image=kub9ik9.png) [[IMG]http://img390.imageshack.us/img390/2646/kub10ol5.th.png[/IMG]](http://img390.imageshack.us/my.php?image=kub10ol5.png) [[IMG]http://img390.imageshack.us/img390/6325/kub11hq8.th.png[/IMG]](http://img390.imageshack.us/my.php?image=kub11hq8.png)

8. After everything is installed close adept

Enjoy your Kubuntu !

** If you are feeling **very geeky** replace the second step with the following
a. Open a terminal
b. Assuming the iso is in your home folder, type

sudo mkdir /mnt/isofile

sudo mount -o loop -t iso9660 UbuKuXu-aptoncd-20080518-CD1.iso /mnt/isofile

c. Continue from Step 3
------------------------------------------------------------------------------------------
**Package list:**
aptoncd_0.1.98-0ubuntu1_all.deb
aptoncd-metapackage_20080517.deb
aptoncd-metapackage_20080518.deb
audacious_1.5.0-2_i386.deb
audacious-plugins_1.5.0-1ubuntu1_i386.deb
audacity_1.3.4-1.1ubuntu1_i386.deb
avidemux_1%3a2.4.1-0.0ubuntu1_i386.deb
avidemux-common_1%3a2.4.1-0.0ubuntu1_all.deb
cdrdao_1%3a1.2.2-8ubuntu3_i386.deb
devede_3.6-0.0ubuntu1_all.deb
docbook-xml_4.5-5_all.deb
dvdauthor_0.6.14-1build2_i386.deb
evince_2.22.1.1-0ubuntu1_i386.deb
ffmpeg_3%3a0.cvs20070307-5ubuntu7_i386.deb
ffmpegthumbnailer_1.1.5-0ubuntu1_i386.deb
gamin_0.1.9-2ubuntu2_i386.deb
gawk_1%3a3.1.6.dfsg-0ubuntu1_i386.deb
gcc-3.3-base_1%3a3.3.6-15ubuntu6_i386.deb
gconf2_2.22.0-0ubuntu3_i386.deb
gconf2-common_2.22.0-0ubuntu3_all.deb
gksu_2.0.0-5ubuntu3_i386.deb
gnome-icon-theme_2.22.0-1ubuntu2_all.deb
gnome-keyring_2.22.1-1_i386.deb
gnome-mime-data_2.18.0-1_all.deb
gtk2-engines-pixbuf_2.12.9-3ubuntu4_i386.deb
k3b_1.0.4-2ubuntu4_i386.deb
kchmviewer_3.1.2-0ubuntu1_i386.deb
kdebase-bin_4%3a3.5.9-0ubuntu7.1_i386.deb
kdebase-bin-kde3_4%3a3.5.9-0ubuntu7.1_i386.deb
kdelibs4c2a_4%3a3.5.9-0ubuntu7.1_i386.deb
kdelibs-data_4%3a3.5.9-0ubuntu7.1_all.deb
kmplayer_1%3a0.10.0c-0ubuntu3_i386.deb
launchpad-integration_0.1.19_all.deb
liba52-0.7.4_0.7.4-11ubuntu1_i386.deb
libao2_0.8.8-3_i386.deb
libarts1c2a_1.5.9-0ubuntu2_i386.deb
libartsc0_1.5.9-0ubuntu2_i386.deb
libaudclient1_1.5.0-2_i386.deb
libaudid3tag1_1.5.0-2_i386.deb
libaudio2_1.9.1-1_i386.deb
libavahi-glib1_0.6.22-2ubuntu4_i386.deb
libavahi-qt3-1_0.6.22-2ubuntu4_i386.deb
libavc1394-0_0.5.3-1build1_i386.deb
libavcodec1d_3%3a0.cvs20070307-5ubuntu7_i386.deb
libavformat1d_3%3a0.cvs20070307-5ubuntu7_i386.deb
libavutil1d_3%3a0.cvs20070307-5ubuntu7_i386.deb
libbonobo2-0_2.22.0-0ubuntu1_i386.deb
libbonobo2-common_2.22.0-0ubuntu1_all.deb
libbonoboui2-0_2.21.90-1_i386.deb
libbonoboui2-common_2.21.90-1_all.deb
libcddb2_1.2.1-1_i386.deb
libcdio7_0.78.2+dfsg1-2ubuntu1_i386.deb
libcdio-cdda0_0.78.2+dfsg1-2ubuntu1_i386.deb
libchm1_2%3a0.39-6_i386.deb
libcurl3_7.18.0-1ubuntu2_i386.deb
libdbus-qt-1-1c2_0.62.git.20060814-2build1_i386.deb
libdc1394-13_1.1.0-5ubuntu1_i386.deb
libdirectfb-1.0-0_1.0.1-7ubuntu3_i386.deb
libdv4_1.0.0-1ubuntu1_i386.deb
libdvbpsi4_0.1.5-3_i386.deb
libdvdcss2_1.2.9-2medibuntu4_i386.deb
libdvdnav4_0.1.10-0.2_i386.deb
libdvdread3_0.9.7-8ubuntu1_i386.deb
libebml0_0.7.7-3.1_i386.deb
libenca0_1.9-4_i386.deb
libfaac0_1.26-0.1ubuntu1_i386.deb
libfaad0_2.6.1-2_i386.deb
libfame-0.9_0.9.1-0.2_i386.deb
libflac++6_1.2.1-1ubuntu2_i386.deb
libfreebob0_1.0.7-1_i386.deb
libgail18_1.22.1-0ubuntu1_i386.deb
libgail-common_1.22.1-0ubuntu1_i386.deb
libgamin0_0.1.9-2ubuntu2_i386.deb
libgconf2-4_2.22.0-0ubuntu3_i386.deb
libggi2_1%3a2.2.1-5ubuntu1_i386.deb
libgif4_4.1.6-4_i386.deb
libgii1_1%3a1.0.1-3_i386.deb
libgii1-target-x_1%3a1.0.1-3_i386.deb
libgksu2-0_2.0.5-1ubuntu5_i386.deb
libglade2-0_1%3a2.6.2-1_i386.deb
libglib1.2ldbl_1.2.10-19build1_i386.deb
libgnome2-0_2.22.0-0ubuntu1_i386.deb
libgnome2-common_2.22.0-0ubuntu1_all.deb
libgnomecanvas2-0_2.20.1.1-1_i386.deb
libgnomecanvas2-common_2.20.1.1-1_all.deb
libgnome-keyring0_2.22.1-1_i386.deb
libgnomeui-0_2.22.1.0-0ubuntu1_i386.deb
libgnomeui-common_2.22.1.0-0ubuntu1_all.deb
libgnomevfs2-0_1%3a2.22.0-2ubuntu1_i386.deb
libgnomevfs2-common_1%3a2.22.0-2ubuntu1_all.deb
libgsm1_1.0.12-1_i386.deb
libgtk1.2_1.2.10-18.1build2_i386.deb
libgtk1.2-common_1.2.10-18.1build2_all.deb
libgtk2.0-0_2.12.9-3ubuntu4_i386.deb
libgtop2-7_2.22.0-0ubuntu1_i386.deb
libgtop2-common_2.22.0-0ubuntu1_all.deb
libid3tag0_0.15.1b-10_i386.deb
libidl0_0.8.10-0.1_i386.deb
libiec61883-0_1.1.0-2ubuntu2_i386.deb
libimlib2_1.4.0-1ubuntu1_i386.deb
libiso9660-5_0.78.2+dfsg1-2ubuntu1_i386.deb
libjack0_0.109.2-1ubuntu1_i386.deb
libk3b2_1.0.4-2ubuntu4_i386.deb
libk3b2-extracodecs_1.0.4-2ubuntu4_i386.deb
libkpathsea4_2007.dfsg.1-2_i386.deb
liblame0_3.97-0.0_i386.deb
liblaunchpad-integration1_0.1.19_i386.deb
liblircclient0_0.8.3~pre1-0ubuntu7_i386.deb
liblua50_5.0.3-3_i386.deb
liblualib50_5.0.3-3_i386.deb
liblzo1_1.08-3_i386.deb
libmad0_0.15.1b-2.1ubuntu1_i386.deb
libmatroska0_0.8.1-1_i386.deb
libmcs1_0.4.1-2_i386.deb
libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb
libmms0_0.3-6_i386.deb
libmodplug0c2_1%3a0.7-7_i386.deb
libmowgli1_0.6.0-1_i386.deb
libmpcdec3_1.2.2-1build1_i386.deb
libmpeg2-4_0.4.1-1_i386.deb
libmusicbrainz4c2a_2.1.5-1ubuntu2_i386.deb
libnautilus-extension1_1%3a2.22.2-0ubuntu6_i386.deb
libneon27-gnutls_0.27.2-1_i386.deb
libnotify1_0.4.4-3build1_i386.deb
libopenal0a_1%3a0.0.8-7_i386.deb
liborbit2_1%3a2.14.12-0.1_i386.deb
libpoppler-glib2_0.6.4-1ubuntu1_i386.deb
libpostproc1d_3%3a0.cvs20070307-5ubuntu7_i386.deb
libpulse0_0.9.10-1ubuntu1_i386.deb
libpvm3_3.4.5-10_i386.deb
libqt3-mt_3%3a3.3.8-b-0ubuntu3_i386.deb
libquicktime1_2%3a1.0.0+debian-5_i386.deb
librsvg2-common_2.22.2-2_i386.deb
libsamplerate0_0.1.2-5ubuntu1_i386.deb
libscrollkeeper0_0.3.14-15ubuntu1_i386.deb
libsdl1.2debian_1.2.13-1ubuntu1_i386.deb
libsdl1.2debian-alsa_1.2.13-1ubuntu1_i386.deb
libsdl-image1.2_1.2.6-3_i386.deb
libsmbclient_3.0.28a-1ubuntu4_i386.deb
libsndfile1_1.0.17-4_i386.deb
libsox0_14.0.0-5_i386.deb
libstartup-notification0_0.9-1_i386.deb
libstdc++5_1%3a3.3.6-15ubuntu6_i386.deb
libsvga1_1%3a1.4.3-24_i386.deb
libswscale1d_3%3a0.cvs20070307-5ubuntu7_i386.deb
libtar_1.2.11-4_i386.deb
libtwolame0_0.3.10-2_i386.deb
libvcdinfo0_0.7.23-4ubuntu1_i386.deb
libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
libvorbisfile3_1.2.0.dfsg-2_i386.deb
libvte9_1%3a0.16.13-1ubuntu1_i386.deb
libvte-common_1%3a0.16.13-1ubuntu1_all.deb
libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb
libwxgtk2.6-0_2.6.3.2.2-2ubuntu4_i386.deb
libx264-57_1%3a0.svn20071224-0.0ubuntu1_i386.deb
libxosd2_2.2.14-1.4_i386.deb
libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb
libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb
medibuntu-keyring_2008.04.20_all.deb
mencoder_2%3a1.0~rc2-0ubuntu13_i386.deb
mozilla-mplayer_3.50-1ubuntu2_i386.deb
mplayer_2%3a1.0~rc2-0ubuntu13_i386.deb
mplayer-skins_2-7_all.deb
normalize-audio_0.7.7-2_i386.deb
ntfs-config_0.5.5-0ubuntu1_i386.deb
peazip_2.0.bin.LINUX.GTK2.i586-1.deb
python-cairo_1.4.0-2ubuntu2_i386.deb
python-gconf_2.22.0-0ubuntu1_i386.deb
python-glade2_2.12.1-0ubuntu1_i386.deb
python-gnome2_2.22.0-0ubuntu1_i386.deb
python-gnomecanvas_2.22.0-0ubuntu1_i386.deb
python-gtk2_2.12.1-0ubuntu1_i386.deb
python-numeric_24.2-8ubuntu2_i386.deb
python-pyorbit_2.14.3-2ubuntu1_i386.deb
scrollkeeper_0.3.14-15ubuntu1_i386.deb
sgml-base_1.26_all.deb
sgml-data_2.0.3_all.deb
shared-mime-info_0.23-5_i386.deb
sox_14.0.0-5_i386.deb
synaptic_0.61ubuntu9_i386.deb
transcode_2%3a1.0.2-0.8ubuntu7_i386.deb
ttf-dejavu_2.23-1_all.deb
ttf-dejavu-extra_2.23-1_all.deb
vcdimager_0.7.23-4ubuntu1_i386.deb
vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
vlc-nox_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
vlc-plugin-pulse_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
w32codecs_20071007-0medibuntu2_i386.deb
xml-core_0.11_all.deb
------------------------------------------------------------------------------------------

---

### Post by nucleuskore on 2008-06-01
Server database error, post deleted

---

### Post by nucleuskore on 2008-06-03
Hi everyone
Here is the update for June 2008. I have included not just the earlier multimedia packages but a full system upgrade. 

File to download: UbuKuXu-aptoncd-20080601-CD1.iso (266.7 MB)
[Bittorrent](http://www.linuxrocks.in/torrents/UbuKuXu-aptoncd-20080601-CD1.iso.torrent) (minimum seeding time 0130 to 1630 hours GMT, weather permitting)
[Massmirror - Direct Download](http://massmirror.com/b10b3a9d84320badc01bdcf90f22d92d.html)

FTP Download
Method 1: Click [here](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-aptoncd-20080601-CD1.iso) to open in your browser and download
Method 2: For those familiar with ftp use an ftp client or a download manager
Server: dart.ftpcontrol.net
Port: 21
Username: nucleuskore1
Password:EllarigE

Alternate download method**

md5sum af39c1d96ceee3d69ff4ad7a808e31a6

After searching and marking all the packages as described in the [above posts](http://ubuntuforums.org/showthread.php?t=795859#4), **before** clicking the apply button to start the install, you have to click on the mark all upgrades or upgrade all button. This will automatically mark all available updates. Then click Apply to apply the changes and start the install.

After the install reboot the system as this contains a kernel update.

Enjoy your Ubuntu/Kubuntu/Xubuntu !!!

[img]http://farm3.static.flickr.com/2073/2123380344_f192929251_o.png[/img]
-------------------------------------------------------------------------------------------------------------------------------
**Alternate download method:
I have broken the iso into three parts, 2x99MB and one 68.67 MB. Download these three part files to your desktop:
xaa [Mirror1](http://www.mediafire.com/?mfnypjg1jsn) [Mirror2](http://rapidshare.com/files/119796735/xaa)
xab [Mirror1](http://www.mediafire.com/?wlxttmmeyeb) [Mirror2](http://rapidshare.com/files/119785128/xab)
xac [Mirror1](http://www.mediafire.com/?s3b3kk9vwkt) [Mirror2](http://rapidshare.com/files/119690784/xac)

We are now going to use a terminal to assemble the file. Do not be afraid, the command line is your friend !

Tip: when you are keying in the name of a file in the current folder that you are in, just type the partial name and press the Tab key once; if the file name is unique it will autocomplete :)

Press Alt and F2, and type
gnome-terminal (in Ubuntu)
konsole (in Kubuntu)
xterm (in Xubuntu)
By default you will now be in your home folder. We now want to navigate to the desktop where you saved your downloaded files.

Type
cd Desktop
and press ENTER. Note that the D of Desktop is in capitals. Linux is case sensitive - Desktop is not the same as desktop

Type
ls
and press ENTER. You should see the three files xaa xab and xac, besides other files if any on your desktop.

Type
md5sum xa*
and press ENTER. You should see the following output

b2cb479eb2ae99d4127dd9b823ada1e1  xaa
341d5c8c34b77e1f785c982d1dd4c9f8  xab
a6d2b9dd88c1b13aaa80d77554b83bb9  xac

that is, the md5sum with the corresponding filename. This means your files are ok, if any of them differ then that particular part file has got corrupted during download and will have to be redownloaded.

If all is well, type
cat xa* > 20080601.zip
and press ENTER. Wait till you get the prompt back, the file 20080601.zip will be assembled on your desktop.

Type
ls
and press ENTER. You should see the file 20080601.zip among other files on your desktop.

Type
unzip 20080601.zip
and press ENTER. The iso file will get extracted to your desktop :)

Type
ls
and press ENTER. You should see the file UbuKuXu-aptoncd-20080601-CD1.iso among other files on your desktop.

Type
md5sum UbuKuXu-aptoncd-20080601-CD1.iso
and press ENTER. (Hint: use the TAB key to autocomplete !) 
You should get the following value af39c1d96ceee3d69ff4ad7a808e31a6
This means your download is fine, you can now write it to a cd using the default cd burning software of your distro.

---

### Post by nucleuskore on 2008-06-14
FTP links added :)
Will release on ftp now on, next release due on July 1st 2008.

---

### Post by jinsujais on 2008-06-15
Hi sir,

please compile and put all ur programs in: [www.orbitfiles.com](www.orbitfiles.com)

---

### Post by nucleuskore on 2008-06-30
Hi
Here is the update for this month, July 2008

[FTP Download](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-aptoncd-20080701-CD1.iso)
md5sum 7323e4b66a9768eadb6caffbf3f69aeb
Size: 438.1 MB

Am rewriting the earlier post, will update shortly

Here is the package list
glipper (Ubuntu)
htop 
kchmviewer
evince
mplayer
kmplayer
mozilla-mplayer plugin
audacious
k3b
libk3b2-extracodecs
normalize-audio
sox
vcdimager
devede
audacity
avidemux
ffmpeg
ffmpegthumbnailer
transcode
ntfsconfig
vlc
libdvdcss
w32codecs
peazip
compizconfig-settings
ubuntu-restricted (Ubuntu only)
kubuntu-restricted (Kubuntu only)
xubuntu-restricted (Xubuntu only)

Instructions same as earlier except for the following variation:
After marking all the above packages for install, click upgrade all button and click mark. [b]Then, if you do not have an internet connection or do not wish to download anything search for the following

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b]

Click Apply

---

### Post by nucleuskore on 2008-07-30
Hi all
I have modified this release a little. No I've included two ISOs
[list=1]
[*]only multimedia packages
[*] multimedia packages + default system updates[/list]

So you can download whichever suits your needs the best :)

**Application list (August 2008):**

**htop** - an extension of top for viewing system processes

**kchmviewer** - a CHM viewer

**evince** (for Kubuntu only) - a pdf viewer

**mplayer** - a multimedia player

**kmplayer (for Kubuntu only)** - instead of Mplayer. If you install firefox then do install mozilla-mplayer

**firefox**(for Kubuntu only as it does not have firefox)

**mozilla-mplayer plugin** - Mplayer plugin for firefox

**audacious** - a winamp look-alike

**k3b** - burn baby burn, CD/DVD burning

**libk3b2-extracodecs** - extra codecs for K3b

**normalize-audio** - needed for K3b

**sox** - needed for K3b

**vcdimager** - needed for K3b

**devede** - DVD authoring

**audacity** - sound file editor

**avidemux** - A demuxer, similar to VirtualDub

**ffmpeg** - CLI video encoder

**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite

**transcode** - CLI video encoder

**ntfs-config** - Easy configuration to mount and write to internal/external ntfs drives

**vlc** - multimedia player

**libdvdcss2** - dvd decryptor

**w32codecs** - required for Mplayer and Kaffeine

**peazip** - an archiving tool like Winzip

**wine** - a Windows emulator

**ubuntu-restricted (Ubuntu only)**

**kubuntu-restricted (Kubuntu only)** 

**xubuntu-restricted (Xubuntu only)** 



**Instructions:**

[list]

  [*]Download one of these iso files
    [list]

      [*]Packages listed above **without** default system upgrade

[FTP Download](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-aptoncd-20080729-CD1.iso) md5sum 3aa1802ee71ea98a2931d814913cfbb9 Size: 168.9 MB

[*]Packages listed above **with** default system upgrade

I have split this iso into six peices to facilitate easy download.
Mediafire.com supports download managers so don't worry.

        [list]

[*][Piece 1](http://www.mediafire.com/?bjwj9ueoxje)
[*][Piece 2](http://www.mediafire.com/?v2yoxwthnzw)
[*][Piece 3](http://www.mediafire.com/?fg2byftnoo9)
[*][Piece 4](http://www.mediafire.com/?mjyyhnyzaoe)
[*][Piece 5](http://www.mediafire.com/?imapz43kddt)
[*][Piece 6](http://www.mediafire.com/?xngcimtjlwv)

[/list]
[/list]

We are now going to use a terminal to assemble the file. Do not be afraid, the command line is your friend !
**Tip:** when you are keying in the name of a file in the current folder that you are in, just type the partial name and press the Tab key once; if the file name is unique it will autocomplete

Press Alt and F2, and type

gnome-terminal (in Ubuntu)

konsole (in Kubuntu)

xterm (in Xubuntu)

By default you will now be in your home folder. We now want to navigate to the desktop where you saved your downloaded files.


Type

cd Desktop

and press ENTER.

Note that the D of Desktop is in capitals. Linux is case sensitive -
Desktop is not the same as desktop


Type

ls

and press ENTER.

You should see the six files, aug_32_2008_aa to aug_32_2008_af, besides other files if any on your desktop.


Type

md5sum aug_32_2008_a*

and press ENTER. You should see the following output

f71983da44b471f3abb76780220b2495 aug_32_2008_aa
c303fac1c90efc1005d77547d89f0041 aug_32_2008_ab
c232ecb884341df30876ddad7d8d3b5e aug_32_2008_ac
fe1133497f9eae08f6f88e762bff372f aug_32_2008_ad
c27a5d43348ec530238072238c7c339c aug_32_2008_ae
02a7d2950737bfd1b605d4c48b3bf94c aug_32_2008_af

that is, the md5sum with the corresponding filename.

This means your files are ok, if any of them differ then that particular part file has got corrupted during download and will have to be redownloaded.


If all is well, type

cat aug_32_2008_a* > upgrade.iso

and press ENTER. 

Wait till you get the prompt back, the file upgrade.iso will be assembled on your desktop.


Type

ls

and press ENTER.

You should see the file upgrade.iso among other files on your desktop.


Type

md5sum upgrade.iso

and press ENTER.

You should get the following value a6f07b2fb7593d5c29e0c6a75c4148df

This means your download is fine, you can now write it to a cd using the default cd burning software of your distro.

  [*]Burn iso to a cd

***Ubuntu specific instructions:***
    
[*]Insert cd, it will open in nautilus along with this
prompt
    
[[img]http://img146.imageshack.us/img146/2990/89697775yf4.th.png[/img]](http://img146.imageshack.us/my.php?image=89697775yf4.png) 

[*]Click start package manager, when you do that you will be prompted for your password

[[img]http://img146.imageshack.us/img146/2655/68918326kr4.th.png[/img]](http://img146.imageshack.us/my.php?image=68918326kr4.png)

Key in your password and press ENTER

[*]CLose the quick introduction dialog box

[[img]http://img146.imageshack.us/img146/8769/12mm8.th.png[/img]](http://img146.imageshack.us/my.php?image=12mm8.png)

[*]Now you will see the Synaptic Package Manager. Click the search button and search for each of the above applications for your distro. When you find them click and mark for installation.

As you mark them you will see dependency warning dialog boxes, select mark

[[img]http://img175.imageshack.us/img175/1192/66639439hd2.th.png[/img]](http://img175.imageshack.us/my.php?image=66639439hd2.png)

If you downloaded the upgrade iso, after marking all the above packages for install, click upgrade all button and click mark. 
[b]Then, if you do not have an internet connection or do not wish to download anything search for the following

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b]

[*]Click Apply. The installation will proceed

[[img]http://img175.imageshack.us/img175/8755/84836551os5.th.png[/img]](http://img175.imageshack.us/my.php?image=84836551os5.png)

8. After everything is installed click Close

[[img]http://img175.imageshack.us/img175/1381/45563161ib1.th.png[/img]](href="http://img175.imageshack.us/my.php?image=45563161ib1.png)

[/list]

Enjoy your Ubuntu !

---

### Post by nucleuskore on 2008-07-30
***Xubuntu specific instructions:***
[list=3]

  [*]Insert cd, it will open in Thunar along with this prompt

[[img]http://img291.imageshack.us/img291/5707/01aq7.th.png[/img]](http://img291.imageshack.us/my.php?image=01aq7.png)  

  [*]Click start package manager, when you do that you will be prompted for your password

[[img]http://img291.imageshack.us/img291/7646/02bj7.th.png[/img]](http://img291.imageshack.us/my.php?image=02bj7.png)

Key in your password and press ENTER

[*]CLose the quick introduction dialog box

[[img]http://img183.imageshack.us/img183/6505/03ex5.th.png[/img]](http://img183.imageshack.us/my.php?image=03ex5.png)

[*]Now you will see the Synaptic Package Manager. Click the
search button and search for each of the applications listed above for
your distro. When you find them click and mark for installation.

[[img]http://img183.imageshack.us/img183/8321/04al4.th.png[/img]](http://img183.imageshack.us/my.php?image=04al4.png)[[img]http://img183.imageshack.us/img183/4774/05of5.th.png[/img]](http://img183.imageshack.us/my.php?image=05of5.png)[[img]http://img183.imageshack.us/img183/4529/06hz4.th.png[/img]](href="http://img183.imageshack.us/my.php?image=06hz4.png)

As you mark them you will see dependency warning dialog boxes, select mark

[[img]http://img149.imageshack.us/img149/4043/07lb8.th.png[/img]](http://img149.imageshack.us/my.php?image=07lb8.png)

If you downloaded the upgrade iso, after marking all the above packages for install, click upgrade all button and click mark. [b]Then, if you do not have an internet connection or do not wish to download anything search for the following 

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b][/list]

---

### Post by nucleuskore on 2008-07-30
[list=4][*]Click Apply. The installation will proceed

[[img]http://img384.imageshack.us/img384/9788/08pz8.th.png[/img]](href="http://img384.imageshack.us/my.php?image=08pz8.png)[[img]http://img384.imageshack.us/img384/7209/09hu1.th.png[/img]](http://img384.imageshack.us/my.php?image=09hu1.png)[[img]http://img329.imageshack.us/img329/3341/10ny7.th.png[/img]](http://img329.imageshack.us/my.php?image=10ny7.png)[[img]http://img329.imageshack.us/img329/180/11cd1.th.png[/img]](http://img329.imageshack.us/my.php?image=11cd1.png)

[*]After everything is installed click Close

[[img]http://img329.imageshack.us/img329/2876/12rq4.th.png[/img]](http://img329.imageshack.us/my.php?image=12rq4.png)  

[/list]

Enjoy your Xubuntu !

<hr>


***Kubuntu specific instructions:***
[list=3]

[*]Insert cd, you will see a prompt onscreen

[[img]http://img355.imageshack.us/img355/4436/01qf2.th.png[/img]](http://img355.imageshack.us/my.php?image=01qf2.png)    

Select Open in new window; a new window opens as below

[[img]http://img355.imageshack.us/img355/7472/02mt8.th.png[/img]](http://img355.imageshack.us/my.php?image=02mt8.png)    

Minimise it.

[*]Click start (KMenu)->System->Adept Manager, when you do that you will be prompted for your password

[[img]http://img355.imageshack.us/img355/2131/03co9.th.png[/img]](http://img355.imageshack.us/my.php?image=03co9.png)

Key in your password and press ENTER

---

### Post by nucleuskore on 2008-07-30
[*]Now you will see the Adept Package Manager. 

[[img]http://img370.imageshack.us/img370/8623/04md7.th.png[/img]](http://img370.imageshack.us/my.php?image=04md7.png)

[*]Click Adept -&gt; Manage Repositories

[[img]http://img106.imageshack.us/img106/4774/05sf2.th.png[/img]](http://img106.imageshack.us/my.php?image=05sf2.png)  

[*]You will see this

[[img]http://img370.imageshack.us/img370/6748/06cy9.th.png[/img]](http://img370.imageshack.us/my.php?image=06cy9.png)

[*] Click on the,"Third-Party Software" tab, and click Add CD-ROM

[[img]http://img106.imageshack.us/img106/1104/07ul3.th.png[/img]](http://img106.imageshack.us/my.php?image=07ul3.png)    

You will see this dialog box

[[img]http://img229.imageshack.us/img229/4417/08ir2.th.png[/img]](http://img229.imageshack.us/my.php?image=08ir2.png)

Insert the CD you made in step 2; the following gets added automatically

[[img]http://img229.imageshack.us/img229/3874/09hb1.th.png[/img]](href="http://img229.imageshack.us/my.php?image=09hb1.png)

In the search box type and search for each of the applications listed above for your distro. When you find them right click and mark for installation.

[[img]http://img410.imageshack.us/img410/3606/10sx4.th.png[/img]](http://img410.imageshack.us/my.php?image=10sx4.png)

If you downloaded Upgrade_UbuKuXu-aptoncd-20080729-CD1.iso, after marking all the above packages for install, click upgrade all button and click mark. [b]Then, if you do not have an internet connection or do not wish to download anything search for the following

flashplugin-nonfree
msttcorefonts

and unmark them so that they will not be installed.[/b]

---

### Post by nucleuskore on 2008-07-30
[*] Click Apply Changes. The installation will proceed

[[img]http://img258.imageshack.us/img258/3558/11by3.th.png[/img]](http://img258.imageshack.us/my.php?image=11by3.png)[[img]http://img258.imageshack.us/img258/183/12gl0.th.png[/img]](http://img258.imageshack.us/my.php?image=12gl0.png)

[*]After everything is installed close adept

[/list]

Enjoy your Kubuntu !

---

### Post by nucleuskore on 2008-08-30
Hi all
I've included two ISOs
   1. only multimedia packages
   2. multimedia packages + default system updates

So you can download whichever suits your needs the best

Application list (September 2008 )

htop - an extension of top for viewing system processes

kchmviewer - a CHM viewer

evince (for Kubuntu only) - a pdf viewer

mplayer - a multimedia player

kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer

firefox(for Kubuntu only as it does not have firefox)

mozilla-mplayer plugin - Mplayer plugin for firefox

audacious - a winamp look-alike

k3b - burn baby burn, CD/DVD burning

libk3b2-extracodecs - extra codecs for K3b

normalize-audio - needed for K3b

sox - needed for K3b

vcdimager - needed for K3b

devede - DVD authoring

audacity - sound file editor

avidemux - A demuxer, similar to VirtualDub

ffmpeg - CLI video encoder

ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite

transcode - CLI video encoder

ntfs-config - Easy configuration to mount and write to internal/external ntfs drives

vlc - multimedia player

libdvdcss2 - dvd decryptor

w32codecs - required for Mplayer and Kaffeine

peazip - an archiving tool like Winzip

wine - a Windows emulator

ubuntu-restricted (Ubuntu only)

kubuntu-restricted (Kubuntu only)

xubuntu-restricted (Xubuntu only)

Instructions:
Download one of these iso files

Packages listed above without default system upgrade
Rapidshare link: [http://rapidshare.com/files/145159551/UbuKuX-aptoncd-20080914-CD1.iso](http://rapidshare.com/files/145159551/UbuKuX-aptoncd-20080914-CD1.iso)
md5sum e1aa5365d29d473f55579fdc096251fd 

Packages listed above with default system upgrade - I have split this iso into five pieces to facilitate easy download.
Mediafire.com supports download managers so don't worry. md5sums mentioned in file info box at site

[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca6628d02152812542](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca6628d02152812542)

Read Post #14 for detailed instructions.

---

### Post by nucleuskore on 2008-10-02
Hi all
I've included two ISOs
   1. only multimedia packages
   2. multimedia packages + default system updates

So you can download whichever suits your needs the best

Application list (October 2008 )

htop - an extension of top for viewing system processes

kchmviewer - a CHM viewer

evince (for Kubuntu only) - a pdf viewer

mplayer - a multimedia player

kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer

firefox(for Kubuntu only as it does not have firefox)

mozilla-mplayer plugin - Mplayer plugin for firefox

audacious - a winamp look-alike

k3b - burn baby burn, CD/DVD burning

libk3b2-extracodecs - extra codecs for K3b

normalize-audio - needed for K3b

sox - needed for K3b

vcdimager - needed for K3b

devede - DVD authoring

audacity - sound file editor

avidemux - A demuxer, similar to VirtualDub

ffmpeg - CLI video encoder

ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite

transcode - CLI video encoder

ntfs-config - Easy configuration to mount and write to internal/external ntfs drives

vlc - multimedia player

libdvdcss2 - dvd decryptor

w32codecs - required for Mplayer and Kaffeine

peazip - an archiving tool like Winzip

wine - a Windows emulator

ubuntu-restricted (Ubuntu only)

kubuntu-restricted (Kubuntu only)

xubuntu-restricted (Xubuntu only)

Instructions:
Download one of these iso files

Packages listed above without default system upgrade
[small-aptoncd-20081001-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/small-aptoncd-20081001-CD1.iso) md5sum 2e025f02d42ce586ed99cccc6df00318 

Packages listed above with default system upgrade - I have split this iso into six pieces to facilitate easy download.
Mediafire.com supports download managers so don't worry. md5sums mentioned in file info box at site

[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca935164b1d9a7c2e9](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca935164b1d9a7c2e9)

Read Post #14 for detailed instructions.

---

### Post by nucleuskore on 2008-11-02
Hi all
I've included two ISOs
   1. only multimedia packages
   2. multimedia packages + default system updates

So you can download whichever suits your needs the best

Application list (November 2008 )

htop - an extension of top for viewing system processes

kchmviewer - a CHM viewer

evince (for Kubuntu only) - a pdf viewer

mplayer - a multimedia player

kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer

firefox(for Kubuntu only as it does not have firefox)

mozilla-mplayer plugin - Mplayer plugin for firefox

audacious - a winamp look-alike

k3b - burn baby burn, CD/DVD burning

libk3b2-extracodecs - extra codecs for K3b

normalize-audio - needed for K3b

sox - needed for K3b

vcdimager - needed for K3b

devede - DVD authoring

audacity - sound file editor

avidemux - A demuxer, similar to VirtualDub

ffmpeg - CLI video encoder

ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite

transcode - CLI video encoder

ntfs-config - Easy configuration to mount and write to internal/external ntfs drives

vlc - multimedia player

libdvdcss2 - dvd decryptor

w32codecs - required for Mplayer and Kaffeine

peazip - an archiving tool like Winzip

wine - a Windows emulator

ubuntu-restricted (Ubuntu only)

kubuntu-restricted (Kubuntu only)

xubuntu-restricted (Xubuntu only)

Instructions:
Download one of these iso files

Packages listed above without default system upgrade (8.04 only)
[small-aptoncd-20081101-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/small-aptoncd-20081101-CD1.iso) 
md5sum ffdc50491b532f48dc9b042ee2a6a3ec 

Packages listed above with default system upgrade - 

8.10 ISO is a single direct download (ISO).
**Ubuntu/Kubuntu/Xubuntu 8.10**
[large-8.10-aptoncd-20081102-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/large-8.10-aptoncd-20081102-CD1.iso)
md5sum 1f1281ba0d84ae5cc75ba417d3952168

I have split this iso into six pieces, for 8.04, to facilitate easy download. Mediafire.com supports download managers so don't worry. md5sums mentioned in file info box at site.
**Ubuntu/Kubuntu/Xubuntu 8.04**
Coming soon....[]()

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2008-12-06
Hi all
I've included two ISOs
   1. only multimedia packages
   2. multimedia packages + default system updates

So you can download whichever suits your needs the best

Application list (December 2008 )
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b2-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]w32codecs - required for Mplayer and Kaffeine
[*]peazip - an archiving tool like Winzip
[*]wine - a Windows emulator
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:
Download one of these iso files

Packages listed above without default system upgrade 
**8.04**
[UbuKuXu-32bit-small-aptoncd-20081205-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-32bit-small-aptoncd-20081909-CD1.iso) 
md5sum eb837de94b7d57915844a3473154d658 

**8.10**
[UbuKuXu-8.10-32bit-small-aptoncd-20081206-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-32bit-small-aptoncd-20081206-CD1.iso) 
md5sum bcaae79b191399edfa72ec05aba04526 

Packages listed above with default system upgrade -

For 8.04
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d26e415ea26c7df845](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d26e415ea26c7df845)

058a75368682c3bc8db8d834755ba668  05122008_8.04_aa
493fe57adeb288e56d490dd63ddd0db6  05122008_8.04_ab
facc02338197c542184c12ff3bb70e40  05122008_8.04_ac
c94882ddc583d302f8203120a73cca39  05122008_8.04_ad
d965e41574e843df27f81dc08d2a30d1  05122008_8.04_ae
c2e5f58ad09f5cbd51cd9e832190dc77  05122008_8.04_af
38f87d4abece34525d20408354ed0ca1  05122008_8.04_ag

For 8.10
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2888c3155185b5fa7](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2888c3155185b5fa7) 

5e83cf9c39e59b3d63028d15265665bc 06122008_8.10_aa
d7c61310b1b10468958dd094dd75824c 06122008_8.10_ab
1ba003085077fcf97483f6e9ff6c3ddb 06122008_8.10_ac
139233d940f4f45f27ba50828d6da004 06122008_8.10_ad
e6adfeeab6a1be96a40947b6ed8b9955 06122008_8.10_ae

md5sums for final image after assembling
You should get the following value 1a7615721d0c3b72ab630a07469669cc for 8.04 and 6de8d62025760e996f10b311332a6c85 for 8.10

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2009-01-06
Happy New Year !
I've included two ISOs
   1. only multimedia packages
   2. multimedia packages + default system updates

So you can download whichever suits your needs the best

Application list (January 2009 )
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b2-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]w32codecs - required for Mplayer and Kaffeine
[*]peazip - an archiving tool like Winzip
[*]wine - a Windows emulator
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:
Download one of these iso files

Packages listed above without default system upgrade 
**8.04**
[UbuKuXu-8.04-small-32bit-aptoncd-20090103-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-small-32bit-aptoncd-20090103-CD1.iso) 
md5sum db67138bcf00717007cdaada2f3fa893 

**8.10**
[UbuKuXu-8.10-small-32bit-aptoncd-20090104-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-32bit-aptoncd-20090104-CD1.iso) 
md5sum f1d4fef308265389624883845ac102da 

Packages listed above with default system upgrade -

For 8.04
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2b354fbde708aee36](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d2b354fbde708aee36)
2563c9ee61671392c37461a98212d6b3  aa
72208dab09eee1417ea8583c615d275a  ab
55575c9e20d6a988bd183590d71f9442  ac
e6a5256cc261837701b76eda5229e2b7  ad
969c2904fa4ef2bc96b2608ed7405763  ae
d117dc7c573585490a6f97a2332b6c14  af
4f43b0204dc8ef0ebe6185815df6c0a1  ag

For 8.10
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d281de0ac319495fdd](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e891b20cc0d07ba4d281de0ac319495fdd) 

2c7169a7c85f1ab9ed8ed3766d14acc7  aa
57729f9394a6095a365c66b4f23a5849  ab
879b8c81f9cd11ba65a2b954378190be  ac
9d829af1c0e7b6a6e692d575c1284ae2  ad
4a6441c30963b308f3ae60125d36c70a  ae
2201af1b5b7acab15afc22ba278d4de6  af

md5sums for final image after assembling
You should get the following value 41aa153a80032bb4756ec08d4ac8f526 for 8.04 and a18fa3953529f40fa6106808becaba4b for 8.10

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2009-04-11
Happy Easter !
Updates after a period of absence.

At the moment I have only included the multimedia packages without the system upgrade. Will add that too once it's uploaded. 

Application list (April 2009 )
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b2-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]w32codecs - required for Mplayer and Kaffeine
[*]peazip - an archiving tool like Winzip
[*]wine - a Windows emulator
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:
Download one of these iso files

Packages listed above without default system upgrade 
**8.04**
[UbuKuXu-8.04-small-32bit-aptoncd-20090411-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.04-small-32bit-aptoncd-20090411-CD1.iso) 
md5sum 6b414cd4542cbd69572f7fc4c6c6bb9a 

**8.10**
[UbuKuXu-8.10-small-32bit-aptoncd-20090410-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-32bit-aptoncd-20090410-CD1.iso) 
md5sum 4ca42ec6915ef7ef02b3a9ca6f56e316 

**9.04**
[UbuKuXu-8.10-small-32bit-aptoncd-20090410-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-9.04-small-32bit-aptoncd-20090501-CD1.iso)
md5sum d66b251ca159d5b05a7f96135900549c

Packages listed above with default system upgrade -

For 8.04
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e88c9e7c56ba37815f3ff621612e7e7499](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e88c9e7c56ba37815f3ff621612e7e7499)

For 8.10
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e88c9e7c56ba37815f8cacf691de5b354c](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e88c9e7c56ba37815f8cacf691de5b354c) 

md5sums for final image after assembling
You should get the following value 3c3962bd665f50370cf2d5ef5dd47abc for 8.04 and d0bc22cb4fa685698fd640eec88e7fec for 8.10

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by liquerLOVER on 2009-04-13
hi... since linux mint 6 is based on ubuntu 8.10, does that mean that i can use your cd for linux mint?

next, my download is really slow (5-7 kBps) from [ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-32bit-aptoncd-20090410-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/UbuKuXu-8.10-small-32bit-aptoncd-20090410-CD1.iso). but from other site (i downloaded g4l), my download can go to 1++ kBps. is it the link or my ip that make my download slow. 

and the mediafire link (december 2008 dependencies)seems like stuck@dead. i wait for a long time but nothing come out. is it dead already?

thank you

---

### Post by nucleuskore on 2009-04-17
^Updated

---

### Post by nucleuskore on 2009-05-01
^Packages for Jaunty Jackalope added !

---

### Post by nucleuskore on 2009-07-03
From this release onwards, July 2009, all the isos of the current stable release, Jaunty (*buntu 9.04) as of now, will be placed on the fast ftp server for download. Here is the updated list of applications 

Application list (July 2009 )
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b2-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]w32codecs - required for Mplayer and Kaffeine
[*]peazip - an archiving tool like Winzip
[*]wine - a Windows emulator
[*]ttf-liberation
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:
Download one of these iso files

Packages listed above without default system upgrade 
**8.04**
[http://www.zshare.net/download/6219213385f67309/]() 
md5sum  e87b1ece11a36330404ce954c82559c8
**8.10**
[http://www.zshare.net/download/62206660296740b7/]() 
md5sum  00c862a9654d6fbc5f2fc5db57ffe747

**9.04**
[Ubuntu-9.04-32bit-July2009-small-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-32bit-July2009-small-CD1.iso)
md5sum d62a1b40d0a88e3db87590bd1f5cb982

Packages listed above with default system upgrade -

For 8.04
[http://www.zshare.net/download/6221873616b18171/](http://www.zshare.net/download/6221873616b18171/)
md5sum de97b34853081ee5904647607aa096d8

For 8.10
[http://www.zshare.net/download/62209997b233b895/](http://www.zshare.net/download/62209997b233b895/) 
md5sum ffd494e975a43c914cfa053bca8728a8

For 9.04
[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-32bit-July2009-large-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-32bit-July2009-large-CD1.iso)
md5sum 008001ef624ffb9cea3b62d593d8e062 

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)[/QUOTE]

---

### Post by nucleuskore on 2009-08-02
Here is the updated list of applications 

Application list (August 2009 )
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b2-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w32codecs - required for Mplayer and Kaffeine
[*]peazip - an archiving tool like Winzip
[*]wine - a Windows emulator
[*]ttf-liberation
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:
Download one of these iso files

Packages listed above without default system upgrade 
**8.04**
[http://www.zshare.net/download/6352457734ca8b9b/]() 
md5sum  1a759fd88c07cd78b2ef7fbeb1374c0a

**8.10**
[http://www.zshare.net/download/6352499619942883/]() 
md5sum  76311961710ca707a76652f0b6ad5a6f

**9.04**
[Ubuntu-9.04-32bit-July2009-small-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-32bit-August2009-small-CD1.iso)
md5sum 27da755c2bd81ffaee7c6424d04c5312

Packages listed above with default system upgrade -

For 8.04
[http://www.zshare.net/download/64080789f4228e2a/](http://www.zshare.net/download/64080789f4228e2a/)
md5sum 8b8f15288647f598c89ece4a5f85e304

For 8.10
[http://www.zshare.net/download/640820081e7ba374/](http://www.zshare.net/download/640820081e7ba374/) 
md5sum 60f18d2536a2494adaf03dc592d6390f

For 9.04
[ftp://dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-32bit-August2009-large-CD1.iso](ftp://dart.ftpcontrol.net/ubuntu/Ubuntu-9.04-32bit-August2009-large-CD1.iso)
md5sum c4fdf2f3d0c0b4dd6221d7ed1a86584d 

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)[/QUOTE][/QUOTE]

---

### Post by nucleuskore on 2009-12-02
Hi everybody :(

Was in a transition phase, moving from India to Antigua. That's why I was not to be seen. Yes, I am in Antigua ! Land of sea and sun as they say. Am working for the American University of Antigua. Hope to be updating my packages threads regularly from January next year.

Am still trying to get my broadband connection here. I got the router day before yesterday from APUA, and they told me that it will take another four days to activate the line :-P
And unlike in India, they just give you your boxed new configured router, and a sheet of instructions on how to connect it to your PC. No tech guy come to your place like they do in India.

So till I get a proper broadband connection all my work is shelved.

On a brighter note I am going to get married soon. Will be arriving in India on the 14th of December :)

More on that here
[http://www.alovelycouple.co.cc](http://www.alovelycouple.co.cc)

---

### Post by nucleuskore on 2009-12-06
Hi
Here is the a list of applications. I will be releasing the iso for 9.10 only, due to bandwidth constraints 

Application list (December 2009 )
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b6-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w32codecs - required for Mplayer and Kaffeine
[*]wine - a Windows emulator
[*]ttf-liberation
[*]libavformat-extra-52
[*]libpostproc-extra-51
[*]libswscale-extra-0
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade -

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-32bit-large-aptoncd-20091206-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-32bit-large-aptoncd-20091206-CD1.iso)
 

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2010-01-14
Hi
Here is the a list of applications.  

Application list (January 2010)
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b6-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w32codecs - required for Mplayer and Kaffeine
[*]wine - a Windows emulator
[*]ttf-liberation
[*]libavformat-extra-52
[*]libpostproc-extra-51
[*]libswscale-extra-0
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade. Download all the pieces below and save them to your home folder.

large_aa
md5sum 93ed1f210ece0c85e765fdb6e35a59c0
[http://rapidshare.com/files/335152222/large_aa](http://rapidshare.com/files/335152222/large_aa)

large_ab
md5sum 8a48f6ff858aac8d40259ac2e2598ada
[http://rapidshare.com/files/335154654/large_ab](http://rapidshare.com/files/335154654/large_ab)

large_ac
md5sum f42c46f17904dad6b0b98b92e1daa6c1
[http://rapidshare.com/files/335154658/large_ac](http://rapidshare.com/files/335154658/large_ac)

large_ad
md5sum 17287d414ed92ebbca9e0cf7d81a9552
[http://rapidshare.com/files/335158251/large_ad](http://rapidshare.com/files/335158251/large_ad)

large_ae
md5sum 56e21648f6ea1988e0b15e594684002d
[http://rapidshare.com/files/335158257/large_ae](http://rapidshare.com/files/335158257/large_ae)

large_af
md5sum ea141dc801da1545f13edadc4db74ec4
[http://rapidshare.com/files/335159865/large_af](http://rapidshare.com/files/335159865/large_af)

**Alternatively, download all the above pieces from here** (download manager supported)
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335caf751dcd099371afd](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335caf751dcd099371afd)

To join the above, open a terminal (Press Alt and F2 and type gnome-terminal in Ubuntu, or konsole in Kubuntu, and press ENTER) and type

cat large_a* > large.iso

Burn the large.iso to a cd.

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)[/QUOTE]

---

### Post by nucleuskore on 2010-03-26
Hi
Here is the a list of applications.  

Application list (March 2010)
[list]
[*]htop - an extension of top for viewing system processes
[*]kchmviewer - a CHM viewer
[*]evince (for Kubuntu only) - a pdf viewer
[*]mplayer - a multimedia player
[*]kmplayer (for Kubuntu only) - instead of Mplayer. If you install firefox then do install mozilla-mplayer
[*]firefox(for Kubuntu only as it does not have firefox)
[*]mozilla-mplayer plugin - Mplayer plugin for firefox
[*]audacious - a winamp look-alike
[*]k3b - burn baby burn, CD/DVD burning
[*]libk3b6-extracodecs - extra codecs for K3b
[*]normalize-audio - needed for K3b
[*]sox - needed for K3b
[*]vcdimager - needed for K3b
[*]devede - DVD authoring
[*]audacity - sound file editor
[*]avidemux - A demuxer, similar to VirtualDub
[*]ffmpeg - CLI video encoder
[*]ffmpegthumbnailer - make thumbnails of your movies like in Media Player Classic of Klite
[*]transcode - CLI video encoder
[*]ntfs-config - Easy configuration to mount and write to internal/external [*]ntfs drives
[*]vlc - multimedia player
[*]libdvdcss2 - dvd decryptor
[*]libxine1 - for Kubuntu only
[*]kaffeine - for Kubuntu only
[*]w32codecs - required for Mplayer and Kaffeine
[*]wine - a Windows emulator
[*]ttf-liberation
[*]libavformat-extra-52
[*]libpostproc-extra-51
[*]libswscale-extra-0
[*]ubuntu-restricted (Ubuntu only)
[*]kubuntu-restricted (Kubuntu only)
[*]xubuntu-restricted (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade. Download the iso file from here (Fast FTP Download)

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-32bit-aptoncd-20100324-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-9.10-32bit-aptoncd-20100324-CD1.iso)


Burn the iso to a cd.

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2010-05-19
Hi
Here is the a list of applications for 10.04 (lucid)  

Application list (May 2010)
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**evince** (for Kubuntu)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade. Download the iso file from here (Fast FTP Download)

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.04-32bit-aptoncd-20100519-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.04-32bit-aptoncd-20100519-CD1.iso)


Burn the iso to a cd.

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2010-11-10
Hi
Here is the a list of applications for 10.10  

Application list (November 2010)
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**evince** (for Kubuntu)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade. Download the iso file from here (Fast FTP Download)

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-x86-aptoncd-20101110-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-x86-aptoncd-20101110-CD1.iso)


Burn the iso to a cd.

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2011-01-27
Hi
Here is the a list of applications for 10.10  

Application list
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**evince** (for Kubuntu)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade. Download the iso file from here (Fast FTP Download)

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-32bit-aptoncd-20110127-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-10.10-32bit-aptoncd-20110127-CD1.iso)


Burn the iso to a cd.

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)

---

### Post by nucleuskore on 2011-06-12
Hi
Here is the a list of applications for 11.04  

Application list
[list]
[*]**htop** - an extension of top for viewing system processes
[*]**kchmviewer** - a CHM viewer
[*]**mplayer** - a multimedia player
[*]**gecko-mediaplayer** - a plugin for firefox to handle multimedia
[*]**timidity** - midi player
[*]**mozplugger** - optional but recommended plugin for firefox to handle multimedia
[*]**gimp** - Image editing
[*]**gimp-help-en** - english help file for GIMP, can be skipped
[*]**gimp-data-extras** - install with gimp above
[*]**firefox**(for Kubuntu only as it does not have firefox)
[*]**evince** (for Kubuntu)
[*]**audacious** - a winamp look-alike
[*]**k3b** - burn baby burn, CD/DVD burning
[*]**libk3b6-extracodecs** - extra codecs for K3b
[*]**normalize-audio** - needed for K3b
[*]**sox** - needed for K3b
[*]**vcdimager** - needed for K3b
[*]**devede** - DVD authoring
[*]**audacity** - sound file editor
[*]**avidemux** - A demuxer, similar to VirtualDub
[*]**ffmpeg** - CLI video encoder
[*]**ffmpegthumbnailer** - make thumbnails of your movies like in Media Player Classic of Klite
[*]**transcode** - CLI video encoder
[*]**vlc** - multimedia player
[*]**libdvdcss2** - dvd decryptor
[*]**wine** - a Windows emulator
[*]**ttf-liberation**
[*]**libavformat-extra-52**
[*]**libpostproc-extra-51**
[*]**libswscale-extra-0**
[*]**ubuntu-restricted-extras** (Ubuntu only)
[*]**kubuntu-restricted-extras** (Kubuntu only)
[*]**xubuntu-restricted-extras** (Xubuntu only)[/list]

Instructions:

Packages listed above with default system upgrade. Download the iso file from here (Fast FTP Download)

[ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-11.04-32bit-aptoncd-20110612-CD1.iso](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/UbuKuXu-11.04-32bit-aptoncd-20110612-CD1.iso)


Burn the iso to a cd.

Deployment: See [http://ubuntuforums.org/showthread.php?t=795859&page=2#14](http://ubuntuforums.org/showthread.php?t=795859&page=2#14)[/QUOTE]

---

