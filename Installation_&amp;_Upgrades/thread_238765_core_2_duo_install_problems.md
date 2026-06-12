---
title: "core 2 duo install problems"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by McVities on 2006-08-18
I wonder if anyone can help me out. I've just bought a new computer   and can't seem to install ubuntu - "the install hangs at uncompressing linux ok, booting kernel"

My specs are:
Mobo: Gigabyte GA-965P-DS4
cpu: core 2 duo e6300
GPU: 7900gt

If anyone has any advice then please let me know as I'd really like to go back to linux (had fedora core on old machine). Tried installing ubuntu using my disk on a friends pc and it worked fine.

Thanks in advance!

---

### Post by wjp.reg on 2006-08-18
Is this the Live CD or Alternate Install CD?  Would be nice to know if the Live one will boot from CD.

just a thought

---

### Post by McVities on 2006-08-18
It's the live one, I was trying to boot from the CD

---

### Post by Lord Erik on 2006-08-19
I've had similar problems.

Try using the text menu installation from the alternate CD.  If that fails search these forums for "mounting root file system" and "no common cd drive found" and see if the symptoms there match what you have.

You might be unlucky enough to have the problem other are having.  There are a lot of workarounds listed in several threads (none have worked for me yet).

---

### Post by taliosfalcon on 2006-08-19
I'm having the same problem however with a gigabyte ds3 mobo, I believe it may be related to this [http://www.fedoraforum.org/forum/showthread.php?t=120571](http://www.fedoraforum.org/forum/showthread.php?t=120571) 

which apparently says current linux kernels have problems with the ICH8 Chipset which the ds3 and ds4 both use. I've set AHCI Mode in my BIOS and tried adding "all-generic-ide" to the boot options with f6 (not sure if i did it right) to no avail. The alternate install CD also does not work and it appears to be different from the problems in other threads as at least in my experience no matter how long it sits no error message comes up (i've also tried all the fixes listed in those other threads to no avail)

---

### Post by jinx099 on 2006-09-04
I'm having the same problems with my DS3.  I've even used a SATA adapter on my CD drive, and it boots fine, but same problems trying to load the live cd or install from the alternate cd.

So have you guys found a workaround for ubuntu yet?  I've tried the "all-generic-ide" thing but it didnt help.  Where is the AHCI option in the BIOS?  I have the DS3 F4 BIOS (most recent... I think).

---

### Post by seaQuest_AMD on 2006-09-04
I too am also having troubles installing with a Core 2 Duo and intel Q965 chipset.

---

### Post by element0 on 2006-09-04
Hi all! Its my first time posting.
I am having the exact same problem with the the 6.06 release I have:
-GA-965P-DS3 (F4 latest official bios)
-E6400
-7900 GTOC
With the 5.10 release, I get the "no common cdrom drivers found" error on both the live cd as well as the install
FedoraCore4 is giving me the same problems as above if that matters.
I am searching the forum for the "no common cdrom drivers found" to find what I can.

PS:
I will be double booting with Windows XP pro. I have left 13GB unpartitoned, Is that okay to just let linux install on the left over space to sucessfully dual boot?

---

### Post by element0 on 2006-09-05
Well, I couldnt find anything in the forums. But I did get Ubuntu 5.10 to install by using my IDE-USB interface device as a temporary  measure. to use a cdrw.
But during the installation Xserver (or some thing like that) didnt install correctly, so I dont have any graphic interface, its just like DOS. Should I just reinstall? This is pretty much my first time installing linux for my personal use (I installed it twice before just to see how it was) because I will need it for my college course.

---

### Post by jinx099 on 2006-09-05
> **element0 said:**
> Well, I couldnt find anything in the forums. But I did get Ubuntu 5.10 to install by using my IDE-USB interface device as a temporary  measure. to use a cdrw.
But during the installation Xserver (or some thing like that) didnt install correctly, so I dont have any graphic interface, its just like DOS. Should I just reinstall? This is pretty much my first time installing linux for my personal use (I installed it twice before just to see how it was) because I will need it for my college course.
Thanks for the tip.  I want to say that I installed Ubuntu 6.06 by using an external USB-CD-rom drive.  However, when my SATA HD was plugged into the purple GSATA ports, it would hang at the partitioner.  On the regular SATA ports, no problems.

I want to add that this OS is smoking fast with the 686-smp kernel!!!  W00T!

---

