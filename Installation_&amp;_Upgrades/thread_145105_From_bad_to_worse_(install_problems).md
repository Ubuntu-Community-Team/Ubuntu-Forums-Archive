---
title: "From bad to worse (install problems)"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by Panhead Bill on 2006-03-15
Initial problem:  Install stopped at 12% "e2fsprogs-udeb"

Burned new iso copies at lowest speed, now I get two lines of install, and what appears to be an error code.

loading / install / vmlinuz
loading / install / initrd.gz
isolinux: Disk error 80, AX=42BA, drive 9F

Asus MB K7V,  750 Mhz Athelon CPU, 384 Meg of ram, Plextor DVD R/W, Main drive is 40 gig, Rocket raid card with 3 - 120 gig seagate drives configures for stripping.

I'm tempted to disconnect  all nonessential items and reformat the 40 gig drive just to see if I can get back to the earlier problem.

Any suggestions?

---

### Post by Sef on 2006-03-15
Other possibilities:

1) Bad batch of CDs (if you're using the same batch.)

        Try another CD from a different batch.

2) Problem with the download (if your downloading from one particular site)

      Try a different site.

---

### Post by Panhead Bill on 2006-03-15
I need to be convinced that a cd batch would work for music, data (on several PC's) and as the live Ubuntu disc, and then be "bad" for the install.

I used a different mirror for the second download.

Since the original post, I reformatted the primary drive (install still fails with the "isolinux:" error).

I replaced the 40 gig drive with a 10 gig drive pulled from a Windows pc whenI upgraded to larger drives; still the "Isolinux:" error code.

Can anyone shed light on this error code?

---

### Post by Sef on 2006-03-15
Did you md5sum your download?

---

### Post by Panhead Bill on 2006-03-15
That would imply that I know what it is, where to find it, and how to use it.

Give me a hint?

---

### Post by Panhead Bill on 2006-03-16
Okay, I searched and found md5sum (for windows) and checked the downloaded file AND the CD I recorded at the lowest speed my burner would run (8X); both copies match the source checksum.

I'll try striping down the system if I can get back to the original error: "e2fsprogs-udeb"


Any suggestions of what the new error code is?

loading / install / vmlinuz
loading / install / initrd.gz
isolinux: Disk error 80, AX=42BA, drive 9F
:confused:

---

### Post by Bartender on 2006-03-17
Panhead - 
This is a bit off-subject - you mentioned checking not just your download, but also the finished CD with an md5 utility.  Could you please explain that to me?  I've been looking into Windows-based md5 programs.  It's a relatively simple task to check the download, but the final CD has been a different story because it doesn't look the same as the original downloaded .iso file.  If you have the time, I'd sure appreciate a quick explanation of how you did that.  PM me if you want ...
Thanks!

---

### Post by WaterCottage on 2006-03-17
I got a similar error code when attempting to install a purchased CD of VectorLinux on a IBM Thinkpad A21E laptop.
 Mine was: isolinux disk error 81,AX=422A,drive 9F
I tried the CD on a desktop PC and the install instantly started fine,so it wasn't the CD:-k 

 I've burned a Damn Small Linux liveCD and that works ok in the Thinkpad and I can also read the documents on the Vector CD with the same Thinkpad's CDrom(Win2000 still on it for the moment),so I don't know why it wouldn't accept the install originally,but it sounds like it has something to do with the drive itself and not the CD's.:confused: 

Jay


Any suggestions of what the new error code is?

loading / install / vmlinuz
loading / install / initrd.gz
isolinux: Disk error 80, AX=42BA, drive 9F
:confused:[/QUOTE]

---

### Post by Panhead Bill on 2006-03-20
Update:  e2fsprogs-udeb problem:  The plextor DVD R/W would not read that package, so I pulled out an old (1995) quad speed CD-ROM.  Problem 1 solved.

Problem 2 vanished when I rebooted "expert".

A new problem arose when the install came to partitioning the master drive, the drive wasn't visible.  Good thing Compusa is running a $9.99 (after rebate) sale on 80 gig drives.

Next the install would error out at different places each time I tried it.  I reformatted the drive and the install would go farther, but still hang.  Solution: Memtest found that one of my ram modules was flakey.  

Yanked the bad module and the install got as far as "downloading other modules", I bypassed it and went to "set time" all went well until the reboot, where it hung at "installing packages", "preparing for installation . . .", 0%.

Any ideas?

---

### Post by Bartender on 2006-03-20
How come you bypassed the "downloading other modules" part & how much RAM are you down to now?

---

### Post by Panhead Bill on 2006-03-21
256meg of ram. 

 I had to bypass the Downloading other packages (in expert) otherwise it would error 2/3rds of the way through and then hang at 0% on restart.  By going to expert install, it allowed me to completely bypass the other packages until after the reboot.  After it started to boot off of the hard drive I put the install CD in.  At thit point it started to download the other packages (and lure me into a false sense of accomplishment), but after the brown ubuntu start screen with all of the various process starting up, it goes into the BASH shell.

  I entered sudo get-apt install ubuntu-desktop, and it returned with a password request.  I entered the password, and it did nothing other than give me another BASH line. (no HD activity, no CD activity.


Update:  Memtest found a bad stick of Ram, video card was not compatible, 4th CD ROM worked to load normally.  Thanks to all.

---

