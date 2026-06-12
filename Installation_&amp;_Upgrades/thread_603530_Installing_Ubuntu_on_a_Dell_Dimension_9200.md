---
title: "Installing Ubuntu on a Dell Dimension 9200"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by dom on 2007-11-05
I have a Dell Dimension 9200.

It has 4GB Ram and two by 160GB hard-drives (ATA).

The drives are raided, and though this is the case Ubuntu see the two drives instead of just one raided volume.

Ubuntu Server is the install I am using.
The 7.10 [as of 2007-11-01] disk locks the keyboard before the install can be initiated.
The 7.4 disk works. 

The installation works. 
But the reboot fails with Grub "Error 2".
Ubuntu will install, regardless of the bios configuration I tried for the disks.
But it will not boot.

After some reading, I see that the 'raid' in this machine is not RAID. It is just stamping the drives with a tag and the os has to the RAIDing. Whatever.

Nothing in the BIOS affects this, so I reset it back to being raid on as it had been originally.

I then booted the computer, and just after the dios load, and before the os load, there is the RAID Bios config.

I press CTRL + I to enter the config for this and delete the raid volume.

Now the two disks are used as just that. 

I reboot with the 7.4 ubu cd, partition and install the disks, and at the reboot it all works fine.

Now I am upgrading to 7.10.

---

### Post by earobinson on 2007-11-05
wait, maybe im dumb, you dont seem to have a problem here do you? But thats a neat story.

I jelous of your 4 gigs of ram :(

---

### Post by dom on 2007-11-05
:)

The 7.10 Ubuntu server cd just didn't work.

Also It took me a bit of time to figure out how to get around the grub "Error 2", so I thought to post about it.

My first instincts were that it 'would just work'.
Second to alter the system bios.

I had to do a bit of reading to understand that the 'raid' wasn't raid, and then realise that the psuedo-raid/fake-raid had it's own bios-type-thing, and that from there i could delete the fake-raid virtual volume, and the disks would be relased to normal use, and ubuntu would then have no trouble booting.

---

### Post by dom on 2007-11-05
I have also now tried teh 7.10 ubuntu desktop live cd and it also locks the keyboard.

There is a countdown timer, and when it reaches 0, nothing happens :)

---

### Post by Pumalite on 2007-11-05
Make sure you do md5sum, burn at 4x, etc. If nothing works, you have the Alternate CD.
(maybe 4 GB RAM is too much for Gutsy. Try with 2 GB and see what happens.)

---

### Post by Denbert on 2008-05-05
> **dom said:**
> I have also now tried teh 7.10 ubuntu desktop live cd and it also locks the keyboard.

There is a countdown timer, and when it reaches 0, nothing happens :)

I'm having the same error, and deleting the raid made GRUB works.

Thinks its something with the INTEL Raid controller, Debian 4 netinst has same problem.

The installer try to install GRUB on hd0 but the OS is installed on sda as this is SATA.

Deleting the RAID with CTRL-I and then reboot gives GRUB and OS boots smoothly - Thanks for this hint, as I was starting to go mad:guitar:

---

