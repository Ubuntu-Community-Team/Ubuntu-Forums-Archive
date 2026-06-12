---
title: "Webmin with Upstart in Edgy - moved to here"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by quackking on 2006-10-28
Hi. The old thread is closed (was here: [http://ubuntuforums.org/showthread.php?t=278594](http://ubuntuforums.org/showthread.php?t=278594) )

But. Dear keybuk, I understand your comment. I installed Webmin from the download at webmin.com. Whatever they did, I did, including where the program was installed. The main issue I have now is that the boot/startup manager cannot find any of the upstarted services, so it is useless. This is a different issue than starting Webmin itself - if I manually start Webmin, I still cannot configure the services that start at boot time. 

In fact, I can't really see any Edgy utility that easily lets me configure this either. Does such a thing exist?

Thanks for all of this support, btw.

/Quackking

---

### Post by keybuk on 2006-10-30
> **quackking said:**
> But. Dear keybuk, I understand your comment. I installed Webmin from the download at webmin.com. Whatever they did, I did, including where the program was installed. The main issue I have now is that the boot/startup manager cannot find any of the upstarted services, so it is useless. This is a different issue than starting Webmin itself - if I manually start Webmin, I still cannot configure the services that start at boot time.

Does it work ok in dapper installed that way?  Services aren't "upstarted" at the moment, we're still using sysv-rc in edgy (and running that with upstart, instead of sysvinit) -- so there's no reason webmin won't find them unless it's not been installed correctly.

[QUOTE]In fact, I can't really see any Edgy utility that easily lets me configure this either. Does such a thing exist?

bum is popular, I believe

---

### Post by quackking on 2006-10-30
Thanks, I will try 'bum'. As far as Dapper/Webmin is concerned, the Bootup and Shutdown webmin applet (or whatever it should be called) behaves totally differently. 

Here's a cut and paste of part of that screen from one omy my Dapper-based servers. The equivalent for the Edgy-based server is completely blank. Both systems were bone-stock installs of Ubuntu, and downloaded-the-.gz-from-Webmin.com  installs of Webmin.: (sorry, the columnization does not appear correctly below, but you get the idea.)

	Action 	Start at boot? 	Description
	acpi-support 	Yes 	INIT script to check whether we're on batteries, and so start with laptop mode etc enabled. BUGS: unless we start *really* late, we have no way of throttling xscreensaver, since it won't be there to command.
	acpid 	Yes 	Check for daemon presence
	alsa-utils 	No 	
	anacron 	Yes 	/etc/init.d/anacron: start anacron
	apache2 	Yes 	This init.d script is used to start apache2. It basically just calls apache2ctl.
	apmd 	Yes 	Start or stop the Advanced Power Management daemon.
	atd 	Yes 	This file was automatically customized by debmake on Thu, 20 Feb 1997 17:33:12 +0100
	bind9 	Yes 	
	bittorrent 	No 	
	bluez-utils 	Yes 	Bluetooth subsystem starting and stopping
	bootclean.sh 	No 	Functions to clean /tmp
	bootlogd 	No 	One of the first scripts to be executed. Starts or stops
	bootmisc.sh 	No 	
	brltty 	No 	
	checkfs.sh 	No 	
	checkroot.sh 	No 	
	console-screen.sh 	No 	
	cron 	Yes 	cron is a standard UNIX program that runs user-specified
	cupsys 	Yes.......
......

---

