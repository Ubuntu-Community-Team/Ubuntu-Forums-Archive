---
title: "Restore priviliges on home directories?"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Garyu on 2006-07-25
Hey, I just upgraded from Breezy to Dapper on my parents computer and ran into some problems. First of all, here is what I did.

1) GParted from LiveCD to change 75gig ext3 breezy partition to 25gig breezy and a new ext3 of 50gig intended to be used for home dirs.
2) First "sudo su" and then "cp /home /media/hd2" to copy all user accounts (there are four of them) to my new partition. I did not know then about the "cp -a" switch to preserve ownership and such.
3) Started Breezy, changed /etc/apt/sources.list and removed breezy entries and added my Dapper DVD as source with apt-cdrom command. Then I did a apt-get update and apt-get dist-upgrade.
4) After completion I rebooted. On startup got error message that X-server could not start. Bummer. I don't know anything about such things, but I figured hey, I got home on a different partition, I'll just reinstall everything and mount home-dirs from new installation. 
5) Re-installed Dapper from scratch with the DVD. Although my brother "helped" me so the installation ended up on the 50gig partition intended for home but without it being formatted. 
6) After installation I created new users with the same names as the old ones and tried to move my old home dirs into /home, but then applications won't start. I think it is an ownership problem.
7) Tried to run "chown -R ingrid /home/ingrid" and "chgrp -R ingrid /home/ingrid" on my mom's account, but it still doesn't work. (before it had my username and group on it)

So my current situation is:
/dev/hda1 - Dapper with broken X-server
/dev/hda3 - Dapper with wrong permissions/ownership on homes

How do I change ownership on all files and dirs in /home so that everything will work?

---

### Post by sgbeamer on 2006-07-25
You can fix the X server well enough to get by until you figure it out by editing /etc/X11/xorg.conf and changing your video driver to "vesa" (mine says "i810" below

Section "Device"
	Identifier	"Video"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

The chown & chgrp commands should work but you need to do it as root.  Try running 

sudo chown -R ingrid /home/ingrid

---

### Post by Garyu on 2006-07-25
I did "sudo su" before running chown and chgrp... It still does not work... And since I moved my home dirs, this is what I have to do now. Fixing the x-server is a bit late... ](*,)

oh, and the user and group ARE changed on the appropriate home dir. "ls -l" says something like "...ingrid ingrid..." on the ingrid home dir. But I still get a "X :0:0"-something error code when I try to launch say gedit. (not at that computer now, so I can't give the exact error)

tx for the reply though. :)

---

