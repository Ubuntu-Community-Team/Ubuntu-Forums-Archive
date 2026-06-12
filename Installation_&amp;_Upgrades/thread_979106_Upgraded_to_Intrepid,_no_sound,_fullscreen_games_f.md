---
title: "Upgraded to Intrepid, no sound, fullscreen games freeze computer"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by AmandaKerik on 2008-11-11
I used the proper alternative CD to upgrade my Ubuntu from Hardy to Intrepid and while most things work, I have found that I have
[LIST]
[*]no sound, 
[*]any games that go full screen freeze my computer
[*]Firefox keeps forgetting my profiles
[/LIST]

My main concern is my computer's stability followed by my sound. Games I can do without for a while and I can keep creating Firefox profiles and copying the old folders over them.

Note: these all worked before the upgrade.

I've tried the [fix]("http://ubuntuforums.org/showthread.php?t=205449") that had me un-install my sound related packages and put them back in, which resulted in not only the sound packages being removed but ubuntu-desktop being removed as well.

Then I was suggested (in the terminal) that I remove packages I'm not using anymore, which then resulted in gnome and a whole slew of things being un-installed.

>   bluez-audio check clamav-testfiles foomatic-db-gutenprint g++-4.2
  gnome-backgrounds **gnome-core** gnome-games-extra-data gnome-keyring-manager
  iamerican ibritish ijsgutenprint ispell libalut0 libavutil1d libbind9-30
  libblas3gf libcamel1.2-11 libdbus-qt-1-1c2 libdns35 libflac++6 libgfortran2
  libgtkhtml3.16-cil libisc32 libisc35 libisccc30 libisccfg30 liblapack3gf
  liblwres30 libmtp7 libnetcdf4 libnss3-0d libntfs-3g23 libopenal0a
  libopenexr2ldbl libpoppler-glib2 libpoppler2 libpostproc1d libqt4-core
  libqt4-gui libsdl-pango1 libsmbios1 libstdc++6-4.2-dev libtotem-plparser10
  libvlc0 libx264-57 **linux-restricted-modules-2.6.22-14-386** o3read
  openoffice.org-filter-mobiledev openoffice.org-java-common
  openoffice.org-writer2latex python-foomatic python-ipy vlc-plugin-pulse

I've reinstalled them as best as I can, but I fear any more tinkering will leave my installation more borked than before.

> a@ubuntu:~$ aplay -l
aplay: device_list:215: no soundcards found...

> a@ubuntu:~$ lspci -v
...
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: FIRST INTERNATIONAL Computer Inc Device 9012
	Flags: medium devsel, IRQ 255
	I/O ports at ec00 [size=256]
	Capabilities: <access denied>
...

sudo modprobe snd-[tab] doesn't come up with anything

(side note)reinstalling gdm complains I'm not the owner of the directory.

I'd rather try to fix this than wipe and install again as I'll learn more, but I definitely need help.

---

### Post by blueberries on 2008-11-11
same here, bit different card: *00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)*

i tried to compile the drivers (with the help of the above mentioned guide), but it failed.

:(

---

### Post by kirilly on 2009-01-22
Same, I have no same in most games in Ubuntu.
But after installing "xubuntu-desktop" packges and logging in xfce4 sound works

---

