---
title: "New Install on Used Drive Failure"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by gbrowning on 2010-09-28
Corei7, 6 gig ddr3, Asus x58 sli,  32gig ssd, 750 gig SATA

Wiped Windows 7 off hard drive and let Ubuntu decide how to reconfigure. Install hangs at "checking DMI pool"  Gave it about five minutes to resolve.  Tried several times
With BIOS setting to boot from CD and without DC in tray it will hang at the point where it checks for a bootable CD

Been running Win7 32 bit version. Lucid off CD runs fine, Attempted install of Lucid dual boot.  Would not Dual Boot,  did a poor job of reinstall and ended up with an extra copy of Lucid on the Hard drive.   Rebooted off CD (downloaded iso) and wiped the hard drive by deleting all partitions then let the installation program decide where to partition.

My suspicion is a bad or protected boot sector left over from the Windows install that Ubuntu is not correcting.   Do not know how to fix.

Help is appreciated:P

---

### Post by Rubi1200 on 2010-09-28
Was there a RAID setup previously on the drive? Sometimes metadata left over from a RAID install can cause issues, but I would also try burning the image again at the lowest possible speed and do a MD5SUM on it before starting.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

From the LiveCD:
> sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending on the disk name)

If that asks you to remove raid settings, that was the problem. Remove them and it should be fine.
courtesy of forum member darkod

---

### Post by gbrowning on 2010-09-28
When Windows was first configured there was a mirrored drive.  Never used it that way and went back to a single drive. You may have found the problem.  I will give your suggestion a try.  If that fails I am going to boot to a partition manager and format the drive from there, then try to install again.

---

### Post by ronparent on 2010-09-28
If data is written to the meta data setion no amount of reformatting will correct. Best follow Rubi1200's advice first!

---

### Post by gbrowning on 2010-09-29
Still failing.
Used dmraid command with the result no raid drive found.
Booted to Partition Wizard and reformatted drive to Fat32 then attempted an install with the same results.
   I think ronparent is correct.   The numbers reported for partition size seem too small.  There is about a gig missing.  I cannot see the hidden portion with either the Ubuntu install disk nor the Partition Wizard.
   I attempted to install Chameleon Bootloader as solution and the result is the same.  Something is in the boot sector and I have not been able to access it.
  
   As of now I can write to the formatted disk but I cannot boot from it.
 
   How to wipe this disk completely and remove the metadata?

---

### Post by mörgæs on 2010-09-29
Killdisk is a good way to erase a drive completely

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by gbrowning on 2010-09-29
Morgas,  Will Killdisk rewrite the MBR?    I had thought of using fdisk /mbr but I do not know enough about what other information might be in the MBR which controls an SSD Drive

---

### Post by ronparent on 2010-09-29
If you still have a problem, it is not with the MBR but with the raid meta data section of the disk which is at the end. The commands Rubi1200 gave you preciously should wipe that out!

---

### Post by mörgæs on 2010-09-29
> **gbrowning said:**
> Morgas,  Will Killdisk rewrite the MBR?    I had thought of using fdisk /mbr but I do not know enough about what other information might be in the MBR which controls an SSD Drive

Yes, Killdisk wipes everything.
[http://www.killdisk.com/erasedata_win.htm](http://www.killdisk.com/erasedata_win.htm)

---

### Post by Rubi1200 on 2010-09-29
Please post the results of the bootscript linked at the bottom of my post.

Thanks.

---

### Post by gbrowning on 2010-09-30
Here is the process planned for this evening when I can get back to my computer (about 12 hours from now)
    download and run bootscript, 
    the disk manufacturer forums recommend programs similar to Killdisk to solve bootstrap problems So I will  attempt this.
    Run bootscript again
    Attempt an install
    If success, drink a beer, if no success run bootscript once more and scratch my head.

---

### Post by gbrowning on 2010-09-30
Unbuntu 10.04 LTS is now booting off the hard drive.
The results of bootscript made the problem obvious and I apologize for not having the bootscript results file.  It was wiped out in my irrational exuberance.
     The physical configuration of the drives was with a 759 gig HD plugged into SATA port 1 and the SSD plugged into SATA port 2. (the cables routed better that way)Ubuntu named the drives sda and sdb respectively.  Ubuntu was instructed to install itself on the SSD drive (sdb) but GRUB installed itself on sda and was searching for a bootable object on that same drive.  I had instructed the BIOS to boot off sdb.
    The easiest solution was to plug the SSD into SATA port 1 which turned it into sda.
     Reinstall worked perfectly and I am posting off the repaired machine.
     Thank you ronparent, morgas and Rubi

---

### Post by Rubi1200 on 2010-10-01
You are more than welcome :)

Glad you got it sorted out; enjoy!

---

