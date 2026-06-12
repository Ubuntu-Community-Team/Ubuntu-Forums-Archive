---
title: "Install without formating the root partition"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by v3rtigo on 2007-08-11
Is there an easy way to install ubuntu on partition without formating it?

---

### Post by Pumalite on 2007-08-11
The installer can do the formatting for you if you have the partition ready.

---

### Post by louieb on 2007-08-11
Maybe. Whats the current file system of the partition? Are you trying to do a reinstall?

---

### Post by v3rtigo on 2007-08-11
I know it can format...

I don't want to format, i allready have it as ext3 partition, and have some files that i don't want to remove :\

Can't move them to other partition either because there is no space...

The installer wont go without formating the partition i want to use as root...

maybe there is other way?

---

### Post by merlinus on 2007-08-11
Backup your data.

-merlin

---

### Post by CharlieSummers on 2007-09-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/72897](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/72897) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **merlinus said:**
> Backup your data.

He mentioned he had no space for a backup. This is unfortunately way too common nowadays.

I have a somewhat different problem; I wanted to install Ubunto to existing ext2 partitions (yeah, I know, no journaling, but I can undelete files when I screw up) without removing gigs worth of unsorted data, so I created an /oldsys directory on the original system's drive, then moved everything to it using a root terminal (ok, ok, lost+found I left alone), also archiving and wiping the /boot partition. The Ubunto installer, of course, didn't like that one tiny little bit. Fortunately, restoring the original system was as simple as re-copying to / and recreating the /boot partition. Still, a long way to go to get nowhere...

According to a response to [Bug 72897](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/72897) (check some of the replies there, as they explain valid reasons for install-without-partition (EDIT: make that format) much better than I can), there *is* a way around this, although I'm not yet comfortable enough with Ubunto to depend on it:

> The way I got around the annoying message box and
didn't have to format my system was by deleting one file.  If you delete
or move this file, the formatting of partitions is not checked:

/lib/partman/check.d/12system_partitions_formatted

I'd be very interested to know if anyone had the courage to do this and install without a format, and whether there was success or failure. There doesn't seem to be any reason the lack of format *wouldn't* work, at least with everything moved out-of-the-way as detailed, but mucking around with core installer files on a distro I don't know yet seemed a little foolhardy without asking...

---

### Post by Pumalite on 2007-09-11
[http://ubuntuforums.org/showthread.php?t=413637](http://ubuntuforums.org/showthread.php?t=413637)

[http://ubuntuforums.org/showthread.php?t=523243](http://ubuntuforums.org/showthread.php?t=523243)

---

### Post by CharlieSummers on 2007-09-11
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=413637](http://ubuntuforums.org/showthread.php?t=413637)

Not directly on-point; the thread you reference discusses dual-boot, grabbing space from a Windoze partition to create a new linux partition. What we're talking about here is installing Ubuntu to an existing linux partition without formatting, partitioning, or otherwise mucking with it.

> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=523243](http://ubuntuforums.org/showthread.php?t=523243)

Er...that's *this* thread...

---

### Post by CharlieSummers on 2007-09-12
For whatever it's worth, this method appears to work. After booting from the desktop installer disc, I mounted the existing partitions and moved the active system into /oldsys, and backing-up and removing the data in the boot partition. I then moved the /lib/partman/check.d/12system_partitions_formatted file (to /lib/partman, since I didn't want to delete it in case it blew up), then ran the installer. When reaching the partitioning screen, I selected "Custom" and changed the mount points of the partitions (right-click and "Edit") to / and /boot, it found the existing swap partition, and proceeded to the next screen, telling me it planned on formatting the swap partition (which isn't a problem).

After the installer was finished with the user-input portion of our entertainment, I monitored the activity through a root terminal; it mounted the partitions to /target/ and /target/boot/ and began to copy the files, leaving the /target/oldsys/ directory blissfully alone.

While I wouldn't suggest this method to those new to linux (I can't imagine the disaster if someone left, say, an old Fedora install alone and installed Ubuntu directly overtop of it), this seems a perfectly reasonable method for a semi-experienced operator to "clean-install" Ubuntu, hanging on to config files, etc., without causing undue support issues.

---

### Post by Pumalite on 2007-09-12
Thank you. I will bookmark it.

---

