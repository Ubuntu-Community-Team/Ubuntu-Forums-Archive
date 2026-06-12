---
title: "Which Windows/HP partition should I get rid of to install Ubuntu?"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by todzak on 2011-08-26
I've been running Wubi for a while, but want to install Ubuntu as on an actual partition.

Problem is:
I can't create an extended partition, because freaking HP/Windows is already taking up all of my hard drive with *4 primary partitions.*

They are: 

'Local Disk' (C:)
'RECOVERY' (D:)
'HP_TOOLS' (E:)
'SYSTEM' (G:)

So my question is: which of these primary partitions would it be best (least bad, rather) to get rid of in order to create an extended partition for an Ubuntu instillation?
Obviously I don't want to get rid of 'Local Disk'. But do any of you know what the other partitions even entail and whether one of them could go?

Now obviously, I don't want to get rid of 'Local Disk', but are any of the rest of them more disposable than the others?

---

### Post by Idefix82 on 2011-08-26
I suspect that the only one that you can get rid of without breaking the current Windows install immediately is D. The recovery partition is there, in case Windows badly breaks down at some point and you need to revert more or less to its virginal state using a recovery CD. I have never needed to do that. Usually reinstalling is just as good (or rather just as annoying, since this is Windows), provided you have the install disk. Note that recovery disc and install disc are not the same thing.

---

### Post by lisati on 2011-08-26
I've was pondering the exact same dilemma earlier today for a new laptop I purchased yesterday, and haven't come up with an answer yet, beyond making a set of system recovery DVDs in case I need them - which would make at least the RECOVERY partition redundant.

---

### Post by sidzen on 2011-08-26
Reboot with a new or newly-fomatted (FAT32) USB stick and move HP_TOOLS to it.  This seems to fool Windows into thinking it's another partition or hdd.

RECOVERY may be placed on C:\, then one has two partitons to make linux happy -- primary / and Extended

Best wishes!
(and always make a recovery/Boot CD before trying this out)

---

### Post by YesWeCan on 2011-08-26
What is the HP Tools partition? Could this one be made logical and still function?

---

### Post by YesWeCan on 2011-08-26
> **sidzen said:**
> RECOVERY may be placed on C:\, then one has two partitons to make linux happy -- primary / and Extended
I think Ubuntu only needs one primary, extended partition. / can be logical.

---

### Post by Quackers on 2011-08-26
Many people in the same position have removed the HP TOOLS partition then resized their C: partition to gain enough free space for Ubuntu.
The HP TOOLS partition contains some diagnostic tools which you will probably (hopefully) never need. Those same tools are (or were, at least) available on the HP website. Maybe check that first :-)

---

### Post by coffeecat on 2011-08-26
If your HP has a similar setup to my HP Mini, you've quoted the partitions in the wrong order. That's not your fault - that's the bizarre way Windows describes partitions. :) On my Mini, they were:

sda1 - SYSTEM
sda2 - Windows C:
sda3 - RECOVERY
sda4 - HP_TOOLS

On my HP Mini I removed HP_TOOLS. I believe it merely has the utility to create a set of recovery DVDs from the RECOVERY partition. So I burnt a set of DVDs before removing HP_TOOLS so that I have both the recovery partition and the recovery DVDs in case I need to restore the machine to its factory condition.

Don't remove the SYSTEM partition - that's the Windows 7 boot partition.

If you remove HP_TOOLS, you will need to shrink the Windows 7 C: partition as Quackers says (use Disk Manager in Windows for this) leaving space between the C: partition and the RECOVERY partition for your Linux extended with logical partitions. This will leave the space formerly occupied by HP_TOOLS up at the end of the drive but as this is only a few megabytes it's of little consequence.

---

### Post by ottosykora on 2011-08-26
I checked all on my HP ProBook 6550b which came with w7x64 and the same HP nonsense setup.

The recovery partition is possible to backup let say on a external drive, I did so on a good quality usb stick. The recovery manager can be pointed to it and will be able to use it later.

The HP tools, well also this you can make some backup and delete it. This I found had no particular function as the tools were not really running from them, there were just thigs stored there which were installed on the main hard drive volume anyway. The tools seems to be only for the case when someone sets up the computer with generic windows disk or so.
I could not find any time that something was really running from that tools part.

Anyway, I kept only the w7 and the w7boot and made the rest to one prim for xp and the rest extended for data and ununtu and so on.

---

### Post by ottosykora on 2011-08-26
>What is the HP Tools partition? Could this one be made logical and still function?<

definitely, so it is also possible to make the recovery partition to logical

can make image and copy back to one of the logical you can make within the extended.

---

### Post by Mark Phelps on 2011-08-27
The Recovery partition allows you to restore the PC to its ORIGINAL state -- which becomes more useless as time goes on!

A better solution is to do the following:
1) Download and install the FREE version of Macrium Reflect (MR)
2) Image off your current Win7 setup (using MR) to an external drive or to DVDs.
3) Use the MR function to create and burn a Linux Boot CD.

NOW you have a restorable copy of your Win7 install -- which you can use later.  You can now get rid of the Recovery partition.

---

