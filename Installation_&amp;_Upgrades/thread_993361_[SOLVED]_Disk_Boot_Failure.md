---
title: "[SOLVED] Disk Boot Failure"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by TheKramer on 2008-11-25
Ok... so I had a thread up yesterday where I was unable to install Ubuntu because my boot disks all seemed to be faulty.

[http://ubuntuforums.org/showthread.php?t=992705](http://ubuntuforums.org/showthread.php?t=992705)

I never figured out those problems, but I completed 27% of an install before getting booted from the Install (the disk supposedly had an error on it), and I was able to run a VERY slow version Ubuntu 8.10 with the CD in.

Ok, so I found out the computer had less RAM than I thought (only 256MB).  I just put in another 512MB, so I'm at 768MB.

I decided to go ahead and try Xubuntu this time instead (even though the added RAM is probably enough to load and run Ubuntu 8.10 now).

Anyway, my new boot disk for Xubuntu 8.10 gives the error:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Note that I also get this error when I tried using a Windows CD (I thought maybe reverting back to Windows might help for whatever reason), but I can still enter the Ubuntu 8.10 boot screen using my original Ubuntu 8.10 boot disk (that has at least one error on it).

Any thoughts?

I have been trying to get some form of Ubuntu on this computer for over 3 days now, and I'm really getting frustrated.

---

### Post by Pumalite on 2008-11-25
Make sure CD is first in boot order in BIOS, Do md5sum on your iso, burn at 4x or less. Do not use CD-RW.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Download and install ImgBurn:
[http://www.imgburn.com/](http://www.imgburn.com/)
Once installed; go to Mode>ISO>Burn
Set speed to 1x.
Clean the lens in your burner.

---

### Post by TheKramer on 2008-11-25
Thanks, I had all of that covered except the burning at 4x or less.  All of my burning software went down to 10x, but no lower.  I just downloaded imgburn and will try that soon at 1x speed.

---

### Post by caljohnsmith on 2008-11-25
So you got the same "disk boot failure" when you try and boot the HDD and the Windows CD? But you can boot the Ubuntu 8.10 CD? Have you changed any of your BIOS settings recently? Maybe you should consider reflashing your BIOS, but otherwise it sounds like you might have a hardware problem. Although the RAM is probably not the most likely culprit, it is easy to check the RAM, so I would recommend doing so just to rule that out as a possible cause of the problem. When you boot the Ubuntu 8.10 CD, at the first menu is an option to "test memory"; how about trying that and let us know the results.

---

### Post by TheKramer on 2008-11-25
> **caljohnsmith said:**
> So you got the same "disk boot failure" when you try and boot the HDD and the Windows CD? But you can boot the Ubuntu 8.10 CD? Have you changed any of your BIOS settings recently? Maybe you should consider reflashing your BIOS, but otherwise it sounds like you might have a hardware problem. Although the RAM is probably not the most likely culprit, it is easy to check the RAM, so I would recommend doing so just to rule that out as a possible cause of the problem. When you boot the Ubuntu 8.10 CD, at the first menu is an option to "test memory"; how about trying that and let us know the results.

Sorry, I think I misspoke a little.

I no longer have an OS on the HDD.  I used the Ubuntu 8.10 boot disk and had it erase Windows 98 (which I didn't want anyway, that was intentional... I can't even find the disk for that anymore).

When I couldn't get it to boot from the Xubuntu 8.10 disk I created, I tried a Windows ME disk, but it gave the same error.  Now, I can get it to boot from the original Ubuntu 8.10 disk, but like I said, that was a failed install and the disk had  1 error when I ran the error check.  And if I try to install from that disk, it just loads forever and never does anything (although I can check memory, etc., from there).

I did check the memory after I added the 512MB to the original 256MB, and it came out fine.

I just checksummed my Ubuntu and Xubuntu 8.10 iso downloads and they both match.  I also downloaded that ImgBurn software, so I'm going to attempt another Ubuntu 8.10 boot disk right now at 1X speed and I'll report back.

Before I started all of this the system was running Windows 98 ok if that helps.

---

### Post by TheKramer on 2008-11-25
Alright, so I tried the new Ubuntu 8.10 disk I burned.

It also showed 1 error when I ran the disk check at boot up.

I tried to install anyway.

I got this error between steps 3 and 4:

Partman crashed
Partman failed with exit code 126.

I'm going to make an Xubuntu 8.10 boot disk at 1x speed with ImgBurn and try it... if that fails as well, I'm assuming I have a hardware problem.  Maybe the HDD itself is bad?

---

### Post by TheKramer on 2008-11-25
Ok, the Xubuntu 8.10 download passed the checksum.  

I burned it at 1x speed with ImgBurn.

It booted from the CD and I ran a check.  No errors.

I tried to install, and it eventually gave me a "Fail" for installing hardware drivers and stopped the install.

I'm trying to run it again, but if it stops in the same place with the same "Fail," what are my options?

---

### Post by TheKramer on 2008-11-26
Ok, I tried again.

Got past the hardware drivers just fine.

Then shortly after I received a LOT of lines that looked like:
SQUASHFS error: Unable to read page, block [letters/digits] size [letters/digits]
SQUASHFS error: sb_bread failed reading block [letters/digits]

I also saw something like:
BUS error: core dumped

Later I saw more of those SQUASHFS errors followed by something listed as [Fail] but it happened to fast to read.

More of those SHAWSHFS errors are piling up.

Any thoughts?

---

### Post by TheKramer on 2008-11-26
My problem isn't solves, but I don't think this is a disk boot failure anymore, so I'm opening a new thread for my new problems.  :/

Thanks for the help from everyone, though!  I'm narrowing this down, slowly but surely...

---

