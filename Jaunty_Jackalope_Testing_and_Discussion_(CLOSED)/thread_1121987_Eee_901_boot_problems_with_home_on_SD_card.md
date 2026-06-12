---
title: "Eee 901 boot problems with /home on SD card"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by redhorse on 2009-04-10
I'm having a problem that looks like one that many others have experienced, but none of the suggested solutions I've found on any forum work for me.

The problem has manifested itself in two ways.  On my Eee 901, I installed Jaunty Beta where / is on the 4GB internal SSD, /usr is on the 16GB SSD, and /home is on the 32GB removable SD card.

1. Booting with AC power:
The boot process begins, but when fsck is run I get the message "fsck died with exit status 8" and "fsck.ext4: Unable to resolve 'UUID=###'" where ### is the UUID of my SD card.  I am given the option to hit Control-D, and when I do, the boot process continues normally and everything works fine.

2. Booting with battery power:
The boot process begins, but before presented with the desktop I get a dialog stating "/home/user does not appear to exist" where "user" is my username.  I am given the option to login as root, but that never ends well.  The boot always fails under battery power.

I was able to partially solve #2 by modifying line 40 of /etc/init.d/checkfs.sh to read as:
if [ ! -f /fastboot ] && [ &#8220;$FSCKTYPES&#8221; != &#8220;none&#8221; ]
which will force fsck to run even when I am on battery power (I removed the check of $BAT).  Now, it goes through the same process as #1 above, and I am able to boot successfully after hitting Control-D.

The question is now, how can I get around the fsck failure?  Many ideas about the problem revolve around unclean mount/unmount of the SD card.  Several suggestions have been made on the Eee user forums about how to modify /etc/init.d/umountfs to fix this, but none of them have worked for me.

Part of this might be because I have both "umountfs" and "umountfs.sh" in /etc/init.d and they only differ slightly.  I'm not sure which one gets used and I haven't yet dug into what the differences mean, so if anyone has any hints that might speed me along, I would appreciate it.

---

