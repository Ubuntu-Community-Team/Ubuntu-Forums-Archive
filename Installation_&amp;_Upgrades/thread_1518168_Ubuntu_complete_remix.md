---
title: "Ubuntu complete remix"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by ubun2warrior on 2010-06-26
Hi 

I recently came across the following site: [http://www.ubuntucomplete.co.uk/](http://www.ubuntucomplete.co.uk/)

Next I downloaded the dvd image of ubuntu 10.04 provided there and created a live usb using ubuntu's usb disk creator.

The Live dvd has loads of software packages in it. The problem is that it does not offer installation to hard disk. Can anyone tell me how i can turn this live dvd into an install+live disk. 

If the above is complex then at least tell me how i can install all the software  packages to my ubuntu 10.04 installed on my computer.

Regards
Ubun2Warrior

---

### Post by ell02 on 2010-06-26
Use the search in synaptic package manager.They seem to be in there and my sources are pretty tame.

---

### Post by ubun2warrior on 2010-06-29
I want the packages oflline i dont want to download them each time i install ubuntu on any system and the complete remix has loads of packages, it is excellent. I just want to know how i can make an install disk from the live iso that i have....

or at least how i can install the packages to my current ubuntu 10.04 from the complete remix...

PLEASE HELP...

---

### Post by dynamo2 on 2010-06-29
The following will download and install up-to-date packages that are in Ubuntu Complete Remix from the Ubuntu repositories to your Ubuntu installation.

After booting into Ubuntu Complete Remix type in a Terminal:

```
dpkg --get-selections > somefile
```

Copy the file to a USB stick or something so that you can access the file from your Ubuntu installation later on.

Then when booted into your Ubuntu installation do (where somefile is the path and file on your USB stick):

```
sudo dpkg --set-selections < somefile
```

and then:

```
sudo apt-get dselect-upgrade
```

---

### Post by ubun2warrior on 2010-07-06
hi dynamo2

i tried the above commands, but i was unable to install packages. Maybe i was going wrong somewhere. Could you please be more detailed with the above instruction . Plz post a step-by-step procedure with explanations. I am still a beginner here...   Thanks in advance, awaiting ur reply...

Rgds
ubun2warrior

---

### Post by dynamo2 on 2010-07-06
Download the attachment dpkglist.tar.bz2, cd to where you downloaded it in a Terminal e.g. if you downloaded it to /home/ubun2warrior/dpkglist.tar.bz2 do a ```
cd /home/ubun2warrior
```
then to extract the contents of the archive dpklist.tar.bz2:
```
tar xvjf dpkglist.tar.bz2
```
the extracted file is literally called 'somefile.txt' so we do
```
sudo dpkg --set-selections < somefile.txt
```
then do:
```
sudo apt-get dselect-upgrade
```
The last two commands will download and install the up-to-date packages you need which are in UCR 10.04 to your current Ubuntu installation.

---

### Post by WinRiddance on 2010-07-06
> **ubun2warrior said:**
> I want the packages oflline i dont want to download them each time i install ubuntu on any system and the complete remix has loads of packages, it is excellent. I just want to know how i can make an install disk from the live iso that i have....

or at least how i can install the packages to my current ubuntu 10.04 from the complete remix...

PLEASE HELP...

Well, in this day and age of dirt cheap blank CDR disks and readily available internet (almost) everywhere I truly do not understand why you would want such a CD, but you might also want to take a look at this thread here which seems to be the same problem:

[http://ubuntuforums.org/showthread.php?t=1525161](http://ubuntuforums.org/showthread.php?t=1525161)

No matter what you put on a CD for yourself .... it will be outdated within days or weeks anyway. That's just the Ubuntu way and it often involves third party apps too ....

---

### Post by ubun2warrior on 2010-07-07
Hi dynamo2

I did exactly as you said, but this is the error the i get:

clientadapter-java/libnb-svnclientadapter-java_6.7-0ubuntu1_all.deb  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libs/libswingx-java/libswingx-java_1.6-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libs/libswingx-java/libswingx-java_1.6-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/j/javax-servletapi2.3/libservlet2.3-java_4.0-10ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/j/javax-servletapi2.3/libservlet2.3-java_4.0-10ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-ide12-java_6.8-0ubuntu5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-ide12-java_6.8-0ubuntu5_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-javaparser-java/libnb-javaparser-java_6.8-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-javaparser-java/libnb-javaparser-java_6.8-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-java3-java_6.8-0ubuntu5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-java3-java_6.8-0ubuntu5_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-apisupport1-java_6.8-0ubuntu5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-apisupport1-java_6.8-0ubuntu5_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnet-libidn-perl/libnet-libidn-perl_0.12.ds-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnet-libidn-perl/libnet-libidn-perl_0.12.ds-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/liba/libauthen-sasl-perl/libauthen-sasl-perl_2.13-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/liba/libauthen-sasl-perl/libauthen-sasl-perl_2.13-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libx/libxml-stream-perl/libxml-stream-perl_1.22-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libx/libxml-stream-perl/libxml-stream-perl_1.22-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnet-xmpp-perl/libnet-xmpp-perl_1.02-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnet-xmpp-perl/libnet-xmpp-perl_1.02-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libo/liboop/liboop4_1.0-6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libo/liboop/liboop4_1.0-6_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libo/libosip2/libosip2-4_3.3.0-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libo/libosip2/libosip2-4_3.3.0-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libp/libphysfs/libphysfs1_2.0.0-4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libp/libphysfs/libphysfs1_2.0.0-4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.6.2-0ubuntu5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.6.2-0ubuntu5_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.6.2-0ubuntu5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.6.2-0ubuntu5_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.6.2-0ubuntu5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.6.2-0ubuntu5_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qwt/libqwt5-qt4_5.2.0-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qwt/libqwt5-qt4_5.2.0-1build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libr/libregexp-java/libregexp-java_1.5-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libr/libregexp-java/libregexp-java_1.5-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/r/ruli/libruli4_0.33-1.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/r/ruli/libruli4_0.33-1.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sdlgfx/libsdl-gfx1.2-4_2.0.20-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sdlgfx/libsdl-gfx1.2-4_2.0.20-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sdlpango/libsdl-pango1_0.1.2-4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sdlpango/libsdl-pango1_0.1.2-4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sdlperl/libsdl-perl_2.2.5-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sdlperl/libsdl-perl_2.2.5-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.1.1-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.1.1-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-6_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/tidy/libtidy-0.99-0_20091223cvs-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/tidy/libtidy-0.99-0_20091223cvs-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff-tools_3.9.2-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff-tools_3.9.2-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_2.2.6b-2ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_2.2.6b-2ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vcdimager/libvcdinfo0_0.7.23-4ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vcdimager/libvcdinfo0_0.7.23-4ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_1.0.6-1ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_1.0.6-1ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore2_1.0.6-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore2_1.0.6-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc2_1.0.6-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc2_1.0.6-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf-bin_0.2.8.4-6.1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf-bin_0.2.8.4-6.1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.5-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.5-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.5-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.5-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.5-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.5-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.17-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.17-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.17-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.17-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.17-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.17-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.17-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.17-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.17-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.17-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-ffmpeg_1.1.17-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-ffmpeg_1.1.17-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.7-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.7-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lifeograph/lifeograph_0.5.6-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lifeograph/lifeograph_0.5.6-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lincity-ng/lincity-ng-data_2.0-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lincity-ng/lincity-ng-data_2.0-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lincity-ng/lincity-ng_2.0-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lincity-ng/lincity-ng_2.0-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/localechooser/localechooser-data_2.12ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/localechooser/localechooser-data_2.12ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu16_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu16_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc3+svn20090426-1ubuntu16_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc3+svn20090426-1ubuntu16_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-nogui_1.0~rc3+svn20090426-1ubuntu16_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-nogui_1.0~rc3+svn20090426-1ubuntu16_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/terminator/terminator_0.93-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/terminator/terminator_0.93-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.1.5-0ubuntu6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.1.5-0ubuntu6_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.5-5-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/mandvd/mandvd_2.5-5-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mdbtools/mdbtools-gmdb_0.5.99.0.6pre1.0.20051109-6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mdbtools/mdbtools-gmdb_0.5.99.0.6pre1.0.20051109-6_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mingw32-binutils/mingw32-binutils_2.20-0.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mingw32-binutils/mingw32-binutils_2.20-0.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mingw32-runtime/mingw32-runtime_3.15.2-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mingw32-runtime/mingw32-runtime_3.15.2-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mingw32/mingw32_4.2.1.dfsg-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mingw32/mingw32_4.2.1.dfsg-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-gmcs_2.4.4~svn151842-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-gmcs_2.4.4~svn151842-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-2.0-devel_2.4.4~svn151842-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-2.0-devel_2.4.4~svn151842-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-csharp-shell_2.4.4~svn151842-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-csharp-shell_2.4.4~svn151842-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-devel_2.4.4~svn151842-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-devel_2.4.4~svn151842-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/monodoc-base_2.4.4~svn151842-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/monodoc-base_2.4.4~svn151842-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/monodoc-manual_2.4.4~svn151842-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mono/monodoc-manual_2.4.4~svn151842-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/monodevelop/monodevelop_2.2.1+dfsg-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/monodevelop/monodevelop_2.2.1+dfsg-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/moon/moonlight-web-devel_2.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/moon/moonlight-web-devel_2.2-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/monodevelop/monodevelop-moonlight_2.2.1+dfsg-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/monodevelop/monodevelop-moonlight_2.2.1+dfsg-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/moon/moonlight-tools_2.2-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/moon/moonlight-tools_2.2-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mutt/mutt_1.5.20-7ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mutt/mutt_1.5.20-7ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/n/nasm/nasm_2.07-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/n/nasm/nasm_2.07-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/netbeans_6.8-0ubuntu5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/netbeans_6.8-0ubuntu5_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netcat/netcat-traditional_1.10-38_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netcat/netcat-traditional_1.10-38_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netcat/netcat_1.10-38_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netcat/netcat_1.10-38_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/nethack/nethack-common_3.4.3-12ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/nethack/nethack-common_3.4.3-12ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/nethack/nethack-x11_3.4.3-12ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/nethack/nethack-x11_3.4.3-12ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/nrg2iso/nrg2iso_0.4-4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/nrg2iso/nrg2iso_0.4-4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/open-invaders/open-invaders-data_0.3-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/open-invaders/open-invaders-data_0.3-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/open-invaders/open-invaders_0.3-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/open-invaders/open-invaders_0.3-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_3.2.0-7ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_3.2.0-7ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_3.2.0-7ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_3.2.0-7ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-report-builder-bin_3.2.0-7ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-report-builder-bin_3.2.0-7ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-sil-gentium-basic/ttf-sil-gentium-basic_1.1-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-sil-gentium-basic/ttf-sil-gentium-basic_1.1-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-officebean_3.2.0-7ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-officebean_3.2.0-7ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-filter-mobiledev_3.2.0-7ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org-filter-mobiledev_3.2.0-7ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org_3.2.0-7ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openoffice.org/openoffice.org_3.2.0-7ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/ophcrack/ophcrack_3.3.0-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/ophcrack/ophcrack_3.3.0-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/outguess/outguess_0.2-7_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/outguess/outguess_0.2-7_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_9.04~dfsg.1-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_9.04~dfsg.1-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pdfcrack/pdfcrack_0.11-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pdfcrack/pdfcrack_0.11-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pearpc/pearpc_0.4.0-5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pearpc/pearpc_0.4.0-5_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-doc_5.10.1-8ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-doc_5.10.1-8ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/perlmagick_6.5.7.8-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/perlmagick_6.5.7.8-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pyexiv2/python-pyexiv2_0.1.3-6build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pyexiv2/python-pyexiv2_0.1.3-6build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/phatch/phatch-cli_0.2.7-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/phatch/phatch-cli_0.2.7-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/python-wxversion_2.8.10.1-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/python-wxversion_2.8.10.1-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/python-wxgtk2.8_2.8.10.1-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/python-wxgtk2.8_2.8.10.1-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/phatch/phatch_0.2.7-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/phatch/phatch_0.2.7-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.6.6-1ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.6.6-1ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.6.6-1ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.6.6-1ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-audacious/pidgin-audacious_2.0.0-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-audacious/pidgin-audacious_2.0.0-1build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-facebookchat/pidgin-facebookchat_1.64-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-facebookchat/pidgin-facebookchat_1.64-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-festival/pidgin-festival_2.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-festival/pidgin-festival_2.4-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-lastfm/pidgin-lastfm_0.4a-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pidgin-lastfm/pidgin-lastfm_0.4a-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pidgin-libnotify/pidgin-libnotify_0.14-1ubuntu14_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pidgin-libnotify/pidgin-libnotify_0.14-1ubuntu14_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gaim-themes/pidgin-themes_0.2-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gaim-themes/pidgin-themes_0.2-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pingus/pingus-data_0.7.2-4ubuild1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pingus/pingus-data_0.7.2-4ubuild1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pingus/pingus_0.7.2-4ubuild1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pingus/pingus_0.7.2-4ubuild1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine_1.1.42-0ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine_1.1.42-0ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mesa/mesa-utils_7.7.1-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/m/mesa/mesa-utils_7.7.1-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/p/playonlinux/playonlinux_3.7.3-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/p/playonlinux/playonlinux_3.7.3-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/podsleuth/podsleuth_0.6.6-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/podsleuth/podsleuth_0.6.6-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-27_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/psutils/psutils_1.17-27_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/putty/putty-tools_0.60+2009-11-22-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/putty/putty-tools_0.60+2009-11-22-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/putty/putty_0.60+2009-11-22-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/putty/putty_0.60+2009-11-22-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/f/foolscap/python-foolscap_0.5.1+dfsg-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/f/foolscap/python-foolscap_0.5.1+dfsg-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mutagen/python-mutagen_1.15-2build1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mutagen/python-mutagen_1.15-2build1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/python-gpod_0.7.93-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgpod/python-gpod_0.7.93-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/k/keybinder/python-keybinder_0.0.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/k/keybinder/python-keybinder_0.0.4-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/lxml/python-lxml_2.2.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/lxml/python-lxml_2.2.4-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/psyco/python-psyco_1.6-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/psyco/python-psyco_1.6-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pyicu/python-pyicu_0.9-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pyicu/python-pyicu_0.9-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-reportlab/python-renderpm_2.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-reportlab/python-renderpm_2.4-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-reportlab/python-reportlab_2.4-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-reportlab/python-reportlab_2.4-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-reportlab/python-reportlab-accel_2.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-reportlab/python-reportlab-accel_2.4-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-uniconvertor/python-uniconvertor_1.1.4-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-uniconvertor/python-uniconvertor_1.1.4-1build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/utidylib/python-utidylib_0.2-3.2ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/utidylib/python-utidylib_0.2-3.2ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/seabios/seabios_0.5.1-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/seabios/seabios_0.5.1-0ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/v/vgabios/vgabios_0.6c-2ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/v/vgabios/vgabios_0.6c-2ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qemu-kvm/qemu-common_0.12.3+noroms-0ubuntu9_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qemu-kvm/qemu-common_0.12.3+noroms-0ubuntu9_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/q/qemu-kvm/qemu-kvm_0.12.3+noroms-0ubuntu9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/q/qemu-kvm/qemu-kvm_0.12.3+noroms-0ubuntu9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qemu-kvm/qemu_0.12.3+noroms-0ubuntu9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qemu-kvm/qemu_0.12.3+noroms-0ubuntu9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qemu-launcher/qemu-launcher_1.7.4-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qemu-launcher/qemu-launcher_1.7.4-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qorganizer/qorganizer_3.1.4-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qorganizer/qorganizer_3.1.4-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qorganizer/qorganizer-translations_3.1.4-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/q/qorganizer/qorganizer-translations_3.1.4-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.21-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.21-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/rdate/rdate_1.2-4build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/rdate/rdate_1.2-4build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/samba4/registry-tools_4.0.0~alpha8+git20090912-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/samba4/registry-tools_4.0.0~alpha8+git20090912-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/reiserfsprogs/reiserfsprogs_3.6.21-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/reiserfsprogs/reiserfsprogs_3.6.21-1build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/r/rfdump/rfdump_1.6-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/r/rfdump/rfdump_1.6-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/samdump2/samdump2_1.1.1-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/samdump2/samdump2_1.1.1-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/scribus/scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/scribus/scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/secure-delete/secure-delete_3.1-5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/secure-delete/secure-delete_3.1-5_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sendxmpp/sendxmpp_1.20-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sendxmpp/sendxmpp_1.20-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sipcalc/sipcalc_1.1.4-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sipcalc/sipcalc_1.1.4-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/siproxd/siproxd_0.7.2-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/siproxd/siproxd_0.7.2-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sipsak/sipsak_0.9.6-2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sipsak/sipsak_0.9.6-2.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.4.7~dfsg-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.4.7~dfsg-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/smplayer/smplayer_0.6.8-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/smplayer/smplayer_0.6.8-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer-themes/smplayer-themes_0.1.20+dfsg-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer-themes/smplayer-themes_0.1.20+dfsg-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/smplayer/smplayer-translations_0.6.8-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/smplayer/smplayer-translations_0.6.8-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/snes9x/snes9x-gtk_1.52-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/snes9x/snes9x-gtk_1.52-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/snes9x/snes9x-x_1.52-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/snes9x/snes9x-x_1.52-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sound-juicer/sound-juicer_2.28.1-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sound-juicer/sound-juicer_2.28.1-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/steghide/steghide_0.5.1-9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/steghide/steghide_0.5.1-9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/streamripper/streamripper_1.64.6-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/streamripper/streamripper_1.64.6-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/supertux/supertux-data_0.3.3-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/supertux/supertux-data_0.3.3-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/supertux/supertux_0.3.3-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/supertux/supertux_0.3.3-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sysv-rc-conf/sysv-rc-conf_0.99-6_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sysv-rc-conf/sysv-rc-conf_0.99-6_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netkit-ntalk/talk_0.17-14_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netkit-ntalk/talk_0.17-14_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tcpreplay/tcpreplay_3.4.3-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tcpreplay/tcpreplay_3.4.3-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/teeworlds/teeworlds-data_0.5.1-3ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/teeworlds/teeworlds-data_0.5.1-3ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/teeworlds/teeworlds_0.5.1-3ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/teeworlds/teeworlds_0.5.1-3ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netkit-tftp/tftp_0.17-17ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netkit-tftp/tftp_0.17-17ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.4+nobinonly-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.4+nobinonly-0ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xbase-clients_7.5+5ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xbase-clients_7.5+5ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/tightvncserver_1.3.9-6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/tightvncserver_1.3.9-6_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/timidity/timidity_2.13.2-37_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/timidity/timidity_2.13.2-37_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/timidity/timidity-daemon_2.13.2-37_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/timidity/timidity-daemon_2.13.2-37_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/tshark_1.2.7-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/tshark_1.2.7-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-sil-gentium/ttf-sil-gentium_1.02-10_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-sil-gentium/ttf-sil-gentium_1.02-10_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/twolame/twolame_0.3.12-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/twolame/twolame_0.3.12-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_39_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_39_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/u/unetbootin/unetbootin_408-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/u/unetbootin/unetbootin_408-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/u/unetbootin/unetbootin-translations_408-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/u/unetbootin/unetbootin-translations_408-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.9.3-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.9.3-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/u/unrtf/unrtf_0.19.3-1.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/u/unrtf/unrtf_0.19.3-1.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.330-1ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.330-1ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.330-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.330-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_1.0.6-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_1.0.6-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.2.0-6build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.2.0-6build1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/lynx-cur/lynx_2.8.8dev.2-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/lynx-cur/lynx_2.8.8dev.2-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wikipedia2text/wikipedia2text_0.11-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wikipedia2text/wikipedia2text_0.11-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wing/wing-data_0.7-27.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wing/wing-data_0.7-27.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wing/wing_0.7-27.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wing/wing_0.7-27.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/wireshark_1.2.7-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wireshark/wireshark_1.2.7-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wormux/wormux-data_0.8.5-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wormux/wormux-data_0.8.5-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wormux/wormux_0.8.5-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wormux/wormux_0.8.5-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/x/xcftools/xcftools_1.0.7-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/x/xcftools/xcftools_1.0.7-1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xfsprogs/xfsprogs_3.1.0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xfsprogs/xfsprogs_3.1.0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/x/xine-ui/xine-ui_0.99.5+cvs20070914-2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/x/xine-ui/xine-ui_0.99.5+cvs20070914-2.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/xtightvncviewer_1.3.9-6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/xtightvncviewer_1.3.9-6_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/z/zsh/zsh_4.3.10-5ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/z/zsh/zsh_4.3.10-5ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.2ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.2ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/a/album/album_4.06-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/a/album/album_4.06-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/a/album-data/album-data_4.05-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/a/album-data/album-data_4.05-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bomberclone/bomberclone-data_0.11.8-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bomberclone/bomberclone-data_0.11.8-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bomberclone/bomberclone_0.11.8-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bomberclone/bomberclone_0.11.8-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/user-setup/user-setup_1.28ubuntu7_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/user-setup/user-setup_1.28ubuntu7_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/casper/casper_1.236_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/casper/casper_1.236_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/cdrdao/cdrdao_1.2.2-18ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/cdrdao/cdrdao_1.2.2-18ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/c/colorgcc/colorgcc_1.3.2.0-10_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/c/colorgcc/colorgcc_1.3.2.0-10_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libosmesa6_7.7.1-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libosmesa6_7.7.1-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/d/desmume/desmume_0.9.5-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/d/desmume/desmume_0.9.5-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/d/dopewars/dopewars-data_1.5.12-9_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/d/dopewars/dopewars-data_1.5.12-9_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/d/dopewars/dopewars_1.5.12-9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/d/dopewars/dopewars_1.5.12-9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/f/fb-music-high/fb-music-high_0.1.2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/f/fb-music-high/fb-music-high_0.1.2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/f/festvox-kallpc16k/festvox-kallpc16k_1.4.0-5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/f/festvox-kallpc16k/festvox-kallpc16k_1.4.0-5_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/f/flashrom/flashrom_0.9.1+r946-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/f/flashrom/flashrom_0.9.1+r946-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/f/frozen-bubble/frozen-bubble-data_2.2.0-1ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/f/frozen-bubble/frozen-bubble-data_2.2.0-1ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/f/frozen-bubble/frozen-bubble_2.2.0-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/f/frozen-bubble/frozen-bubble_2.2.0-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gnucash/gnucash-common_2.2.9-5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gnucash/gnucash-common_2.2.9-5_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gnucash/gnucash_2.2.9-5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gnucash/gnucash_2.2.9-5_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gnucash-docs/gnucash-docs_2.2.0-3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gnucash-docs/gnucash-docs_2.2.0-3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod-data_0.99.14-2ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod-data_0.99.14-2ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.14-2ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.14-2ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/h/hfsutils/hfsutils_3.2.6-11build3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/h/hfsutils/hfsutils_3.2.6-11build3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/i/iat/iat_0.1.3-7_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/i/iat/iat_0.1.3-7_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b18-1.8-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b18-1.8-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b18-1.8-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b18-1.8-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/lupin/lupin-casper_0.29_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/lupin/lupin-casper_0.29_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/p0f/p0f_2.0.8-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/p0f/p0f_2.0.8-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pymtp/python-pymtp_0.0.4-1.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/pymtp/python-pymtp_0.0.4-1.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sipcrack/sipcrack_0.2-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/sipcrack/sipcrack_0.2-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode-doc_1.1.5-0ubuntu6_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode-doc_1.1.5-0ubuntu6_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/u/udftools/udftools_1.0.0b3-14ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/u/udftools/udftools_1.0.0b3-14ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wipe/wipe_0.21-9_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wipe/wipe_0.21-9_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/y/youtube-dl/youtube-dl_2010.04.04-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/y/youtube-dl/youtube-dl_2010.04.04-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I think that it is trying to upgrade from the online repositries and from the dvd disk..

kindly tell me what to do next!!

Regards
ubun2warrior

---

### Post by dynamo2 on 2010-07-07
You need to be connected to the internet for the process to work.

---

### Post by ezsit on 2010-07-07
While running your liveDVD, why not install the Ubuntu installer

apt-get install ubiquity

Say yes and agree to install. After Ubiquity is installed, it should place an icon in your System menu. See if this works.

---

### Post by ubun2warrior on 2010-07-10
hi ezsit

tried ubiquity... does not work.. 
i also mailed to ucr someone said that he will try to make the next ucr installable

regds
ubun2warrior

---

