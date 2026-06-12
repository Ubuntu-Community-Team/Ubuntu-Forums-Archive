---
title: "Using entire disk Installation"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by mlyons16 on 2008-03-02
So umm, I've officially had it with @%#$! Windows. So if I were to use under the install options 'Guided - Use entire disk', that will effectively format my hard drive and install Ubuntu as the one and only OS correct?

My contingency plans are: 

A) If I for some absurd reason need Windows back I can just use my HP Recovery CDs and install Windows.

B) I still have my laptop running Vista, but I plan to at least dual-boot that sooner or later.

Sound good?.... Should make for a pretty easy install right.. No partition planning I have to do in Windows or anything if I'm just gonna use the whole HDD, correct?

---

### Post by Shazaam on 2008-03-02
Normally Recovery Disks rely on a hidden OEM partition to perform a re-install. So If you format the whole drive you will WIPE OUT that hidden partition. Investigate before you leap.

---

### Post by mlyons16 on 2008-03-02
oh really... okay then.. ya'll i'll ask HP if the disks alone are sufficient of if they rely on the recovery partition. 

I'm probably going to do a system recovery pre-install anyways to get a nice clean windows installation (and clear off my year's worth of junk)... then I'll do the partition shrinking from the vista disk manager i guess.

When I'm installing.. (this is where I get stuck)...

I want to use option: guided- use largest continous free space instead of manual.. I'm afraid i don't know how to properly use the manual option... can you maybe help me there... as I will be eventually dual booting one if not both of my systems.

---

### Post by mlyons16 on 2008-03-02
Starting the recovery from recovery discs : use this section when the hard disk drive has been replaced or damaged and you have a set of recovery discs. Recovery discs can be those ordered from HP or those created by the Recovery Disc Creator software.

I did find that on HP's Support Site... do you think that would be a No, it doesn't require the partition... It can just run it from the cd, it doesn't require the partition in conjunction with the CDs to perform a recovery?

The instructions are at:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00814731&cc=ca&lc=en&dlc=en&product=3437575&dlc=en&lang=en#](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00814731&cc=ca&lc=en&dlc=en&product=3437575&dlc=en&lang=en#)

---

### Post by housam on 2008-03-02
> **mlyons16 said:**
> 
I want to use option: guided- use largest continous free space instead of manual.. I'm afraid i don't know how to properly use the manual option... can you maybe help me there... as I will be eventually dual booting one if not both of my systems.

To use the manual way :
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> Gparted )
- You can create up to only 4 primary partitions on single HDD.( you already have two of them , one has windows and the other for the recovery )
-I suggest to create one more primary partitions for your data and another one as extended partition which can be devided to many logical partitions (resizing windows partition and creating two new partitions)
- the extended partition can be devided to 2 partitions : one EXT3 ( 10 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

### Post by mlyons16 on 2008-03-02
Ya, I think I might just avoid all of that and just use entire disk. I asked HP and they said their recovery cds are independent of the oem partition. You can use that partition instead of the cd's, but if the recovery partition is damaged or missing, then one can use simply the recovery cds in place of the partition.

---

### Post by mlyons16 on 2008-03-03
So just letting everyone know that I'm going to do a full disk installation tonight on my HP desktop. Like I said, and I've researched that the recovery cd's are sufficient on their own, I could always reinstall Vista, and do a dual boot.

Who knew I'd do such a drastic conversion to Linux. Let's hope it works out! :p

---

### Post by mlyons16 on 2008-03-04
When I do select to use the entire disk, Ubuntu will do all the formatting correct? I don't need to make any disk preparations in Vista or Ubuntu beforehand?

---

