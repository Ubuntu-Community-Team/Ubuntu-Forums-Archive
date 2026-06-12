---
title: "USB transfer speed in 11.04"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2011-07-13
Can anyone tell me if the problem of slow usb transfer speeds has been resolved in 11.04 (Natty Narwhal)? I am currently using Lucid and facing the problem of slow usb transfer speeds which has always been there in ubuntu but everything else is running just fine for me so I see no reason to upgrade yet unless the new OS has solved this problem.

---

### Post by mikewhatever on 2011-07-13
Are you sure there is an Ubuntu related problem of slow USB transfer speed? If so, can you explain in detail why you think that's the case.

---

### Post by davy jones on 2011-07-13
I have used various pen drives as well as external hard drives and that's the case with all of them so it can't be the drives. I get speeds of around 10-11 mbps with pen drives and around 20 with hard drives. Its pretty slow so around a year ago I started searching the net to find out if there could be something in Ubuntu which causes this and I saw many posts saying that this is a problem which has always been there in ubuntu. So I just want to know if its been resolved in the new OS

---

### Post by mörgæs on 2011-07-13
10-11 mbps is a normal speed for a USB 1 memory stick in Ubuntu. There are many bug reports in Launchpad concerning slow transfers, but they concern much slower speed.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069) (and duplicates)

---

### Post by davy jones on 2011-07-13
These are USB 2.0 sticks and drives and my laptop also has USB 2.0. In other OS's USB 2.0 drives have speeds which are several times higher.

---

### Post by mörgæs on 2011-07-13
There are some workarounds here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177235](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177235)

Do they help?

---

### Post by mikewhatever on 2011-07-13
> **davy jones said:**
> I have used various pen drives as well as external hard drives and that's the case with all of them so it can't be the drives. I get speeds of around 10-11 mbps with pen drives and around 20 with hard drives. Its pretty slow so around a year ago I started searching the net to find out if there could be something in Ubuntu which causes this and I saw many posts saying that this is a problem which has always been there in ubuntu. So I just want to know if its been resolved in the new OS

These are more or less the speeds I get in both Ubuntu and WindowsXP. If you want faster transfer speeds, consider switching to USB3 or eSATA.

---

### Post by davy jones on 2011-07-13
> **mörgæs said:**
> There are some workarounds here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177235](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177235)

Do they help?

Ok this does not really help because (I know I may sound like a beginner here) there's no "drive" tab when I click on properties in nautilus. But when I look at the drive details in the Disk Utility option in Administration, it says USB 480 mbps.

---

### Post by davy jones on 2011-07-13
> **mikewhatever said:**
> These are more or less the speeds I get in both Ubuntu and WindowsXP. If you want faster transfer speeds, consider switching to USB3 or eSATA.

I find that really surprising because I've seen 7-800 mb video files being transferred within a few seconds in Windows XP (USB 2.0)

---

### Post by davy jones on 2011-08-21
I've seen that formatting the drive to a different partition type changes the transfer speed. On a FAT pen drive I was getting speeds of around 10. But I was forced to reformat it to NTFS since it is not possible to transfer files larger than 4 GB in FAT drives and now the transfer speed has gone down to 3-4. Formatting it to EXT4 again gives a speed of 10 but then the drive is not recognized by any other device (such as my BD player). Is there a work around to this?

---

