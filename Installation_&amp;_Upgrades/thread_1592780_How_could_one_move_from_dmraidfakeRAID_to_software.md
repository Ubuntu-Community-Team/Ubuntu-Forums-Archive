---
title: "How could one move from dmraid/fakeRAID to software RAID?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by ryuusei on 2010-10-10
Hi,

About a year ago I bought a new compy and decided to get on-motherboard RAID, and by golly I was gonna use it, even if it wasn't worth it.

Well, after one year, two upgrades, a lot of random problems dealing with RAID support, and a lot of articles read, I have come to my senses.

The problem:
I have a fakeraid using dmraid, RAID 1, two SATA harddrives. They are mirrors of eachother, including separate home and root partitions.  I actually found the method I think I had used here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The ideal solution:
No need to reinstall, no need of another drive, no need to format.

My last resort:
Buy a drive, copy my home directory, start from scratch, copy my stuff over.

Anyone have any ideas on achieving a solution any amount better than my last resort method?

Any input or experience would be appreciated.
Thanks

PS: if it matters, I'm on 64 bit 10.04 LTS

---

### Post by ryuusei on 2010-10-11
PS even a link to a similar forum topic would be appreciated! No clue what to do

---

### Post by ryuusei on 2010-10-24
<Bump>

Please help!

---

### Post by popat007 on 2010-10-24
Fakeraid is Software raid, what are you talking about. dmraid is used in linux if you want to use manufacture software raid (Intel, Nvidia, Via etc..) which comes install with Windows(through BIOS). If you want to dual boot with Windows, you must use dmraid inside Linux so you can see raid Volumes. you mean, you want to convert from software raid1 to software raid0?

---

### Post by ryuusei on 2010-10-24
Actually, fakeRAID is when a motherboard comes with cheap onboard RAID, usually only raid 1 or 5, and doesn't actually have a chip devoted to it.  Really, it is a little extra hardware that offloads the work of a RAID controller to the processor.

From the Ubuntu FakeRAID HowTo:
"Instead, they are simply multi-channel disk controllers combined with  special BIOS configuration options and software drivers to assist the OS  in performing RAID operations. This gives the appearance of a hardware  RAID, because the RAID configuration is done using a BIOS setup screen,  and the operating system can be booted from the RAID."

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I'm saying that in my BIOS I set up this shitty RAID and would much rather use standard software RAID and I know it is the same basic setup, but I don't know the process of switching over.

I imagine I need to search through my BIOS and find a magic "OFF" button and just start using dmraid all on its own, but I don't think I have the option in my BIOS to just stop managing the RAID it has already setup, and I don't want to risk data loss, so I'm looking for any suggestions.

Considering my own thought of a magic off button, I'll check after posting, but I don't remember seeing anything obvious.

---

### Post by ronparent on 2010-10-24
It is not as simple a finding an off button. Yes, you have to get into the raid bios to 'turn off' the raid. That bios has already placed meta data on your disks marking them as raid. To remove them you have to explicitly erase them (sudo dmraid -r -E /dev/sdx - for each raid member disk). Then uninstall dmraid. Although the removal of dmraid in itself will stop it from discovering the raid drives I also recommend the erasure of the meta data to prevent its reappearance in a future install when you have probably forgotten it is still there to  cause you problems.

The fakeraid is only there to permit access to raid drives used by Windows. However I have seen a lot of negative comment about it I don't feel are merited. I have found it reasonably reliable if you know what you are doing. If you read much on this forum you will see that use of software raid is no assurance that your life will be any easier.

---

### Post by ryuusei on 2010-10-24
Thanks ronparent,
I think this was a case of me using the wrong tool for the job.

I only have one linux installation and a raid 1 setup, and since dmraid is more suited for windows, it sounds like the right tool would be mdadm.

Thank you for the help!
My plan will be to turn it off in the BIOS, erase the metadata, and figure out a way to have mdadm pick up the array.
I am wondering if mdadm will be able to autodetect it.

Should I leave the metadata on the drives until after I figure out mdadm then?

Again, thank you to anyone for any help or suggestions!

---

### Post by ronparent on 2010-10-24
You better protect the data before you start because mdadm will not be able to autodetect the raid setup. You will have to reconstruct a software raid  from scratch. They work from a different set of symbolic links. Dmraid works from a set in /dev/mapper although with 10.10 a parallel set has been set up as /dev/dm-0, /dev/dm-1 etc. Mdadm works with /dev/md's. I doubt your dmraid raid partition tables could survive a transition.

---

### Post by psusi on 2010-10-24
Go into the bios and delete the raid array, or use dmraid -E to erase the fake raid signatures from the disks.  Then partition the second disk and use mdadm to set it up as a raid with only one disk.  Then copy everything from the non raid disk to the raid disk, and once you are sure you can boot from the raid disk and it is working well, you can add the non raid disk to the set with mdadm, and it will synchronize.

---

### Post by ronparent on 2010-10-24
I love it, I wish I had thought of it myself. But then again, only with a raid 1.

---

### Post by ryuusei on 2010-10-24
Yay!
 Thank you all so much!

Plan of attack:
  -Just-in-case back up of important data because I could mess things up if I make big mistakes
  -Turn off the RAID in the BIOS
  -Use dmraid -r -E to erase the RAID metadata on the disks
  -Boot drive 1 and use it to partition drive 2
  -Setup RAID with mdadm on disk 2, and copy over all data to disk 2
  -Boot from disk 2 and be sure everything is there and working properly
  -Add disk one to the mdadm raid array
  -Be happy!

I realized my old laptop harddrive is big enough to have a copy of all  my important data, so I may back up most important stuff on there  just-in-case.

Thank you all so much!

I will make sure to tell you how well it works and for reference of future readers!

---

### Post by psusi on 2010-10-24
You should ALWAYS back up your important data.  Raid doesn't protect against things like filesystem corruption, or just plain accidentally deleting/overwtiting the file.

---

