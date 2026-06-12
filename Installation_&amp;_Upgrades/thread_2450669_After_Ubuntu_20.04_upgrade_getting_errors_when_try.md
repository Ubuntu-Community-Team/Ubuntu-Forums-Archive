---
title: "After Ubuntu 20.04 upgrade getting errors when trying to connect with Samba"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by DarkStarDeity on 2020-09-18
I've just upgraded one of the boxes in our home network from Ubuntu 18.04 to 20.04, and when we tried to connect to the Samba shares from the other Ubuntu box (still at 18.04), we got the error "Failed to retrieve share list from Server: Invalid argument". We got the same error when trying to connect to the box from itself via Samba. The box appears in Nautilus Other Locations (both directly and via the Windows Network/Workgroup group), but clicking on it produces this error. Trying to connect to the box directly via it's IP address produces the same error. I checked all of the shares on the box in Nautilus and they all appear to be good. The shares are set up to allow anonymous read and write access, because they can only be accessed from within the home network. 

We have been able to connect to the server from our android devices with no problems; ironically it is only the ubuntu-ubuntu connections that are having this issue. 

Looking around for solutions on the web, I saw a suggestion to add the line "client max protocol = NT1" to my smb.conf file for a similar (but not exactly the same) issue, which I tried, but all that did was change the error to "Failed to retrieve share list from Server: Connection timed out", which was returned immediately, when connecting from the other Ubuntu box. 

Can anyone help me out here? As this is the file server for the household, we really need file sharing from this box to be working (and I'm also reluctant to upgrade the other box until I've fixed this, as I also do a lot of file-sharing to and from it as well).

---

### Post by TheFu on 2020-09-18
I probably cannot help with samba stuff, but the first questions will be to
[LIST]
[*]Post the samba config file on the server - get the actual one use by running **testparm**.
[*]Post the mount command used by the clients. That should be in the /etc/fstab for each client machine for each mount.
[/LIST]
I believe in the last 6 months both the Samba team and MSFT changed their default settings in some way. Unfortunately, those changes appear to break access. 

If you are interested in using the native file sharing that all Unix systems support, I can help with NFS. NFS sorta "just works", provided the network is properly being managed. That means having 
[LIST]
[*]static IPs for any servers. This is a best practice.
[*]centrally managed DNS or mDNS lookups. Modifying the /etc/hosts files can work most of the time as well. Using IP addresses for mounts should skip this part.
[*]uid/gid on all Unix systems being either centrally maintained or matched across systems. The 'id' command run on each system for each userid will show the uid/gid.  The first userid uid would be 1000. 2nd uid would be 1001, etc.  There are mapping techniques if they don't match already, but I've never seen those work.
[/LIST]
NFS supports native Unix file permissions.

---

### Post by DarkStarDeity on 2020-09-19
Since I did that post, I noticed that there were samba client updates available for the 18.04 box, and after installing those and restarting that machine, it can now connect to the 20.04 box. I also installed a fresh 20.04 build on an old unused machine and it was able to connect to both the 20.04 box and the 18.04 box with no problems, so I think I will go ahead and upgrade the 20.04 box. Cross your fingers for me. 

The 20.04 box still cannot connect to itself via samba, which, although a weird thing to do, it should be able to. So I've included the information requested just in case there's something else I should modify or update (I removed the "client max protocol = NT1" that I previously added to the smb.conf file as it didn't appear to help at all).

----------------------
Testparm output on 20.04 box:

Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	logging = file
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb


[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---------------------------

/etc/fstab on client machine (currently 18.04):

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=162f72d6-5418-4c66-80f9-3f4eb140c191 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5055cb0a-a510-44ad-8045-1aecff15d2e4 none            swap    sw              0       0
/dev/sdb1                                  /media/data  ext4  defaults             0  0

---

### Post by TheFu on 2020-09-19
Well, I don't see any samba shares configured.  Nothing is shared, when nothing is configured.

And the fstab on that client doesn't show any attempts to mount any samba (or other) shared storage from other systems.

If nothing is configured, my answer is, working as expected.  There is no "magic" here. Configuration is mandatory.

---

### Post by DarkStarDeity on 2020-09-20
I set up the shared folders through nautilus. That is the same both pre- and post- 20.04 upgrade. After another couple of rounds of updates and restarts on that box and updating the remaining 18.04 box to 20.04, everything is now working in both directions and all of my previously-shared folders are available as samba mounts on both the remote client and on the box itself.

---

