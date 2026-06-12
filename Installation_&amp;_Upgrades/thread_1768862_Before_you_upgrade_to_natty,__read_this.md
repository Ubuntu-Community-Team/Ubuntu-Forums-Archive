---
title: "Before you upgrade to natty,  read this"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by jmoseby on 2011-05-27
I run several Ubuntu servers on older hardware.  My web server was nagging me to upgrade to natty. It says:

```

New release 'natty' available.
Run 'do-release-upgrade' to upgrade to it.

```So I do it.

During the upgrade I see:

```
error: Found two disks with the index 0 for RAID md0
```...once for each physical drive.  At the end of the upgrade, I am prompted to reboot.  I decline because I'm afraid grub2 is now munged.

A google search finds this: 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/776422](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/776422)
... in essence, a verification that a bug exists, affects more people than just me, and is repeatable.


I remove grub2 and replace it with grub per instructions on this page:
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy")

Reboot, and no joy.  A brick.  My server will no longer boot, nor will grub recognize the array, and therefore cannot find /boot/grub.

Fortunately, I make images of my servers prior to any major changes (like a dist upgrade).  Because I am in a hurry to get our web server back in production, I forgo any more troubleshooting and restore my backup image. I am now back at square one with a happy server.  If it weren't for my backup image, this would have been a big problem.  Essentially, I lost all data on the array, as far as I could tell. (Really, probably not lost, but not immediately apparent how to get back to it.)

In my opinion, one of the shining achievements of Ubuntu (and linux in general) is its ability to extend the usefulness of otherwise obsolete hardware.  For a grub update to brick a previously happy server shakes my confidence in the update process.  I normally run 'update/upgrade' without much thought.  Now I will worry about it.

I realize maintaining backwards compatibility for every known hardware  combination is impossible, but I think that putting the effort into  maintaining linux in general, and Ubuntu in particular, as the go-to OS  for resurrecting legacy hardware is an important task that is worth putting effort into.

Questions:

Could I have recovered this server if I did not have the backup image?  
Since this is now a known problem, should the grub devs code a fix for it?
Can I still upgrade to Natty and not include the buggy grub update?

---

