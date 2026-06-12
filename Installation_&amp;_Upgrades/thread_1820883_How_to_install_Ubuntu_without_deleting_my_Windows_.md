---
title: "How to install Ubuntu without deleting my Windows recovery partion."
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by Advice Pro on 2011-08-08
How do I go about this, in the ***Partition discs*** option during installation, do I just not choose ***Guided - resize SCSI3 (0,0,0), partion #1 (sda) and use free space***?

---

### Post by Mark Phelps on 2011-08-08
You didn't mention WHICH Windows version you have, but if it's Windows 7 -- you might NOT be able to do what you want.

You need to first determine how many primary partitions exist on your PC.  All too often now, the PC vendors (especially laptop) force 4 primary partitions onto the drives.  Since this is ALL you can have on one drive, you simply can NOT install any Linux distro into its own partition without deleting an existing partition.

Additional problems include:
1) Resizing: Win7 is especially touchy about its OS partition, such that if you allow the Ubuntu installer to resize it, you run the risk of corrupting it and rendering it unbootable.  You need to use the Win7 Disk Management utility to do the resize -- and it often won't let you shrink it much.
2) Partitioning: Win7 will let you create a 5th partition -- but it will automatically convert your partitions into Dynamic Disks -- which presents you with a whole new set of problems.  So, don't use it to create any partitions.
3) Recovery: Some laptops allow you to create recovery optical media -- but all that does is restore your original setup and wipe out everything you've done since then.  A better solution is to image off the current Win7 setup to an external drive. That will allow you to restore what you have now.
4) Boot Loader repair: Vendors typically do NOT provide optical media anymore, so if you run into a Win7 boot loader problem, you can't boot into anything to fix it.  So, BEFORE you do anything else, use the Win7 Backup Feature to create and burn a Win7 Repair CD.

Also, do NOT move, resize, or tamper with your Recovery partition in any way -- unless, you do the imaging thing and decide you no longer need it.  Messing around with it virtually guarantees that, when you need it down the road, it won't work anymore.

---

### Post by Advice Pro on 2011-08-08
> **Mark Phelps said:**
> You didn't mention WHICH Windows version you have

Vista

---

### Post by lkraemer on 2011-08-09
Since it's Vista I'd recommend doing the following:

1.  Boot a LiveCD of Ubuntu or Gparted and have a look at the current Partitions,
making a note of the sizes and sdax data.

2.  Once you know that you can make your decision.  There are a MAXIMUM
of four Primary Partitions on any Physical Hard Drive.  Vista probably is
installed on one Lareger Partition and then immediately after that  Partition
is your smaller (~8 Gig) Recovery Partition.  This leaves you two Partitions for
Ubuntu which is exactly what you will be needing.

3.  Boot Vista and run:
    Disk Clean
    Defrag
    System Configure - Storage Media  and shrink the Vista all you can.
    That number will be only around 15 Gig.  But that should allow you
    to install, and and get Ubuntu running.

4.  Boot Ubuntu then use gparted to move the Vista recovery Partition
    immediately after the resized Windows Partition.  The remainder will
    be used for Ubuntu.  (I used 10.04.3 LTS)
    At this point you can try shrinking Windows again with Gparted but
    you run the risk of Vista barfing.....but it might be worth a try.
    Next time you boot Windows it will give you a warning, and go
    through a disk check.....hopefully.  I DID NOT do what follows.......
    MAKE SURE YOU WRITE DOWN THIS SIZE SO THAT YOU CAN GO BACK TO IT!
    If you elect to do this, I'd stop at this step, and resize the windows
    partition, then boot Vista letting it do it's thing before you continue.
    It will SQUAWK about being corrupted....but it should work through the
    process and boot.  If it does, then move the recovery partition immediately
    after the resized Vista Partition.  If it doesn't boot I'd resize it back
    to the last size Vista created, Reboot Vista and see if it SQUAWK's again
    and proceed.   Then continue by sliding the Recovery Partition immediately
    after the Vista Partition..................then on to the next step.  

5.  Create a Primary Partition for Ubuntu that is ~2 * System RAM less
    than what is available.  This will become /

6.  Create your Linux-Swap which will be ~2 * System RAM.

7.  Install Ubuntu on /

I just did this on a Compaq 6700 for my neighbor, and it worked well.
Only problem was I really wanted to give Ubuntu 40 Gig, but Vista was
a HOG about not giving up enough Partition space.  

My next suggestion would be to purchase a New Drive, Insert it in your
computer saving the Windows for a Hot Backup. Then install Ubuntu or
the distro of your choice and never look back.  You will be there soon
enough anyway.  It's just a matter of which time you get infected and how
bad it is before you finally switch.  Better now than the next time....

As with anything you do with Wonders....You are on your own, and no guarantee
can be made as to your data or the safety of your your data unless you back it up.
But, if you are going to make a purchase to backup your data, you might as well
pop in the new Drive and install Ubuntu and be finished.

Let us know how it goes.  I know for a fact that 95% of this method works...

LK

---

### Post by YesWeCan on 2011-08-09
For more flexibility I'd crate an extended primary partition to contain all your Ubuntu partitions. Then there is no limit to how many you may have. :)

---

