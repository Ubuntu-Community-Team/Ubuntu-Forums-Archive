---
title: "Won't boot off RAID after install: P965 MB with SATA RAID 1"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by RickNak on 2007-04-03
I've tried installing 6.10 and 7.04 beta alternate without success on my Dell E520, which has an Intel P965/G965 MB and thieir SATA RAID 1 controller.

The problem appears to be the RAID controller: are drivers available?  It will install on a partition, but Grub doesn't get installed properly, and the system just boots back into Windows as if Ubuntu was never installed.  (Same problem with Solaris 10 and Fedora Core 6, too.)

Other than that, it does appear to boot and run the install smoothly -- just Grub doesn't get installed in the correct spot.  (On Fedora Core 6, an advanced option for Grub installer offered to put it on the RAID, but that resulted in a Grub hard disk error on the next boot. Had to use the resource CD to run fixboot/fixmbr to get the machine booting again.)

Ideas, anyone?  I'm so close, and I'm almost there!

---

### Post by djRobbieF on 2007-04-05
When installing the Linux OS, did you remember to set the filesystem type to "physical volume for RAID" instead of "Ext3 journaling file system"?

:popcorn: 

I don't know why the popcorn is there.  I just thought it was cute.

---

### Post by dschultz on 2007-04-05
I'm struggling with SATA RAID-0 myself.  When I configure all 3 of my disks for RAID and then setup all drives to one large volume, I am no longer allowed to create more than 1 partition on the drive.  When I play around and split things up (which is not what I want to do as I wanted a raid-0) I am still running into a wall where the GRUB or LILO will not start up.  

I've read somewhere that RAID volumes cannot be used to boot up...  same with LVM's.

---

### Post by loverboy on 2007-10-03
I'm having the same problem. I just built a new pc amd 64 5200 with two SLI video cards and I have 4 500 gb drive attached to a SATA raid controller card and I have setup RAID 10. Now i'm using the 64 and 32 Ubuntu Live CD's now after installing both of then I'm getting the message of Error 2 and I'm still unable to install. I need help after two days and I'm brand new to Ubuntu.

---

