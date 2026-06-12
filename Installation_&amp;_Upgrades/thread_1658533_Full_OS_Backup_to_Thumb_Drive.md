---
title: "Full OS Backup to Thumb Drive"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2011-01-02
The problem is not a lack of information, it is a waterfall of overlapping and often contradictory information.

Here is what I have and what I want to do:

I have a fresh Maverick install--and nothing else on the hard drive--which has been customized and augmented in various ways.  The install has a dedicated **/boot** partition, and that is where GRUB2 was installed.

At present, I back up my home directory to (among other places) a USB stick.  What I want to do as well (or instead) is back up my entire system to a bootable USB stick.  Moreover, I want to be able to keep that backup in sync with my existing system, updating on a frequent basis.  In effect, if my entire hard drive were destroyed, I would like to be able to completely restore from the USB stick.

Now it *seems* to my doubtless ignorant mind that all that is needed is for the stick to get a simple MBR on it, after which I could just use rsync to keep the entire rest up to date (omitting, if one wants, things like the /tmp directory).  Is that over-simplistic?  And in any event, how would I most easily go about first getting the bare MBR onto the stick?  Would a simple use of mbr-install do the trick?

I suppose the long way round would be to install from the Live CD to the stick, using manual format and setting partitions analogous to those on the main hard drive, *then* use rcync, but that seems tedious.

My thanks for any help anyone can give here.

---

### Post by C.S.Cameron on 2011-01-02
If the partitions on your hard drive are smaller than your USB stick you can clone it to the stick using:
```
dd if=/dev/sda of=/dev/sdb
```
Confirm that sda is what you want to clone and sdb is the target.
This will take care of your MBR etc.

---

### Post by snuffy47 on 2011-01-02
Sorry to jump in here but I am searching for the best way to Clone a OS 10.04 hardrive for a hot spare for recovery.

The is what you posted the best way?

---

### Post by C.S.Cameron on 2011-01-03
> **snuffy47 said:**
> Sorry to jump in here but I am searching for the best way to Clone a OS 10.04 hardrive for a hot spare for recovery.

The is what you posted the best way?

It works for me but takes time with large drives.

---

### Post by owlcroft on 2011-01-03
Re:

[INDENT]**dd if=/dev/sda of=/dev/sdb**[/INDENT]

Thank you.

That looks frighteningly simple (by which I mean that simple things often have frighteningly great power).

Now, if I do that, then--as I am understanding it--my thumb drive becomes an exact, bootable equivalent of my hard drive, MBR and all.  As I make changes over time on the hard drive, can I just keep the thumb drive up to date using rsync and still have a 100% bootable exact equivalent of my then-current hard drive?  (Assuming none of the changes are to the MBR)

---

### Post by snuffy47 on 2011-01-03
I have a large storage raid array mounted in the media folder.

When using this command will it try to back that file system up also or just the OS information?

---

### Post by vader95 on 2011-01-03
You could use remastersys
 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by C.S.Cameron on 2011-01-03
Some more on dd:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

