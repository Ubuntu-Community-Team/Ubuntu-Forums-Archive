---
title: "[SOLVED] Error loading OS"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by volkswagner on 2007-12-08
I have tried both mythbuntu 7.10 and ubuntu 7.10 amd_64 versions.

Both return the same error

This is my only amd64 machine so I was only able to verify the check sum on the iso which was ok.  It will load i386 versions fine so it is not a drive problem.  I looked at the both cd's and neither have the .exe file as all my other ubuntu cds have.  I will try to burn the cd on my windows machine and see if it varies 

I tried to trick the system booted i386 cd, at boot screen changed the cd back to amd_64 version and selected install, got I/O error

---

### Post by Pumalite on 2007-12-08
Post your specs. With the right computer you can install 64 bit and 32 bit, Live CD or Alternate CD

---

### Post by volkswagner on 2007-12-08
Firstly I was wrong about the ubuntu desktop amd-64, the exe is there and boots normally.

System is new build gigabyte [LIST]
[*]MOBO- GA-MA69GM-S2H
[*]CPU- AMD Athlon X2 BE-2400
[*]RAM- G.SKILL 2GB (4 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
[*]DVD-SOME OLD SONY DVD WRITER
[/LIST]

I tried downloading ISO in win machine and burning, burn failed not sure why, still looking for the log file.  I also extracted the original iso on my ubuntu laptop and still do not see the .exe so this is why it wont boot

Need to find a new source for the iso, my torrent rejected my last attempt.  still searching

---

### Post by Pumalite on 2007-12-08
What OS do you have running at the moment?

---

### Post by volkswagner on 2007-12-08
no os yet was going to be dedicated master backend/frontend mythbuntu

---

### Post by volkswagner on 2007-12-08
I don't understand how it passed md5sum on the iso when it seems to be missing a few folders, ie: no bin, .exe, boot comand, images, etc

---

### Post by Pumalite on 2007-12-08
With your hardware you can install anything. Make sure you have a good iso, do md5sum, etc; clean lens in your burner, try CD's in different computers, check cables, connections, get in BIOS and double check that everything is configured right.

---

### Post by volkswagner on 2007-12-08
Wouldn't the amd64 be best for my system?  Can anyone confirm missing boot and .exe files from mythbuntu-amd64 iso?

see here  [http://ubuntuforums.org/showthread.php?t=634993]("http://ubuntuforums.org/showthread.php?t=634993")

if there is no benefit to the amd64 version I will try the i386

---

### Post by volkswagner on 2007-12-08
Well not much faith in the md5sum.  I burned a disk from the torrent download rather than the direct download and now have a bootable cd.  The iso is a tad larger indicating some missing files.  I don't understand where the md5sum gets its results if they all show good.

---

### Post by Pumalite on 2007-12-08
Glad you got it working. Md5sums are vital and never lie.

---

