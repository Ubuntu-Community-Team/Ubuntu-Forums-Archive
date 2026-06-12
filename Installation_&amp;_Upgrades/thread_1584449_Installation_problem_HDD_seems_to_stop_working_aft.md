---
title: "Installation problem: HDD seems to stop working after some time"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by chrischu on 2010-09-29
Hi guys!

I recently bought a Shuttle XS-35 Mini-Barebone-PC and filled it with a 2GB Corsair RAM and a 1 TB WD Scorpion Blue Drive.

After assembling all the parts I simply wanted to install Ubuntu but it simply doesn't work. During the installation sometimes there occurs an error like this:

> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

Sometimes the setup just disappears (literally: when I came back from doing some errands the setup window had just disappeard and there was nothing else there). 

I thought it could help to format the drive before the installation of Ubuntu and therefore made an USB drive with the Parted Magic Live CD. There I used the tools to check on the health of the hardware (for 4,5 hours) and the tool reported everything was fine (so I kinda moved away from the fact that it is a hardware error). 

However then I had the idea it would be good to kinda get the drive to a completely clean state and used the tools to safely wipe the whole HDD (by writing zeros everywhere as the tool tells me). The tool ran good for around 30 minutes but suddenly the write speed showing in the console window would go down to 0B/s (meaning basically nothing at all I suppose). I tried it 2 more times and it always came to a halt at the 10-20GB mark. 

So this lead me to belief that that is also the problem while installing, that my drive doesn't want to wark anymore but rather just sleep a bit.

What could be the problem? Is it a hardware error? Is there some linux system setting that could whip my HDD whenever it gets lazy? Did I do something else wrong?

---

### Post by plucky on 2010-09-29
Just a thought,check the BIOS settings for how long it is set before the BIOS will put the system to sleep and turn off the hard drives.If it is too short,maybe it is coming in during the install as it thinks there is no mouse or keyboard activity.

Good Luck

---

### Post by chrischu on 2010-09-29
I already searched through all the BIOS options and there seems to be no setting for this.

---

