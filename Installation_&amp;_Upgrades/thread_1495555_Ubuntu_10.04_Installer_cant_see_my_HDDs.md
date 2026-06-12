---
title: "Ubuntu 10.04 Installer cant see my HDDs"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Styrofoam on 2010-05-28
Am completely new to Ubuntu. I decided to change as I salvaged an old old computer and got it back into working order. Windows 7 kills the computer and the media being served is sluggish and slow.

The computer spec are as follows:
Asus A8N32-SLI Deluxe Bios 1303
Asus Nvidia En210
1 x Maxtor 160gb SATA2 (plugged into port 1)
3 x Samsung F1 1tb SATA2 (plugged into port 2, 3 and 4)
LG DVD Drive
AMD 939 Socket @ +3200 (1.8ghz actual speed)
2gb Ram (4 x 512mb sticks)


I've tried multiple combos and solution from installing from Windows 7, installing from the CD Live session and swapping the drives to different SATA2 ports.

I even partitioned my main drive to have 60gig to install Ubuntu on but it does not see it. I tried disconnecting all drives but 1 and it still does not see it.

I am getting ready to format the entire Maxtor drive and see if I can install Ubuntu from scratch on there but I doubt it. The only time when I was able to see a drive to install Ubuntu on was when all drives was plugged in. It showed me the option to install it onto my 1tb drive that was plugged into port 2. 

Only that specific drive (that drive in Windows is assigned the drive letter K) in that specific port will work. I have tried other drives in that port or the same drive (K drive) in other ports with no luck.

This is a very strange problem. I changed the BIOS Silicon Image controller to be Raid or SATA2 and that does not affect anything.

Is it just me having this problem or am I doing something wrong?
The furthest I got was to a point where Ubunto Installer told me I haven't specific a root partition and should sort it out through using the Wubi installing in Windows 7 on the 3rd partition of my OS drive.

Sorry for the long read, hope someone knows something about this and thanks in advance :)

---

### Post by lmarmisa on 2010-05-28
Maybe the chipset (SATA controller) of your computer is not supported by Ubuntu. This is the case of the Marvell 88SE6145, for example. I have a server computer with this chipset and I am not able to run Ubuntu there.

---

### Post by Styrofoam on 2010-05-28
That is a very fair point. It does seem like its a Raid Controller comparability issue. Is there a list of Compatible Raid Controller lying around somewhere?

I'll start looking into that for now and confirm my findings.

Oh, I should also mention that Ubuntu is able to find all my HDDs. Just the installer isn't able to see them. Could this be a problem with Wubi and not Ubuntu itself?

---

### Post by darkod on 2010-05-28
If you can see them in Gparted in live mode, it's most probably they have raid metadata settings on them, if they were ever used in raid. I don't know whether for your protection, not to destroy your array by mistake, the installer ignores disks with raid metadata.

First go into BIOS and make sure you disable all RAID settings, if not planning to use the fakeraid.

Then boot into live mode, and for all disks that are not recognized by the installer, do:

sudo dmraid -r -E /dev/sda (also for /dev/sdb, /dev/sdc, etc if you need to)

That should ask you if you want to remove raid settings. Once that is done, I think the installer should see all disks just fine.

PS. On the other hand, if planning to use RAID, you should use the alternate install cd which is designed for RAID and/or LVM.

---

### Post by Styrofoam on 2010-05-28
Thats a good point. The drives use to be in a raid 5 array but I broke that up and kept them as separate drives now this may change in the future but for now they're not a problem.

The 1 drive I want to install Ubuntu on is the 160gb Maxtor drive. That drive has been fully formatted before Windows 7 so that shouldn't be a problem. I will try to do a clean installation of Ubuntu only onto the drive later which isn't preferable but will have to do. 

I found only a single post that I found relevant on google here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555530](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555530)

It would appear that Ubuntu installer isn't compatible with nVidia nforce 4SLI Sata chipset. Ubunutu can see all of my drives fine, its just the installer that wont for some reason or another. Can anyone confirm that Wubi or Ubuntu isn't compatible with nforce4 Sli?

---

### Post by darkod on 2010-05-28
Just to remind that formatting a disk DOESN'T remove the metadata. Try the command on the Maxtor too, nothing to loose. It might have been used in raid even without you knowing it.
Or when you briefly enabled RAID as you said, that's sometimes enough to get some metadata traces on it. Windows wouldn't show it, so some remains might be there from much earlier.

---

### Post by darkod on 2010-05-28
> **Styrofoam said:**
> 
I found only a single post that I found relevant on google here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555530](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555530)

It would appear that Ubuntu installer isn't compatible with nVidia nforce 4SLI Sata chipset. Ubunutu can see all of my drives fine, its just the installer that wont for some reason or another. Can anyone confirm that Wubi or Ubuntu isn't compatible with nforce4 Sli?

That is still not confirmed as bug, it's only a report by someone. Who knows, maybe he had different issue in fact. Usually other people with the same issue would report there and there is no one else. Maybe that's why it wasn't even confirmed as a bug. Plus, he is talking about the Beta 1, not the final release.

Further more, you said one of the Samsung disk is seen by the installer. If the installer can't work with the sata controller, it wouldn't see any disk at all. Makes sense, right?

The two Samsungs were used in raid, so that's why they don't show.

As for the Maxtor, I still think it also has metadata on it, but you are not aware of it. Running the mentioned command will show this for you, and remove the metadata if found.

---

### Post by Styrofoam on 2010-05-28
darkod, your a genius!!!

It worked perfectly, I thought I tried that already but apparently not, I must've tried something similar or did it to a wrong drive.

This drive was in a raid array about 5-6 years ago hehe.

Cant wait to get crackin on Ubuntu and see how the media streaming goes :)

Thanks again for the amazingly quick replies and help :)

---

### Post by darkod on 2010-05-28
You are welcome. Enjoy it now.

---

