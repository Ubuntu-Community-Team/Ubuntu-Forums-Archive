---
title: "Live Cd stops at Enterprise Volume managaer"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by dabster on 2005-11-21
I Tried the Live Cd of Breezy But  Booting Stops at the 
"Starting Enterprise Logical Volume Manager"
After Which the System Halts...

Any Idea That Why It is Happening...
I suppose That Many People are Facing this error....
Any Solutions to it.....

--
dabster

---

### Post by jwmislan on 2006-01-25
There is also another thread on this issue
( [http://ubuntuforums.org/showthread.php?t=83809](http://ubuntuforums.org/showthread.php?t=83809) )
it was no help other than suggesting that you could turn off volumes management, if you are not presently using it .
   update-rc.d -f evms remove

I have this same problem but I don't want to turn off the service because I'm planning to use it in the near future.

Ubuntu users don't want to resort to turning off potentially important services as Volume Management.
This is an important issue in my opinion, and I'm
 a bit disturbed that proper attention to this has not appeared anywhere on the forums, or elsewhere, to address, or resolve Volume Management issues.  
 Guess I'll have to wait and see if an update comes soon that solves the Volume Management boot-time slowdown/lockup issue.

JohnWM

---

### Post by Turin Turambar on 2006-01-28
[QUOTE=jwmislan]There is also another thread on this issue
( [http://ubuntuforums.org/showthread.php?t=83809](http://ubuntuforums.org/showthread.php?t=83809) )
it was no help other than suggesting that you could turn off volumes management, if you are not presently using it .
   update-rc.d -f evms remove

I have this same problem but I don't want to turn off the service because I'm planning to use it in the near future.

Ubuntu users don't want to resort to turning off potentially important services as Volume Management.
This is an important issue in my opinion, and I'm
 a bit disturbed that proper attention to this has not appeared anywhere on the forums, or elsewhere, to address, or resolve Volume Management issues.  
 Guess I'll have to wait and see if an update comes soon that solves the Volume Management boot-time slowdown/lockup issue.

JohnWM[/QUOTE]

I have the same problem as well, though not with the live cd, but when cd/dvd is in the drive. The system then halts at EVMS during boot! After I reset the machine for 2-3 times, the boot goes normally. Strange! I too do not want to disable this service... but it's getting really annoying.

---

### Post by Turin Turambar on 2006-01-28
I think I fixed this problem.
In /etc/evms.conf file I added the cd drives in "exclude" section for sysfs devices.

Here's a part of evms.conf, how it looks now: ```
sysfs_devices {

	# "include" are the block devices found in the [sysfs_mount_dir]/block/
	# directory that you want EVMS to use as disks.
	#
	# Block device names can be specified using "*", "?", and "[...]"
	# notations.

	include = [ * ]

	# "exclude" are the block devices found in the [sysfs_mount_dir]/block/
	# directory that you don't want EVMS to use as disks.  Entries here
	# will override any possible matches from the "include" setting.
	#
	# Block device names can be specified using "*", "?", and "[...]"
	# notations.

	exclude = [ hdc hdd ]

	# "max_open_disks" is the maximum number of disks that EVMS will have
	# open file-descriptors for while the engine is running. The allowable
	# range is 1 to 1024, and the default value is 64.

#	max_open_disks = 64
}
```

So far, it works on my machine... even after several reboots, loading was normal.

---

