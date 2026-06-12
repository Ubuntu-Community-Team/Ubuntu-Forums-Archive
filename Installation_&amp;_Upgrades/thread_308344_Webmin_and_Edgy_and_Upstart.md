---
title: "Webmin and Edgy and Upstart"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by sscotti on 2006-11-27
I installed Edgy and have worked through some bugs to get it to where it is working failry well.  However, I then installed WebMin to manage some of my servers and settings.  It was working fine under 6.06, but in 6.10 the bootup and startup items appear disabled and the runlevel is stuck at 0.  I suspect that this is due to upstart being used.  The following is the list of my services, modules, etc. and status.:

 	acpi-support 	No 	INIT script to check whether we're on batteries, and so start with laptop mode etc enabled. BUGS: unless we start *really* late, we have no way of throttling xscreensaver, since it won't be there to command.
	acpid 	No 	Check for daemon presence
	alsa-utils 	No 	This script stores and restores mixer levels on
	anacron 	No 	/etc/init.d/anacron: start anacron
	apmd 	No 	Start or stop the Advanced Power Management daemon.
	apport 	No 	
	atd 	No 	Debian init script for the atd deferred executions
	avahi-daemon 	No 	This file is part of avahi.
	binfmt-support 	No 	Enable support for extra binary formats using the Linux
	bluetooth 	No 	
	bootclean 	No 	
	bootlogd 	No 	Starts or stops the bootlogd log program
	bootmisc.sh 	No 	
	brltty 	No 	
	checkfs.sh 	No 	
	checkroot.sh 	No 	
	console-screen.sh 	No 	
	console-setup 	No 	
	cron 	No 	cron is a standard UNIX program that runs user-specified
	cupsys 	No 	
	dbus 	No 	
	dns-clean 	No 	by John Hasler 1999-2003 Any possessor of a copy of this program may treat it as if it were in the public domain. I waive all rights. This script should be run at bootup to clean up any mess left by 0dns-up. It should be run before ppp is started. It should never be run while ppp is up.
	festival 	No 	/etc/init.d/festival
	gdm 	No 	Originally based on: Version: @(#)skeleton 1.8 03-Mar-1998 [email]miquels@cistron.nl[/email]
	glibc.sh 	No 	
	halt 	No 	
	hdparm 	No 	
	hostname.sh 	No 	
	hotkey-setup 	No 	
	hplip 	No 	initscript for the HP Linux Printing and Imaging System Distributed under the GPLv2 or newer
	hwclock.sh 	No 	Set and adjust the CMOS clock, according to the UTC setting in /etc/default/rcS (see also rcS(5)).
	keriomailserver 	No 	Start the Kerio MailServer
	keyboard-setup 	No 	
	killprocs 	No 	
	klogd 	No 	/etc/init.d/klogd: start the kernel log daemon.
	laptop-mode 	No 	chkconfig: - 20 90 description: Starts and stops "laptop-mode" - tweaks system behavior to extend battery life.
	linux-restricted-modules-common 	No 	
	loopback 	No 	- brings up the loopback (127.0.0.1) network device so that DHCP and other such things will work
	makedev 	No 	
	mgetty-fax 	No 	
	module-init-tools 	No 	Load the modules listed in /etc/modules.
	mountall-bootclean.sh 	No 	Clean temporary filesystems after
	mountall.sh 	No 	
	mountdevsubfs.sh 	No 	Mount the virtual filesystems the kernel provides
	mountkernfs.sh 	No 	Mount initial set of virtual filesystems the kernel
	mountnfs-bootclean.sh 	No 	Clean temporary filesystems after
	mtab.sh 	No 	Update the mount program's mtab file after
	networking 	No 	
	nvidia-kernel 	No 	
	pcmciautils 	No 	This service provides PCMCIA hardware support for
	powernowd 	No 	
	powernowd.early 	No 	Set DO_MODULES to yes which will trigger the module loading part of the powernowd init script instead of the daemon part.
	pppd-dns 	No 	
	procps.sh 	No 	
	rc.local 	No 	
	readahead 	No 	init script for readahead Check the package is still installed
	readahead-desktop 	No 	init script for readahead (second stage) Check the package is still installed
	reboot 	No 	
	rmnologin 	No 	This script removes the /etc/nologin file as the
	rsync 	No 	
	screen 	No 	Script to remove stale screen named pipes on bootup.
	sendsigs 	No 	
	single 	No 	
	stop-bootlogd 	No 	See the bootlogd script
	stop-bootlogd-single 	No 	See the bootlogd script
	stop-readahead 	No 	init script for stopping readahead profiling Check the package is still installed
	sysklogd 	No 	/etc/init.d/sysklogd: start the system log daemon.
	udev 	No 	init script for udev Check the package is still installed
	umountfs 	No 	
	umountnfs.sh 	No 	Also unmounts all virtual filesystems (proc, devfs, devpts,
	umountroot 	No 	
	urandom 	No 	
	usplash 	No 	The usplash script makes sure that usplash exits at the end of the boot sequence and re-run the console-screen.sh script to make sure that the console fonts are actually set
	vbesave 	No 	
	vpnclient_init 	No 	File: vpnclient_init Date: 04/23/2001
	waitnfs.sh 	No 	Network file systems are mounted in the background when
	webmin 	No 	Start/stop Webmin
	wpa-ifupdown 	No 	Run ifdown on interfaces authenticated via
	x11-common 	No 	
vpnclient_init.lock 	No 	
vpnclient_init.lock 	No 	
vpnclient_init.lock 	No 	
vpnclient_init.lock 	No 	
vpnclient_init.lock 	No 	
vpnclient_init.lock 	No 	
vpnclient_init.lock 	No 	


The spacing isn't the best, but you get the drift.  They all say no, and the runlevel at the bottom of the page is 0.

Does this part of webmin work the Edgy.  How else can I manage services and startups in Edgy.

Also, not sure why there are so many vpncient_init.locks.

---

### Post by sscotti on 2006-11-29
FYI anybody,

there is a 1.310 dev version of webmin here:

[http://download.webmin.com/devel/deb/](http://download.webmin.com/devel/deb/)

that should solve a number of issues with Edgy and Webmin.

The official release is suppose to be tomorrow.

---

