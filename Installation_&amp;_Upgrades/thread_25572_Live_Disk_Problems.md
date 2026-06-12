---
title: "Live Disk Problems"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by charles_linux1 on 2005-04-10
System- Acer travelmate 2300, Win XP, relatively new lap-top with Intel 1.4 Ghz Celeron.

Problem- Live Disk will not start up. There is an Acer splash screen prior to the Win Xp logo appearing that allows you to access Bios by hitting F2 (look below). The system just loads up Win XP as usual. Complete decription of my actions.

1. Downloaded 5.04 iiso image, extracted files then burned to a CD. All folders, files visible. Including 'start" files. 

2. Changed BIOS priority to boot CD first.

3. Tried cold start as well as restart, disk not accessed, win xp loads as usual. Tried several burn programs to burn on several disks (Not sure if relevant but I did it)

Question: Is there anything I'm missing here? ANy other parameters for XP that need to be changed? I'm wondering if acer placed another partition on my system which is over-riding the bios? Does the disk have to be formatted in a certain way? Each of the disks (4) that I tried had one or two minor 1mb files on them (Strapped for cash!).

Will not put Ubuntu on my drive till I get the live-disk to work.

Thanks- frustrated.

---

### Post by miklov on 2005-04-10
What do you mean when you say you extracted the files?

The livecd download just comes as a single .iso file.

If you use Nero Burning Rom  go to the Tools menu --> Burn Image.

I believe you can also use this to check the MD5sum to make sure that the download was not corrupted.

---

### Post by SmallOak on 2005-04-10
> extracted files then burned to a CD Maybe I am wrong here, but shouldn't you burn the ISO direct to CD, not extract the files? If you extract the files I didn't think you got a bootable CD afterwards, which would display the issues you describe. From the doc:> After downloading the ".ISO" file to your desktop, in WXP, make sure your file explorer settings allow you to see file extensions, so that you can verify that the file has an ".ISO" extension (if not, rename the last 3 letters of the file to "ISO"). For making a CD image, DO NOT try to "extract" any of the files contained within the .ISO image. For more detail on burning the ISO to CD read [Burning ISO Howto](http://www.ubuntulinux.org/wiki/BurningIsoHowto)

---

