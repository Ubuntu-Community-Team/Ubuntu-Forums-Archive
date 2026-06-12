---
title: "upgrade 6.10 to 7.04 fails"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by keithbunt1 on 2007-08-10
Hi,

Because the synaptic upgrade failed, I followed method two at [this link]("http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html").

Upon rebooting as suggested, GRUB selects 2.6.17.12, the latest kernel.  I get the initial UBUNTU loading screen, just a hairline completed, after a minutes fails into 

```
Busy Box v 1.1.3(deb 1:1.1.3-2ubuntu3)
/bin/sh: can't access tty; job control turned off

(initramfs) prompt
```

recovery mode selected in GRUB with the same kernel yields a number of startup messages, and shortly a

```
Begin: waiting for root file system
```

where after it hangs the system requring a cold boot.

trying to boot into 2.6.17.10, I get
```
Activating Swap ..... [ok]
checking root filesystem...
fsck 1.40-wip (14-Nov-2006)
/dev/hdb1: clean, blah blah files, blah/blah blocks [OK]

checking file systems...
fsck 1.40-WIP(14-Nov-2006) [OK]

```

At this point, it hangs the machine.

I had an unused SCSI card in the box, and I read in another forum that udev was giving SCSI people problems, so I yanked it out.  Same error messages.  Two drives in the machine are PATA.  I forget the organization, I bet think drive 1 has 2000/xp on it, and drive 2 is dedicated to ubuntu.

How should I proceed to fix this?  Boot off a live cd?  Recovery mode does not work.  I've got a decent amount of files etc stored on the drive, so I'd rather not nuke and start over.

Thanks

Keith

P.S. this is an old school Intel PII 333mhz/256mb ram

---

### Post by clyrrad on 2007-08-12
> (initramfs) prompt

Im no expert on this - but that is a really bad error to have - at least it was for me.

This happened to one of my machines a while back when the Partition Table was killed due to the hard drive over heating and dieing on me.

I had no way to recover the data from the drive, but I did thankfully have a daily backup to restore from.

When I was looking up that error message back when I had the issue, all things pointed to a corrupt partition table.  I am not sure if this is your exact problem too, but it may give you a place to start looking.

Hope this helps!

---

