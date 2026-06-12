---
title: "Possible Partition Gotcha"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by ytene on 2007-01-07
Hey everyone, apologies if this is a repeat posting but thought worth passing on.

I've just upgraded my Breezy system to Edgy - and hit a minor issue with partitions. The original configuration of the system [under Breezy] was as follows :-

/dev/hda1    /boot      250Mb
/dev/hda5    /            16 Gb
/dev/hda6    swap      4 Gb
/dev/hda7    /usr       16 Gb
/dev/hda8    /home    16 Gb
/dev/hda9    /var       16 Gb
/dev/hda10  /tmp      5 Gb

The first partition went into a primary, all the rest were logical partitions within an extended partition. Rather than "sudo apt-get..." etc I decided to perform a re-installation, primarily because I wanted to see what Edgy's new installer looked like.

I elected to edit the partition table manually and to assign file systems to the pre-existing partitions that were set out on the disc [as illustrated above]. You'll be aware that this is a 2-stage process: defining or validating the partitions, then mapping file systems to those partitions. During the installation process both stages seemed to work OK, until I clicked the "forward" button on the second screen. 

The installer repeatedly gave me an error message to the effect that "You must have a root partition". After some gnashing of teeth and asking the PC, "What do you think *that* is, Scotch mist?" realisation dawned and I basically reformatted the system, removing the /boot partition and ensuring that the "root" partition was the first on the disc. For good measure I migrated this from a logical partition to a primary at the same time. So now my root partition is the only primary - all the rest are logically within a single extended partition on the back of the disc.

Installation worked smoothly...

It's interesting to see how a configuration that was acceptable to Breezy is now unacceptable to Edgy [and, I believe, to Dapper as well - need to check that]. I'll concede that my original HDD layout was unconventional and, while OK, probably not the best idea around. I hope the now working setup is a little more sensible. This "problem" almost certaily comes as a tightening of the logical "rules" within the installer and is no bad thing. What would be interesting to find out - and I might have to fling another HDD in and find out - is to ask what would happen if I *had* tried to use "upgrade" and "dist-upgrade" over the existing partition allocation. I wonder if Edgy would have booted??? If I get the time and inclination I'll try that and post the results as a comment to this entry.

---

