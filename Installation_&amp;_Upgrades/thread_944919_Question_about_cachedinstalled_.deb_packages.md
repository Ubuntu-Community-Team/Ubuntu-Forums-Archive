---
title: "Question about cached/installed .deb packages"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by themightymegatron on 2008-10-11
I'm trying to build my own custom Apt-On-CD and I realized I had removed most of the cached .deb packages for all the packages installed on my system (I think by running 'apt-get autoclean/autoremove)! 

Is there a way to re-download the .deb packages for all installed software in synaptic or apt or something? I can only find about 15% of the .debs for my system on my HDD and don't know how to get them back without un/reinstalling everything... 

Here's some bash output for reference if it helps:

[QUOTE=]primus@Cybertron:/var/cache/apt/archives$ ls -a
.
..
alien_8.69_all.deb
app-install-data-commercial_9.3_all.deb
cmake_2.4.7-1build1_i386.deb
compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb
debhelper_6.0.4ubuntu1_all.deb
deskbar-applet_2.22.3.1-0ubuntu1_i386.deb
exim4_4.69-2_all.deb
exim4-base_4.69-2_i386.deb
exim4-config_4.69-2_all.deb
exim4-daemon-light_4.69-2_i386.deb
faac_1.26-0.1ubuntu1_i386.deb
faad_2.6.1-2_i386.deb
faad_2.6.1-2ubuntu0.1_i386.deb
fgfs-base_1.0.0-1_all.deb
firefox_3.0.2+build6+nobinonly-0ubuntu0.8.04.1_all.deb
firefox-3.0_3.0.2+build6+nobinonly-0ubuntu0.8.04.1_i386.deb
firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb
firefox_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_all.deb
firefox-3.0-gnome-support_3.0.2+build6+nobinonly-0ubuntu0.8.04.1_i386.deb
firefox-3.0-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb
firefox-gnome-support_3.0.2+build6+nobinonly-0ubuntu0.8.04.1_all.deb
firefox-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_all.deb
flightgear_1.0.0-1ubuntu1_i386.deb
gdb_6.8-1ubuntu3_i386.deb
html2text_1.3.2a-3build2_i386.deb
intltool-debian_0.35.0+20060710.1_all.deb
lame_3.97-0.0_i386.deb
libbeecrypt6_4.1.2-6build1_i386.deb
libc6_2.7-10ubuntu4_i386.deb
libc6-dev_2.7-10ubuntu4_i386.deb
libc6-i686_2.7-10ubuntu4_i386.deb
libfaad0_2.6.1-2ubuntu0.1_i386.deb
libfreetype6_2.3.5-1ubuntu4.8.04.1_i386.deb
libnautilus-extension1_1%3a2.22.5.1-0ubuntu1_i386.deb
libqt4-core_4.3.4-0ubuntu3_i386.deb
libqt4-gui_4.3.4-0ubuntu3_i386.deb
librpm4.4_4.4.2.1-1ubuntu6_i386.deb
libruby1.8_1.8.6.111-2ubuntu1.2_i386.deb
libsdl-mixer1.2_1.2.8-1ubuntu0.1_i386.deb
libsdl-ttf2.0-0_2.0.9-1_i386.deb
libsmpeg0_0.4.5+cvs20030824-2_i386.deb
libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb
libxml2-utils_2.6.31.dfsg-2ubuntu1.2_i386.deb
lock
lsb_3.2-4ubuntu1_all.deb
lsb-core_3.2-4ubuntu1_i386.deb
lsb-cxx_3.2-4ubuntu1_i386.deb
lsb-desktop_3.2-4ubuntu1_i386.deb
lsb-graphics_3.2-4ubuntu1_i386.deb
lsb-languages_3.2-4ubuntu1_i386.deb
lsb-multimedia_3.2-4ubuntu1_i386.deb
lsb-printing_3.2-4ubuntu1_i386.deb
mailx_1%3a8.1.2-0.20071017cvs-2_i386.deb
nautilus_1%3a2.22.5.1-0ubuntu1_i386.deb
nautilus-data_1%3a2.22.5.1-0ubuntu1_all.deb
ncurses-term_5.6+20071124-1ubuntu2_all.deb
partial
pax_1%3a1.5-16_i386.deb
plib1.8.4c2_1.8.4-8ubuntu1_i386.deb
po-debconf_1.0.10_all.deb
python-gnome2-extras_2.19.1-0ubuntu7.1_i386.deb
python-gtkhtml2_2.19.1-0ubuntu7.1_i386.deb
python-libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb
python-pygame_1.7.1release-4.1ubuntu1_i386.deb
rdesktop_1.5.0-3+cvs20071006ubuntu0.1_i386.deb
rpm_4.4.2.1-1ubuntu6_i386.deb
ruby1.8_1.8.6.111-2ubuntu1.2_i386.deb
simgear0_1.0.0-1_i386.deb
singularity_0.26a+r409-5_all.deb
sudo_1.6.9p10-1ubuntu3.3_i386.deb
tzdata_2008g-0ubuntu0.8.04_all.deb
vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-nox_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-plugin-alsa_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_all.deb
vlc-plugin-arts_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-plugin-esd_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-plugin-ggi_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-plugin-pulse_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-plugin-sdl_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
vlc-plugin-svgalib_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2_i386.deb
xulrunner-1.9_1.9.0.2+build6+nobinonly-0ubuntu0.8.04.1_i386.deb
xulrunner-1.9_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb
xulrunner-1.9-gnome-support_1.9.0.2+build6+nobinonly-0ubuntu0.8.04.1_i386.deb
xulrunner-1.9-gnome-support_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb
primus@Cybertron:/var/cache/apt/archives$[/QUOTE]

Whereas if we look at my installed-packages file (made by running the following command) there should be many more packages cached. Did I do this by running autoclean/remove? The command I ran was:

[QUOTE=]primus@Cybertron:~$ sudo dpkg --get-selections > installed-software[/QUOTE]

and the result was: 

[QUOTE=]
acl						install
acpi						install
acpi-support					install
acpid						install
adduser						install
alacarte					install
all-in-one-sidebar				install
alltray						install
alsa-base					install
alsa-utils					install
amarok						install
amarok-xine					install
anacron						install
apache2-mpm-prefork				install


[B][U]# I cut out a lot of ouput here for the sake of shortening this post up
[/U][/B]


xcursor-themes					install
xdg-user-dirs					install
xdg-user-dirs-gtk				install
xdg-utils					install
xfonts-100dpi					install
xfonts-75dpi					install
xfonts-base					install
xfonts-encodings				install
xfonts-scalable					install
xfonts-utils					install
xinit						install
xkb-data					install
xml-core					install
xorg						install
xorg-driver-fglrx				install
xsane						install
xsane-common					install
xscreensaver-data				install
xscreensaver-gl					install
xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install
xserver-xorg-input-kbd				install
xserver-xorg-input-mouse			install
xserver-xorg-input-synaptics			install
xserver-xorg-input-vmmouse			install
xserver-xorg-input-wacom			install
xserver-xorg-video-all				install
xserver-xorg-video-amd				install
xserver-xorg-video-apm				install
xserver-xorg-video-ark				install
xserver-xorg-video-ati				install
xserver-xorg-video-chips			install
xserver-xorg-video-cirrus			install
xserver-xorg-video-cyrix			install
xserver-xorg-video-dummy			install
xserver-xorg-video-fbdev			install
xserver-xorg-video-geode			install
xserver-xorg-video-glint			install
xserver-xorg-video-i128				install
xserver-xorg-video-i740				install
xserver-xorg-video-i810				install
xserver-xorg-video-imstt			install
xserver-xorg-video-intel			install
xserver-xorg-video-mga				install
xserver-xorg-video-neomagic			install
xserver-xorg-video-newport			install
xserver-xorg-video-nsc				install
xserver-xorg-video-nv				install
xserver-xorg-video-openchrome			install
xserver-xorg-video-psb				install
xserver-xorg-video-rendition			install
xserver-xorg-video-s3				install
xserver-xorg-video-s3virge			install
xserver-xorg-video-savage			install
xserver-xorg-video-siliconmotion		install
xserver-xorg-video-sis				install
xserver-xorg-video-sisusb			install
xserver-xorg-video-tdfx				install
xserver-xorg-video-tga				install
xserver-xorg-video-trident			install
xserver-xorg-video-tseng			install
xserver-xorg-video-v4l				install
xserver-xorg-video-vesa				install
xserver-xorg-video-vga				install
xserver-xorg-video-via				install
xserver-xorg-video-vmware			install
xserver-xorg-video-voodoo			install
xsltproc					install
xterm						install
xulrunner-1.9					install
xulrunner-1.9-gnome-support			install
xutils						install
xutils-dev					install
yelp						install
youtube-dl					install
zenity						install
zip						install
zlib1g						install[/QUOTE]

from the looks of all that I think I should have a lot more cached packages haha. Is there a way I can redownload them or at least the ones I want to add to my Apt-On-CD? I've been working on backing my system up for a couple days now and am trying different methods to see which I prefer...  Thanks a bunch!

---

