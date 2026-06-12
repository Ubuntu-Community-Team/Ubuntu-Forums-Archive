---
title: "Preinstallation Question"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Samizdata on 2008-04-02
Here's to hoping the news is good...

Hardware layout:
HD 1 - 750Gb, 500Gb XP SP2 partition, 250Gb unused partition with a possibility of starting past cylinder 1024
HD 2 - 250Gb, 250Gb Vista partition

What I am interested in doing is setting up Ubuntu on the unused 250Gb partition.

What I am not interested in doing, however, is bollixing everything up.

So I figured I would ask if anyone would have suggestions, potential issues, or past pitfalls to share before I dive in.

I am a happy Ubuntu user on a dedicated machine, but I have always had a hankering to run it on my biggest machine, and I thought this might be an ideal opportunity.

Anything I should know before I get started?

---

### Post by housam on 2008-04-02
- First of all you have to back-up your data - just in case.
- Do defrage your first HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> partition editor)
- You can create up to only 4 primary partitions on single HDD.( you'll have one for windows )
-I suggest to create one more primary partitions for your data ntfs format and another two partitions for ubuntu, one EXT3 ( 50 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1-2 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

