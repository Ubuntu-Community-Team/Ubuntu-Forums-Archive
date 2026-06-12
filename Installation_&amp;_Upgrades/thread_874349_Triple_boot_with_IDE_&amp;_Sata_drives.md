---
title: "Triple boot with IDE &amp; Sata drives"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by jukingeo on 2008-07-29
Hello all,

I been having much trouble lately with setting up a triple boot set up across an IDE and a SATA drive.

These are the specs:

1) IDE Maxtor 80gig 7200rpm drive (Currently boots to Windows).
2) SATA Seagate 500gig 7200 rpm drive (Desire to boot to Ubuntu Studio and Puppy Linx


The IDE drive currently has Windows on it and it is what came with the computer. The Sata drive is where Ubuntu Studio and Puppy Linux will be installed on.

Ok, this was my line of thinking early on and it led to major problems with Grub.  I will say that it is also not entirely Grub's fault as my BIOS doesn't have separate boot-up settings for the SATA and Primary IDE drives.  Instead it has a 'flag' which is labeled IDE Hard Disk C:.  This flag is how my Bios boots up and it CAN switch from the Primary IDE drive to the SATA drive (if the SATA drive is the only one on the machine at the time).  

Without going into crazy details of what I just said in the above paragraph, I can say from every possible combination I tried with setting up Grub on the Linux (Sata) drive or the Windows (IDE) drive.  I had nothing but problems, including wiping out Windows a few times.  (In fact, right now I only have a bare bones Windows set up until I get this situation straightened out).

So tonight I had a bit of a brain storm (sadly it came a little too late...but better late than never).  Storage memory space is storage memory space, right?  So by right I have about 580gig total storage space.  So would it matter how I would like it to be set up?  No it doesn't.  So this is what I thought of doing:

1) Erase everything AGAIN (don't worry I have my important data backed up.
2) Install all three operating systems on the SATA drive ONLY.  Set up Grub on this drive.
3) Remove all boot flags or anything that is 'bootable' off of the IDE drive.  I would reformat this entire drive as a FAT32 storage drive so this way it could be accessed by both the Windows and Linux operating systems.

The good thing about this setup is that should I run out of space on the IDE drive (or should this plan not work) I can always replace the IDE drive with another SATA drive and keep my information on the main SATA drive intact.

I would assume that by allocating ALL the bootable operating systems to the one hard drive, Grub shouldn't have a problem with setting up the boot table.

So that is my first question.  Can it be done?

If the answer is a "Yes", then my next question would be how would I go about setting it up.

I would assume that I would put on Windows first, then Puppy Linux (but tell it's grub not to install), then finally Ubuntu Studio, capping it's installation off with the Grub installation and configuration.

However, this is just a guess on my part.  I would like to know the 'right' way to do it.

Any information would be much appreciated.

EDIT


[Solved-(Partially anyway)]

I decided to go full SATA and pulled the IDE drive out of my machine.  I set up all my operating systems and applications on the first drive and the second SATA drive is just used as workspace/storage area.

I began by installing Windows FIRST.  This is important that it is first so that it will not detect another OS and install it's own bootloader.  Then you would be in for the ride of your life if THAT happens.

Next I put on Puppy Linux, but told it NOT to install grub.

Finally I installed Ubuntu Studio and told it to install Grub on the MBR.

Worked first shot out.  My machine booted right into Grub and all my selections worked.

So this is what I learned:

1) Multiple booting from ONE hard drive-Very Good no problems
2) 2 Sata drives or two IDE drives-A little more involved, but should work
3) Combination IDE & SATA drives-very very very BAD!  Avoid this combination at all costs.


Geo


Thank You,

Geo

---

