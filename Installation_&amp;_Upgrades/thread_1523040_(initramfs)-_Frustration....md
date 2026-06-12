---
title: "(initramfs)- Frustration..."
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Masmidow on 2010-07-03
Hey,

  I know that this sounds typical, but I have not found the answer I seek for my Ubuntu frustration. I am trying to install Ubuntu onto my brother's Dell Computer with:

Operating System: Windows XP Professonal v2008

It gets to the Ubuntu loading screen and then pops up a message:

[B]BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system[/B]

I downloaded the ISO onto a CD-R and I know that this disk works (or should) because it worked for another computer I have. I have considered trying alternate methods of booting up, HDD (through ISO Mounter) and USB. However, I can't find a thorough explanation on how to use these methods.

Are there any command that I can use to get around this "(initramfs)" thing?

If no, may someone please walk me through using an alternative process?

Is there something wrong with my disk drive?


Thank You!

           Mike S.

Additional Info:

Dist.: Ubuntu 10.04

---

### Post by Yarui on 2010-07-03
You get this error while trying to load the CD?  Initramfs is a piece of software that loads your file system when you boot, it's basically saying that it can't find the filesystem.  If this is happening when you try to boot to the disk I would do two things.  First verify that the ISO downloaded properly with the md5sum and if it did, reburn the CD.  If the md5sum doesn't match, then you need to redownload the ISO and then reburn it.

---

### Post by Masmidow on 2010-07-03
So, regardless I have to re-burn it? It is weird because this same CD was able to work fine on another computer. I am pretty sure that it was burned correctly the first time. Just to clarify, what is the md5sum?

---

### Post by Yarui on 2010-07-03
You don't necessarily have to burn a new cd, but there is a chance the cd didn't burn well and if it didn't then you have to.  If you reburn and it works then you will save yourself a lot of time, which will probably be worth it to risk wasting a single CD.  If it works with one PC and not another, there is always the chance that the problem is with the cd drive on the computer it's not working on.  That doesn't mean you would need to replace the drive, most likely it's an issue of compatibility.  Some disk drives don't like certain brands of disks.  Especially if the disk is colored oddly, it could cause the drive to have a hard time reading it.

md5sum is a string of letters and numbers that you can normally find with linux ISO downloads.  If you are on a linux machine you can just navigate to the folder the ISO is in and type:

```
md5sum filename.iso
```

replacing filename with the name of the iso file, of course.  It gives you a string of numbers and letters and if it matches that means the download was good.  You can find more information here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cogier on 2010-07-03
You could try an "Alternative" CD. You can down load here [http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/"). It has a different setup so might be worth a try.

---

