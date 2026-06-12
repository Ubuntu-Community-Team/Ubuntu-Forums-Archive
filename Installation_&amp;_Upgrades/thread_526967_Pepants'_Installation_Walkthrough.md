---
title: "Pepants' Installation Walkthrough"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by pepants on 2007-08-16
Hi, I'm new to the forums and wanted to help anyone I could with this little walkthrough. I installed ubuntu today, and made a basic walkthrough for users with nvidia cards (wanting to use TV-OUT in twinview clone mode), wanting to run beryl, virtualbox (for running windows xp within ubuntu), kde (in addition to gnome), ktorrent (better than azureus for downloading), vlc (best media player), proprietary codecs,  ntfs write support and wine.
This also walks you through setting up Ubuntu to boot without a login name/password entry requirement.

Prereq's:
To enter any command into terminal
navigate to
applications->accessories->terminal (hit ENTER after entering command)

1. install ubuntu
remove all data hdd's (except for the one with Ubuntu and (Windows if you are dual booting))
 load Ubuntu cd, make sure your BIOS is set up to boot first from CDROM
start Ubuntu in safe graphics mode.
	double-click install icon
	manual partition
make 2 partitions:
       1. / partition (ext3) (this will be your Ubuntu file system drive)
	2. swap partition: at least size of total installed RAM
	
	install system
	replace data hdd's after first boot (test)
2. update system
	(in terminal) sudo apt-get update
	sudo apt-get dist-upgrade
3. install kde
	sudo apt-get install kde
4. install ktorrent
	sudo apt-get install ktorrent
5. install wine
	sudo apt-get install wine
6. change mozilla homepage to [www.google.com](www.google.com) (or whatever)
7. install virtualbox
	apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential
	sudo apt-get install libxalan110 libxerces27
	sudo gedit /etc/apt/sources.list
	add this line to end of sources.list
	deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free
	sudo apt-get update
	sudo apt-get install virtualbox
	add user name to group of vboxusers
		system->administration->users and groups
8. start restricted nvidia driver
	system->administration->restricted drivers manager
9. restart
10. sudo nvidia-settings
	twinview, clone, apply, save to x configuration file
       sudo nvidia-xconfig --add-argb-glx-visuals
       logout with control+alt+backspace
       log back in
11. install beryl
	sudo apt-get install beryl emerald-themes
	beryl-manager
	system->preferences->sessions->new
	ADD beryl-manager to list
12. remove login requirement at boot
	system->administration->login window->security->enable automatic login
13. add ntfs drives & write support
	sudo apt-get install ntfs-config
	sudo ntfs-config
        check all hdd's
14. install proprietary codecs
	open any mp3, avi, wmv file
        follow instructions
15. install vlc
	sudo apt-get install vlc
16. make vlc default media player
	right click media file->properties->open with
	(program files located in file system/usr/bin)
	
That's it for now. I'm just a nix noob, just learning myself. I'm only posting this 
in case it might help someone with similar needs.

Pepants

---

