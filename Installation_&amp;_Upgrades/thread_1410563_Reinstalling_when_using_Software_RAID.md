---
title: "Reinstalling when using Software RAID"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by aglc2005 on 2010-02-18
Hello, I am running a Linux Software RAID on my system. If I were to reinstall, what kind of complications should I prepare myself for? I have my /home on a separate RAID partition (and drives for that matter), will I lose any of this upon a re-installation? I would appreciate any help with this. Thank you in advance.

---

### Post by yogesh.girikumar on 2010-02-22
Hi,[INDENT]      > I have my /home on a separate RAID partition (and drives for that matter), will I lose any of this upon a re-installation?   [/INDENT]    There are risks involved when trying to install an OS on an existing RAID setup. Doing something like this is risky to the data in the disk. So it is always a good idea to have a back up of all your important data.


       That said, you can try to install the OS on the software RAID. Be sure to choose manual partitioning and make sure that you choose to leave the existing data intact when partitioning. You can simply specify just the filesystem to use and the mount points.


       Here are some pointers to resources:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
If you want a multiboot environment on a single RAID: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by darkod on 2010-02-22
> **aglc2005 said:**
> Hello, I am running a Linux Software RAID on my system. If I were to reinstall, what kind of complications should I prepare myself for? I have my /home on a separate RAID partition (and drives for that matter), will I lose any of this upon a re-installation? I would appreciate any help with this. Thank you in advance.

I have never tried it but I assume there is not much difference as with standard non-raid install. Use the alternate cd and the partitions should be recognized.
Then select the / partition with mount point / and select to be formatted.
For /home select the mount point and make sure you DO NOT format it.

And that should be it, in theory at least.

You could also try a test in Virtual Box. Make a similar soft-raid setup, put few files in /home, make a reinstall and see it they are there.

---

### Post by aglc2005 on 2010-02-22
> **darkod said:**
> I have never tried it but I assume there is not much difference as with standard non-raid install. Use the alternate cd and the partitions should be recognized.
Then select the / partition with mount point / and select to be formatted.
For /home select the mount point and make sure you DO NOT format it.

And that should be it, in theory at least.

You could also try a test in Virtual Box. Make a similar soft-raid setup, put few files in /home, make a reinstall and see it they are there.

Okay, that's what I was thinking it would be. I never thought about the Vbox to test it out. I'll give that a shot first.

---

