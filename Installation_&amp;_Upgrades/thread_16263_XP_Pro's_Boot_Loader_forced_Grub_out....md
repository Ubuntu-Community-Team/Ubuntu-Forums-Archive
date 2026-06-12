---
title: "XP Pro's Boot Loader forced Grub out..."
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by ghoat on 2005-02-20
[FONT=Arial Black][SIZE=2]Hello, 
    I'm a Linux Newbie and Warty Warthog is my first Linux install. :-)   Had it dual booting with XP Pro very nicely for about a week.   Ubuntu & XP Pro are on diffeent Harddrives.  I made another partition on the Ubuntu drive with XP Pro on it.  Now the Windows partition loader has forced Grub out and it only reads the 2 XP Pro OS's for choice selection.  How do I get the OS selector, either Grub or Window's,  to list all my OS's?  I can't get Ubuntu to load up so I wouldn't be able to run any Linux commands unless it can be done through Windows.  I do have Cygwin which may help. [/SIZE]  [/FONT]

---

### Post by seedubya on 2005-02-20
I'm a noob too.  I do know, however, that if you can get into XP you can download xOSL and install it from Windows.  This will give you a functioning boot manager.
Sorry but I don't have a link..........

---

### Post by andyjenkins on 2005-02-20
Get a rescue cd ([http://www.sysresccd.org/](http://www.sysresccd.org/) or others, just about any will do, could maybe even use ubuntu distribution cd), burn it.  Boot from it.

Once you are at a root console (command prompt with a '#'), do:

```
mkdir /mnt/ubuntu
mount /dev/hdbX /mnt/ubuntu

``` 

NOTE: replace 'X' in /dev/hdbX with your ubuntu partition (/dev/hdb1 maybe?).  You can either figure this out with fdisk (try 'fdisk /dev/hdb' then hit p) or, you can plug a few in, starting with 1 and counting up, until one of them works (i.e. doesn't say anything, just gives you another command prompt).

/dev/hda is your primary hard drive (ide channel 0 master), probably the one with Win XP on it.  /dev/hdb is ide channel 0 slave, probably the one with ubuntu on it.  There are probably a few partitions on /dev/hdb, depending on how you set up ubuntu.  I'm assuming you have one big ubuntu partition mounting to '/' on /dev/hdb1 - if this is wrong, post your partitioning setup (from fdisk or any other partitioning tool).

Now, do
```
chroot /mnt/ubuntu /bin/bash
grub-install (hd0)
```

Then, to be nice to ubuntu, log out of the chroot and unmount the ubuntu partition by
```
exit
umount /mnt/ubuntu

```

Then, reboot.  You should get a nice grub prompt.

---

### Post by ghoat on 2005-02-21
[FONT=Arial Black]I'll give that a try.   I have the Ultimate Boot CD but I'm going to try to boot from the Ubuntu distro first.  Hope it works.  Thanks. [/FONT]   :-)

---

### Post by wallijonn on 2005-02-21
What you did is normal.

You had hd0 - wxp, hd1 - Ubuntu.

So when you installed Ubuntu it wrote the MBR on hd0.

You then installed a second wxp on hd1, which caused it to write the MBR on hd0, which erased the GRUB loader.

---

### Post by ghoat on 2005-02-22
"What you did is normal.

You had hd0 - wxp, hd1 - Ubuntu."

Actually, I have 3 partions on hd0, an 80 gig WD, 1 with XpPro that I use daily, one with Ubuntu, and the other with XpPro on it that fails to boot as of a couple of weeks ago.  On hd1, a 40 gig IBM,  I have an XpPro partition that failed to boot with the other XpPro partition on hd0 (they were dual booting and I lost access to them after installing Acronis OS selector) and is still unbootable like the other.  On hd2, an old 2 gig Seagate, I have XpPro on a partition.  The Windows OS selector only reads the bootable XpPro on hd0 & the "emergency" XpPro partition on hd2.   I know it sounds a mess but I wouldn't have been in it if I hadn't installed the Acronis program.  Anyway, if I could get GRUB to read all my OS'd partions, I would be eternally grateful.   :grin:

---

### Post by wallijonn on 2005-02-22
Sounds like running 'fixboot' from the hd0 wxp partition 1 will scan all the drives and make a boot map. Then you would have to go and re-install GRUB.

---

### Post by ghoat on 2005-02-23
Would a Grub boot disk work?  I tried to make one with the System Rescue Disk for Linux yesterday but the command mount  /dev/fd0 /media/floppy wouldn't work....can a floppy like that be made off of a System Rescue Disk or does it have to be made on a regular Linux box?

---

### Post by wallijonn on 2005-02-23
If you can get into Ubuntu, [http://www.ubuntuforums.org/showthread.php?t=6195&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=6195&highlight=floppy)

---

