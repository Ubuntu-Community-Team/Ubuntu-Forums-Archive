---
title: "Ubuntu 9.10 Live CD Won't Boot"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by gcs1984 on 2010-02-01
Years ago, when I first tried Ubuntu, I think it was version 7.(something), Ubuntu Live CDs always worked fine. But then, after there were a few kernel updates, they just stopped working. Sometimes changing the drive mode from IDE to RAID did the trick, sometimes it didn't. I've been moving back and forth from Ubuntu to Windows for the past 2-3 years. I've decided to install Ubuntu again today.

I downloaded the ISO file from the Ubuntu website, and burnt it onto a CD using PowerISO 4.2, at the maximum burn speed. I changed the drive mode from IDE to RAID, and tried to boot the CD. I get as far as the main menu, at which I choose the option "Try Ubuntu without changing your system". At this point, a white pulsing Ubuntu logo appears, and nothing else happens. I hear the CD drive spin down, to a stop. Then, it clicks five times (as if the computer is looking for something on the disk, but can't find it), and spins down again. It continues to do this indefinitely.

I tried setting the computer to IDE mode, no change.

I tried burning another disk, this time with a burn speed of 4x, no change.

From the main menu of the Live CD, I checked the disk, and it found two errors.

My computer is a Dell Inspiron 530. I am not computer savvy enough to say what parts such as motherboard or whatever are inside the computer, but I can say that they are all stock parts, I haven't changed or altered any of them.

What am I doing wrong? Why isn't Ubuntu working on my system? Any help is greatly appreciated!

Thanks for reading.

**Edit:** Also, when I burned the disk with PowerISO, I ticked off an option to check the disk when it was finished. An error came up, I think it said something like "Invalid Function".

---

### Post by Goldcoin on 2010-02-01
Well I'm no expert, but here's what I did that worked for me. Before burning the disk I checked the .iso file with md5sum and everything matched up. I then downloaded and used [infra recorder]("http://infrarecorder.org/") and kept all the settings on default. Restarted. Popped the disk in and booted up. Bingo. The Ubuntu logo comes up and a few minutes later I'm running the OS off the Live CD.

---

### Post by dabl on 2010-02-01
> **gcs1984 said:**
> 

 burnt it onto a CD using PowerISO 4.2, at the maximum burn speed. 



That's probably your problem.  Verify the md5sum on the ISO file, then try burning it at 4x or no faster than 8x.

---

### Post by gcs1984 on 2010-02-07
Hey, sorry for the delay in posting this reply.

I've since successfully installed Ubuntu on my computer. I didn't need to change the drive mode to RAID, or anything, it simply worked.

I did a md5checksum of the Ubuntu ISO and it was fine. I then installed InfraRecorder, and used that to burn the disk image, with the write speed set on the lowest it would allow me, 16x. When I popped the disk into my computer and began the install process, it went along without problems. I guess the issue was that PowerISO was not writing the disk properly or something.

Thanks so much for your help! My problem is solved.

---

