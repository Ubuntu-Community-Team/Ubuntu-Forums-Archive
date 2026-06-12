---
title: "Sound and wireless card not working after update"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Sorandal on 2008-08-23
After downloading quite a few routine updates I rebooted and the sound and wireless card were no longer working.  I'm running 8.04.  I don't know how to undo the updates, but I have a list of them from the history section in the package manager, it's kind of long but here it is:

Commit Log for Fri Aug 22 19:25:57 2008


Upgraded the following packages:
anacron (2.3-13ubuntu2) to 2.3-13ubuntu2.1
app-install-data-commercial (9) to 9.2
base-files (4.0.1ubuntu5) to 4.0.1ubuntu5.8.04.2
bind9-host (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
compiz (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
compiz-core (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
compiz-gnome (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
compiz-plugins (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
cpp (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
deskbar-applet (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1
dnsutils (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
file (4.21-3) to 4.21-3ubuntu1
firefox (3.0~b5+nobinonly-0ubuntu3) to 3.0.1+build1+nobinonly-0ubuntu0.8.04.3
firefox-gnome-support (3.0~b5+nobinonly-0ubuntu3) to 3.0.1+build1+nobinonly-0ubuntu0.8.04.3
flashplugin-nonfree (9.0.124.0ubuntu2) to 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2
g++ (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
gcalctool (5.22.2-0ubuntu1) to 5.22.3-0ubuntu0.1
gcc (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
gnome-about (1:2.22.2-0ubuntu2) to 1:2.22.3-0ubuntu1
gnome-app-install (0.5.2.7-0ubuntu1) to 0.5.2.8-0ubuntu1
gnome-applets (2.22.2-0ubuntu1) to 2.22.2-0ubuntu2
gnome-cards-data (1:2.22.1.1-0ubuntu3) to 1:2.22.3-0ubuntu2
gnome-desktop-data (1:2.22.2-0ubuntu2) to 1:2.22.3-0ubuntu1
gnome-panel (1:2.22.2-0ubuntu1) to 1:2.22.2-0ubuntu1.1
gstreamer0.10-plugins-ugly (0.10.7-3) to 0.10.7-3ubuntu1
gtk2-engines (1:2.14.1-0ubuntu1) to 1:2.14.3-0ubuntu2
gtk2-engines-murrine (0.53.1-1ubuntu1) to 0.53.1-1ubuntu2
gtk2-engines-ubuntulooks (0.9.12-11) to 0.9.12-12
gtkhtml3.14 (3.18.2-0ubuntu1) to 3.18.3-0ubuntu2
guidance-backends (0.8.0svn20080103-0ubuntu16) to 0.8.0svn20080103-0ubuntu16.1
gvfs (0.2.4-0ubuntu1) to 0.2.5-0ubuntu2
gvfs-backends (0.2.4-0ubuntu1) to 0.2.5-0ubuntu2
gvfs-fuse (0.2.4-0ubuntu1) to 0.2.5-0ubuntu2
hal (0.5.11~rc2-1ubuntu8.1) to 0.5.11~rc2-1ubuntu8.2
hal-info (20080317+git20080318-1ubuntu4) to 20080508+git20080601-0ubuntu0.8.04
initramfs-tools (0.85eubuntu36) to 0.85eubuntu39.2
iproute (20071016-2ubuntu1) to 20071016-2ubuntu2
klibc-utils (1.5.7-4ubuntu3) to 1.5.7-4ubuntu4
language-pack-en (1:8.04+20080415) to 1:8.04+20080708
language-pack-en-base (1:8.04+20080415) to 1:8.04+20080527
language-pack-gnome-en (1:8.04+20080415) to 1:8.04+20080708
language-pack-gnome-en-base (1:8.04+20080415) to 1:8.04+20080527
language-support-writing-en (1:8.04+20080410) to 1:8.04+20080630
libavcodec1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7.1+medibuntu1
libavformat1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7.1+medibuntu1
libavutil1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7.1+medibuntu1
libbind9-30 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
libcairo2 (1.6.0-0ubuntu1) to 1.6.0-0ubuntu2
libcamel1.2-11 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libdecoration0 (1:0.7.4-0ubuntu6) to 1:0.7.4-0ubuntu7
libdeskbar-tracker (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
libebook1.2-9 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libecal1.2-7 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libedata-book1.2-2 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libedata-cal1.2-6 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libedataserver1.2-9 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libedataserverui1.2-8 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libegroupwise1.2-13 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libexchange-storage1.2-3 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libgdata-google1.2-1 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libgdata1.2-1 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2
libgksu2-0 (2.0.5-1ubuntu5) to 2.0.5-1ubuntu5.1
libglib2.0-0 (2.16.3-1ubuntu2) to 2.16.4-0ubuntu2
libglibmm-2.4-1c2a (2.16.0-1) to 2.16.4-0ubuntu1
libgnome-desktop-2 (1:2.22.2-0ubuntu2) to 1:2.22.3-0ubuntu1
libgtkhtml3.14-19 (3.18.2-0ubuntu1) to 3.18.3-0ubuntu2
libgtksourceview2.0-0 (2.2.1-1) to 2.2.2-0ubuntu1
libgtksourceview2.0-common (2.2.1-1) to 2.2.2-0ubuntu1
libgvfscommon0 (0.2.4-0ubuntu1) to 0.2.5-0ubuntu2
libgweather1 (2.22.1.1-0ubuntu2) to 2.22.3-0ubuntu2
libhal-storage1 (0.5.11~rc2-1ubuntu8.1) to 0.5.11~rc2-1ubuntu8.2
libhal1 (0.5.11~rc2-1ubuntu8.1) to 0.5.11~rc2-1ubuntu8.2
libisc32 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
libisccc30 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
libisccfg30 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
libklibc (1.5.7-4ubuntu3) to 1.5.7-4ubuntu4
libldap-2.4-2 (2.4.7-6ubuntu4.1) to 2.4.9-0ubuntu0.8.04.1
liblircclient0 (0.8.3~pre1-0ubuntu7) to 0.8.3~pre1-0ubuntu7.1
liblwres30 (1:9.4.2-10) to 1:9.4.2-10ubuntu0.1
libmagic1 (4.21-3) to 4.21-3ubuntu1
libnspr4-0d (4.7.1~beta2-0ubuntu1) to 4.7.1+1.9-0ubuntu0.8.04.5
libnss3-1d (3.12.0~beta3-0ubuntu1) to 3.12.0.3-0ubuntu0.8.04.4
libntfs-3g23 (1:1.2216-1ubuntu1) to 1:1.2216-1ubuntu2
libpanel-applet2-0 (1:2.22.2-0ubuntu1) to 1:2.22.2-0ubuntu1.1
libpango1.0-0 (1.20.1-1) to 1.20.5-0ubuntu1
libpango1.0-common (1.20.1-1) to 1.20.5-0ubuntu1
libparted1.7-1 (1.7.1-5.1ubuntu9) to 1.7.1-5.1ubuntu9.1
libpcre3 (7.4-1ubuntu2) to 7.4-1ubuntu2.1
libpolkit-gnome0 (0.7-2ubuntu1) to 0.7-2ubuntu1.1
libpoppler-glib2 (0.6.4-1ubuntu1) to 0.6.4-1ubuntu3.1
libpoppler2 (0.6.4-1ubuntu1) to 0.6.4-1ubuntu3.1
libpostproc1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7.1+medibuntu1
libsmbclient (3.0.28a-1ubuntu4) to 3.0.28a-1ubuntu4.4
libsmbios1 (0.13.10-1ubuntu1) to 0.13.10-1ubuntu1.1
libsoundtouch1c2 (1.3.0-2.2) to 1.3.0-2.2ubuntu0.1
libtracker-gtk0 (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
libtrackerclient0 (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
libvlc0 (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
libwnck-common (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1
libwnck22 (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1
libxine1 (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-bin (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-console (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-ffmpeg (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-misc-plugins (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-plugins (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxine1-x (1.1.11.1-1ubuntu3) to 1.1.11.1-1ubuntu3.1
libxslt1.1 (1.1.22-1ubuntu1) to 1.1.22-1ubuntu1.2
linux-headers-generic (2.6.24.18.20) to 2.6.24.19.21
linux-libc-dev (2.6.24-18.32) to 2.6.24-19.36
linux-restricted-modules-common (2.6.24.13-18.41) to 2.6.24.13-19.45
nautilus-sendto (0.13.2-0ubuntu1) to 0.13.2-0ubuntu2
notification-daemon (0.3.7-1ubuntu11) to 0.3.7-1ubuntu11.2
ntfs-3g (1:1.2216-1ubuntu1) to 1:1.2216-1ubuntu2
openoffice.org-l10n-common (1:2.4.0-3ubuntu1) to 1:2.4.1-1ubuntu2
openssl (0.9.8g-4ubuntu3.1) to 0.9.8g-4ubuntu3.3
parted (1.7.1-5.1ubuntu9) to 1.7.1-5.1ubuntu9.1
pciutils (1:2.2.4-1.1ubuntu3) to 1:2.2.4-1.1ubuntu5
pm-utils (0.99.2-3ubuntu9) to 0.99.2-3ubuntu10
policykit-gnome (0.7-2ubuntu1) to 0.7-2ubuntu1.1
poppler-utils (0.6.4-1ubuntu1) to 0.6.4-1ubuntu3.1
procps (1:3.2.7-5ubuntu2) to 1:3.2.7-5ubuntu3
python-central (0.6.5ubuntu1) to 0.6.7ubuntu0.1
python-gobject (2.14.1-2ubuntu2) to 2.14.2-0ubuntu1
python-launchpad-bugs (0.2.30) to 0.2.30.1
samba-common (3.0.28a-1ubuntu4) to 3.0.28a-1ubuntu4.4
smbclient (3.0.28a-1ubuntu4) to 3.0.28a-1ubuntu4.4
tracker (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
tracker-search-tool (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
transmission-common (1.06-0ubuntu5) to 1.22-1ubuntu1~hardy1
transmission-gtk (1.06-0ubuntu5) to 1.22-1ubuntu1~hardy1
ttf-opensymbol (1:2.4.0-3ubuntu6) to 1:2.4.1-1ubuntu2
tzdata (2008b-1ubuntu1) to 2008e-1ubuntu0.8.04
ufw (0.16.2) to 0.16.2.3
update-manager (1:0.87.27) to 1:0.87.30
update-manager-core (1:0.87.27) to 1:0.87.30
update-notifier (0.70.7) to 0.70.9
update-notifier-common (0.70.7) to 0.70.9
vino (2.22.1-1) to 2.22.2-0ubuntu1
vlc-plugin-pulse (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
x11-common (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xbase-clients (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xfce4-appfinder (4.4.2-1ubuntu1) to 4.4.2-1ubuntu1.1
xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-input-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-amd (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-cirrus (1:1.1.0-8) to 1:1.1.0-8ubuntu1
xserver-xorg-video-geode (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-intel (2:2.2.1-1ubuntu13) to 2:2.2.1-1ubuntu13.6
xserver-xorg-video-nsc (1:2.8.3-2) to 1:2.8.3-2ubuntu0.1
xsltproc (1.1.22-1ubuntu1) to 1.1.22-1ubuntu1.2
xutils (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2

Installed the following packages:
libdns35 (1:9.4.2-10ubuntu0.1)
libsilc-1.1-2 (1.1.5-1ubuntu1)
linux-headers-2.6.24-19 (2.6.24-19.36)
linux-headers-2.6.24-19-generic (2.6.24-19.36)
linux-image-2.6.24-19-generic (2.6.24-19.36)
openoffice.org-hyphenation-en-us (2.3.1-2ubuntu1)
winbind (3.0.28a-1ubuntu4.4)

Thanks

---

### Post by Pumalite on 2008-08-23
Post:
lshw -C sound
lshw -C network

---

### Post by Sorandal on 2008-08-23
paul@paul-laptop:~$ sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: ES1983S Maestro-3i PCI Audio Accelerator
       vendor: ESS Technology
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=2

paul@paul-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:07:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list

---

