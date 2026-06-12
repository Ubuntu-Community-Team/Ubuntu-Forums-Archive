---
title: "Post-Install NTFS Partition size confusion"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by jgaynor on 2007-04-23
An unlucky series of partition moves, copies and resizes has led to GPartEd saying my NTFS partition is one size, but windows thinking it's another.

Order of events:

- Installed Feisty using the 'resize NTFS partition and used freed-up space' option. Accidentally made my windows partition 13 GBs (my bad - see sda1).
- Began attempting to fix this - resized ubuntu root partition to ~10GBs. Screenshot [**here**]("http://gaynor.org/images/images/Screenshot.png").
- Got to [**this**]("http://gaynor.org/images/images/Screenshot2.png") state, where I had things as I wanted. If this state was real, I'd be happy.
- Upon booting into windows, I found [**this**]("http://gaynor.org/images/images/screenshot3.jpg").  Windows still thinks it's partition is only 13 GBs.

If I remove 1GB of files from the NTFS partition in windows, the same amount is removed from the GPartED representation of that partition in lunix. I've attempted to resize again in the hopes of it 'shocking' windows into realizing the size of the partition, but no dice. Honestly I don't know which of the two operating systems is telling me the truth.

I would really like to get the NTFS partition utilize the 12+ GBs it's not recognizing. Any ideas? Thanks for your time!

---

### Post by jgaynor on 2007-04-24
If anyone encounters this same issue, turns out that GPartEd resized the partition correctly but did not do the same for the NTFS filesystem within the partition.  An ntfsresize on the volume in question fixed the problem.  More on this [**here**]("http://ask.metafilter.com/61135/Partitioning-Wizard-My-***") if you're interested.

---

