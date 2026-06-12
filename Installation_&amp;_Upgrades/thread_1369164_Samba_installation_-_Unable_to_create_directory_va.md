---
title: "Samba installation - Unable to create directory /var/run/samba for file mutex.tdb"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by Silvestro Fantacci on 2009-12-31
I am trying to get Samba to work on Ubuntu 9.10 (Karmic Koala) with little success.

On installing the samba package via the Synaptic Package Manager I get the following details:

-------------------------------
[COLOR="Blue"]Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 138124 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.4.0-3ubuntu5.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up samba (2:3.4.0-3ubuntu5.1) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
Generating /etc/default/samba...
[COLOR="Red"]Unable to create directory /var/run/samba for file mutex.tdb. Error was No such file or directory[/COLOR]
tdbsam_open: Converting version 0.0 database to version 4.0.
tdbsam_convert_backup: updated /var/lib/samba/passdb.tdb file.
[COLOR="Red"]account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0[/COLOR]
Importing account for nobody...ok
Importing account for silvestro...ok
 * Starting Samba daemons
   ...done.[/COLOR]
-------------------------------

Following that, rebooting, making a folder shareable, etc. I go to Places --> Network and:

(1) I can only see the "Windows Network" icon, but not the icon for this PC (I would expect the PC to be able to see its own shared folders?)

(2) On clicking Windows Network I get the message "Unable to mount location" - "Failed to retrieve share list from server".

I also had a first go at the fixes described in "Howto: Fix Windows share browsing issues" ([http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)) but no luck so far, so I wonder whether it's the installation errors above that cause the problem in the first place and if so, how can I avoid them?

---

