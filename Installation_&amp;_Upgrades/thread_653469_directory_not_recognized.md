---
title: "directory not recognized"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Magellan on 2007-12-29
I recently did a clean install of Gutsy on an old P3 I had around and used that for a while until I built a new pc.
 I copied the .mozilla-thunderbird folder from the hard drive from another, now dead, pc into the home directory and had Thunderbird up and running with all my old email and settings intact.

I completed the build of my new pc and did a clean install of Gutsy.

I then took the hard drive from the P3 and installed it into an external enclosure.  I plugged it into the new PCs firewire port and the disk was mounted.

I can see most of the data on the disk, but the .mozill-thunderbird directory (and a few others) are not recognized correctly.  Here's the ls output:

> jklee@family-room-desktop:/media/disk/home/jklee$ ls -la
total 188
drwxr-xr-x 39 jklee jklee  4096 2007-12-23 21:07 .
drwxr-xr-x  3 root  root   4096 2007-12-01 15:25 ..
?---------  ? ?     ?         ?                ? .automatix
-rw-------  1 jklee jklee  1159 2007-12-05 21:17 .bash_history
-rw-r--r--  1 jklee jklee   220 2007-12-01 15:25 .bash_logout
-rw-r--r--  1 jklee jklee  2298 2007-12-01 15:25 .bashrc
drwxr-xr-x  4 jklee jklee  4096 2007-12-19 22:03 .bloboats
drwxr-xr-x  3 jklee jklee  4096 2007-12-01 18:08 .cache
drwxr-xr-x  4 jklee jklee  4096 2007-12-03 21:52 .config
drwx------  2 jklee jklee  4096 2007-12-08 10:59 .dbus-keyrings
drwxr-xr-x  2 jklee jklee  4096 2007-12-21 12:52 Desktop
-rw-------  1 jklee jklee    28 2007-12-23 21:03 .dmrc
drwxr-xr-x  2 jklee jklee  4096 2007-12-01 18:07 Documents
-rw-------  1 jklee jklee    16 2007-12-01 18:08 .esd_auth
drwxr-xr-x  9 jklee jklee  4096 2007-12-23 21:07 .evolution
lrwxrwxrwx  1 jklee jklee    26 2007-12-01 15:25 Examples -> /usr/share/example-content
drwxr-xr-x  2 jklee jklee  4096 2007-12-05 22:07 .fontconfig
drwx------  5 jklee jklee  4096 2007-12-23 21:03 .gconf
drwx------  2 jklee jklee  4096 2007-12-23 21:07 .gconfd
?---------  ? ?     ?         ?                ? .ggz
-rw-r-----  1 jklee jklee     0 2007-12-19 21:39 .gksu.lock
drwxr-xr-x  3 jklee jklee  4096 2007-12-01 18:07 .gnome
drwx------ 15 jklee jklee  4096 2007-12-23 21:07 .gnome2
drwx------  2 jklee jklee  4096 2007-12-05 22:08 .gnome2_private
?---------  ? ?     ?         ?                ? .gstreamer-0.10
-rw-r--r--  1 jklee jklee   108 2007-12-23 21:04 .gtk-bookmarks
-rw-r--r--  1 jklee jklee    87 2007-12-01 18:07 .gtkrc-1.2-gnome2
-rw-------  1 jklee jklee   700 2007-12-23 21:07 .ICEauthority
?---------  ? ?     ?         ?                ? .icons
drwxr-xr-x  3 jklee jklee  4096 2007-12-01 18:08 .local
drwx------  3 jklee jklee  4096 2007-12-01 18:08 .metacity
drwx------  3 jklee jklee  4096 2007-12-04 22:11 .mozilla
?---------  ? ?     ?         ?                ? .mozilla-thunderbird
?---------  ? ?     ?         ?                ? .mplayer
drwxr-xr-x  2 jklee jklee  4096 2007-12-01 18:07 Music
drwxr-xr-x  3 jklee jklee  4096 2007-12-23 21:07 .nautilus
drwxr-xr-x  3 jklee jklee  4096 2007-12-02 19:40 old_backup_disk
drwxr-xr-x  5 jklee jklee  4096 2007-12-02 22:22 old_ubuntu_system
?---------  ? ?     ?         ?                ? old_windows_system
drwxr-xr-x  3 jklee jklee  4096 2007-12-23 20:24 Pictures
-rw-r--r--  1 jklee jklee   566 2007-12-01 15:25 .profile
drwxr-xr-x  2 jklee jklee  4096 2007-12-01 18:07 Public
-rw-r--r--  1 jklee jklee 21192 2007-12-23 21:07 .recently-used.xbel
-rw-r--r--  1 jklee jklee     0 2007-12-01 18:11 .sudo_as_admin_successful
drwxr-xr-x  2 jklee jklee  4096 2007-12-01 18:07 Templates
?---------  ? ?     ?         ?                ? .themes
drwx------  4 jklee jklee  4096 2007-12-02 19:32 .thumbnails
drwx------ 10 jklee jklee  4096 2007-12-03 22:05 .Trash
?---------  ? ?     ?         ?                ? .update-manager-core
drwx------  2 jklee jklee  4096 2007-12-01 18:08 .update-notifier
drwxr-xr-x  2 jklee jklee  4096 2007-12-01 18:07 Videos
drwx------  2 jklee jklee  4096 2007-12-02 19:58 .w3m
-rw-r--r--  1 jklee jklee  7397 2007-12-23 21:07 .xsession-errors


I also tried a chmod on it to see if I could copy it.  I got the following error:
> jklee@family-room-desktop:/media/disk/home/jklee$ sudo chmod 777 .mozilla-thunderbird 
[sudo] password for jklee:
chmod: cannot access `.mozilla-thunderbird': Input/output error
jklee@family-room-desktop:/media/disk/home/jklee$ 


At this point, I'm not sure what to check.  Thunderbird was working fine on the P3 until the day I decommissioned it (it has a future as a NAS server).

TIA

James

---

### Post by Magellan on 2007-12-30
one more thing.  The p3 install was with the x86 version.  The new install is the 64 bt version.

---

