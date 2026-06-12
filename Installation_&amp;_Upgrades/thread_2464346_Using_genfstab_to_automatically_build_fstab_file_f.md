---
title: "Using genfstab to automatically build fstab file for 21.04"
date: 2021-06-29
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2021-06-29
I installed sysvinit-utils using Synaptic.  I ran the command genfstab -U / in a terminal.  The listing below is what I got.  Does it make sense?  Is it safe to use?

Thank you,

John

```
john@john-Vostro-3500:~$ genfstab -U /
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /dev/sda9
UUID=83254358-81f6-43d6-896d-018dc78b840b	/         	ext4      	rw,relatime,errors=remount-ro	0 1
# tracefs
tracefs             	/sys/kernel/tracing	tracefs   	rw,nosuid,nodev,noexec	0 0
# /run/snapd/ns/snap-store.mntmnt:[4026532573]
/run/snapd/ns/snap-store.mntmnt:[4026532573]	/run/snapd/ns/snap-store.mnt	none      	rw,bind   	0 0
# gvfsd-fuse
gvfsd-fuse          	/run/user/1000/gvfs	fuse.gvfsd-fuse	rw,nosuid,nodev,user_id=1000,group_id=1000	0 0
# portal
portal              	/run/user/1000/doc	fuse.portal	rw,nosuid,nodev,user_id=1000,group_id=1000	0 0
# /dev/loop3
/dev/loop3          	/snap/gtk-common-themes/1514	squashfs  	ro,nodev,relatime	0 0
# /dev/loop4
/dev/loop4          	/snap/gnome-3-34-1804/72	squashfs  	ro,nodev,relatime	0 0
# /dev/loop2
/dev/loop2          	/snap/core18/2066	squashfs  	ro,nodev,relatime	0 0
# /dev/loop0
/dev/loop0          	/snap/gnome-3-34-1804/66	squashfs  	ro,nodev,relatime	0 0
# /dev/loop5
/dev/loop5          	/snap/gtk-common-themes/1515	squashfs  	ro,nodev,relatime	0 0
# /dev/loop1
/dev/loop1          	/snap/core18/2074	squashfs  	ro,nodev,relatime	0 0
# /dev/loop6
/dev/loop6          	/snap/snap-store/518	squashfs  	ro,nodev,relatime	0 0
# /dev/loop7
/dev/loop7          	/snap/snap-store/547	squashfs  	ro,nodev,relatime	0 0
# /dev/loop9
/dev/loop9          	/snap/snapd/12398	squashfs  	ro,nodev,relatime	0 0
# /dev/loop8
/dev/loop8          	/snap/snapd/12159	squashfs  	ro,nodev,relatime	0 0
# /dev/loop10
/dev/loop10         	/snap/vlc/2344	squashfs  	ro,nodev,relatime	0 0
# /dev/loop11
/dev/loop11         	/snap/vlc/2288	squashfs  	ro,nodev,relatime	0 0
/swapfile           	none      	swap      	defa
```

Gparted screenshot that was taken just after fstab listing was generated

---

### Post by MAFoElffen on 2021-06-29
First note... If you post any type of commands or "coe" please post that within { c o d e ] [ / c o d e } tags with the spaces between the I added for that that display... The Moderators here will porbaly ask you to go back and edit that, that way.

Second note: "Symantec/Peter Norton Computing" is not the originator of the Linux utility genfstab. It originally came from Arch Linux, the Arch Linux arch-install-scripts, which is  over 6 years old.

Third Reference this for using it with Ubuntu: [Ubuntu "genfstab" Man Page]("http://manpages.ubuntu.com/manpages/cosmic/man1/genfstab.1.html")

Next: this is what I see... I would doubt the loop devices that are there... Was this run from a LiveCD image? where this was a temporary mount?

Next, the entry for TraceFs... tracefs is a thin stackable file system for capturing file system traces in a portable manner. It's not something that you run full-time, because those kinds of traces usually take up a lot of space quickly.. It's usually something temporary.  Do you have a need to run it full-time on a test/lab machine? 

Next, the entry for gvsd-fuse... gvsds is also a temporary filesystem, which uses gvsd-fuse to kept track of the mount point. Which by the invocation of, it identified it as being in /run/ which is in a temporary space. Usually applications using this, use a call to the Linux utility "gvsd-fuse, to get the mount point and use the filesystem. Is there an supplication that you use that needs it mounted all the time "formally"?

Okay. You have my curiosity now. What is this machine's job?

---

### Post by TheFu on 2021-06-29
I see 2 lines that make sense.  Don't know enough about the install to know if that is sufficient to boot or not. All the others should not be in there for a typical Ubuntu server/desktop installation.

---

### Post by MAFoElffen on 2021-06-29
@TheFu I just saw he added a thumbnail... Do you see what I see? In his fstab. Between post #1 and #2, there is only one mount point. Usually, if you are mounting something on boot, you are mounting it then, becuase you want access to it...

There are 17 things being mounted in the fstab, with 16 of them in memory, with no mount points to access them.

So to answer your question, no. that is a non-working, non-safe fstab.

EDIT: My recommends would be to use
```

sudo fdisk -l

```
To list out your partitions and get the UUID's to reference them, then... Well, I see you just used partitions, instead using of file folders/directories inside your home directory, which is a technique... but to get them organized in a logical manner, you might want to make directories your your Home directory to mount them into as mount points. That way, you have less navigation to access them. That is if you are the only user... If not, then mount them in the Public/Shared home.

Or... combine the partitions into one space/partiton, move the Home to that partition, and mount it as Home... using directories in your Home to organized that data.

---

### Post by TheFu on 2021-06-30
Eeeew. With that number of partitions, I'd have used LVM and some LVs instead.  Getting the sizes correct at the partition level would be nearly impossible. That's were LVM and other advanced volume managers like ZFS really shine. Making it trivial to resize storage areas while the system keeps running.

**genfstab** isn't impressing me at all.  Some things are just too important to trust to less than perfect tools.  I'd skip using it.
Understanding an fstab takes about 10 minutes. Not hard at all. The manpage explains each field.  30 seconds of preliminary "what is a field" would probably help someone completely new, but once that is understood, it all becomes clear.

IMHO.

cigtoxdoc - if you join the ALE or ALE-NW meetings (50% online), someone can talk you through with however much information you need.  There's definitely a Macon LUG too.  I've met a few of those good people over the years.  ALE has multiple meetings each week. I think the SW and central meetings are all back to physical meetings - there is something magical about humans being in the same room, but ALE-NW has decided to retain both - online and in-person meetings.  We just started having in-person meetings again, but I'm pushing for 50/50 ... since the online meetings also provide some goodness that doesn't happen when people are only in the same room.

---

### Post by ActionParsnip on 2021-06-30
> **TheFu said:**
> Eeeew. With that number of partitions, I'd have used LVM and some LVs instead.  Getting the sizes correct at the partition level would be nearly impossible. That's were LVM and other advanced volume managers like ZFS really shine. Making it trivial to resize storage areas while the system keeps running.

**genfstab** isn't impressing me at all.  Some things are just too important to trust to less than perfect tools.  I'd skip using it.
Understanding an fstab takes about 10 minutes. Not hard at all. The manpage explains each field.  30 seconds of preliminary "what is a field" would probably help someone completely new, but once that is understood, it all becomes clear.

IMHO.
I'd just use LVM regardless. So much more flexible

---

### Post by cigtoxdoc on 2021-07-10
Thank you very much to all for your replies to my request for help.

First, I have been using Ubuntu on my Dell Vostro 3500 laptop since 2014.  It is my main PC.  It is dual-boot with the original Win XP Pro SP3.  It is a life-saver when Ubuntu misbehaves as I can access all my files on the Ubuntu partitions.  I have six or so other PC's, some dual boot with Windows 10 others standalone Windows 10 for dedicated use with chromatography data systems.  Some clients of my scientific consulting business want things done in Windows 10. MS Office, and Adobe Acrobat.  Others don't care.  So some of my Ubuntu-based machines also have PDF Studio Pro along with LibreOffice.  Both the Ubuntu user data partitions and the Win 10 partition and data files are backed up on commercial backup services.  Unfortunately, I did not have the fstab files backed up on the commercial servive

Second, at one time I had a Canonical support agreement, and support person who was helping me, had me set up the original disk partitions.  I was told at that time never to put my own files on the same partition with Ubuntu so you do not loose them if you need to reinstall Ubuntu.  Good advice except I have never figured out how to keep Evolution dats files off the Ubuntu partition, so all email goes through one of several commercial IMAP accounts.

Third, if one is supposed to keep non-OS files out of the partition that has the Ubuntu OS on it, then fstab should be automated, and instructions for installation of Ubuntu changed to advise users to set up a separate partition for user data.

Fourth, with respect to the suggestion to use Logical Volume Manager, sounds easy, but no instructions on how to recover if it does not work.

Five, if Canonical still offers support agreements such as I purchased some years ago, I would appreciate a link to such services.

John

---

### Post by cigtoxdoc on 2021-07-11
Easy solution here.  Much easier than I thought.  Just take what you get from genfstab and comment out anything that doesn't begin with UUID or /swapfile

Perhaps someone who knows what to do to get gensfstab to comment out anything that isn't UUID or /swapfile.

John

---

### Post by TheFu on 2021-07-11
The problem with gensfstab is that there are 50 other types of storage devices which could be mounted that is probably doesn't handle correctly too.  It is a hack for a tiny number of specific uses, not a general solution.  That's my guess for why it isn't used by other distros.

The Unix method to do what you seek is to run the gensfstab result through a filter. Those are a core skill for anyone who is running Unix systems, IMHO.  Most text processing tools are already installed on the system.  Nobody would make that an option to gensfstab because it is very trivial to use grep or egrep to achieve the result.  It is a different way of thinking from the MSFT way.  
This article tries to explain the Unix techniques: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

BTW, nobody here works for Canonical.  My LUG meets multiple times a week in your part of the world. There's a mix virtual/IRL meeting today. The knowledge is available if you show up.  If you seek just "what do I type" help, that doesn't interest me, but it might interest others on the LUG, for a price.

---

