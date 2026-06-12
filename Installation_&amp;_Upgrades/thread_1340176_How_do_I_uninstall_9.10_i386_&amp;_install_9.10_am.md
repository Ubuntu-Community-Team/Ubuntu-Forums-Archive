---
title: "How do I uninstall 9.10 i386 &amp; install 9.10 amd64?"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by jarednielsen on 2009-11-28
Total noob here.
I built my first PC and installed Ubuntu 9.10.  Unfortunately I installed the 32bit version and need the 64.  I made a new installation disk with the AMD64.iso but when I try to install it receive this message: 

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?  

I've searched through forums and found advice on how to do this with a Windows CD or by partitioning.  I don't have a Windows CD and don't know enough about partitioning.  How do I do this?  Any help would be greatly appreciated.

---

### Post by phillw on 2009-11-28
> **jarednielsen said:**
> Total noob here.
I built my first PC and installed Ubuntu 9.10.  Unfortunately I installed the 32bit version and need the 64.  I made a new installation disk with the AMD64.iso but when I try to install it receive this message: 

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?  

I've searched through forums and found advice on how to do this with a Windows CD or by partitioning.  I don't have a Windows CD and don't know enough about partitioning.  How do I do this?  Any help would be greatly appreciated.

1) Is it deffo a 64 bit chipset
2) How much data do you need to backup from your exisitng Ubuntu Install
3) What Size hard disk & partitions do you currently have
4) how much RAM

Regards,

Phill.

---

### Post by darkod on 2009-11-28
If you left Ubuntu to use the whole disk during the 32bit install and set up its own partitioning, you probably have one large / (root) partition and one swap partition.
Boot with the 64bit CD, select Install Ubuntu option. On step 4 when it asks where to install select manual and it will display the current partition you have.
Click on the larger one and at the bottom of the screen click on Change button. At first slected option will be Do Not Use This Partition. Change that into ext4 filesystem. Tick the format box. Select the mount point as /.
Selecting the format box will make sure it destroys the 32bit installation because it will format the partition.

Do the same for the smaller swap partition. Note that for swap there will be no option to select format because it's not used. Mount it as swap.

If you are confused at any point, just click Quit and the process will quit without any changes to your computer. Come back here and ask what is confusing you.

---

### Post by jarednielsen on 2009-11-28
1) Phenom II 965, 
2) Nothing to back up yet
3) 300GB HDD, no partitions (that I know of)
4) 4GB RAM,

---

### Post by darkod on 2009-11-28
You must have partition if you have 32bit installed even if you don't know that. :)
Don't be afraid, boot with the 64bit CD and look around. That's how you learn. If you still feel nervous about my previous post, you can always use the Use Whole Disk option and 64bit will install itself on the whole disk wiping it previously.
If again there are any errors or it doesn't let you install, report them here.

Also tell us at what point the error appears. How far does it let you go with the install process.

---

### Post by jarednielsen on 2009-11-28
> **darkod said:**
> 
Boot with the 64bit CD, select Install Ubuntu option. 

I'm unable to get to this point.  I boot with the 64bit CD, but the 32bit OS starts up and I'm presented with a package dialogue box.  I click OK and receive this message: 

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

Is there some way I can boot from the 64bit CD?

---

### Post by darkod on 2009-11-28
Hold on, booting from the CD should not allow the OS on the hdd to start at all. Are you sure about that?
Check BIOS is CD-ROM the first device in boot order.

---

### Post by phillw on 2009-11-28
>  Once again, we tried XP 64-bit, Vista 64-bit, and Windows 7 64-bit and the results are always the same. As we near 4GHz, the voltage requirements increase dramatically and the clocking ability of the processor decreases in much the same manner. This does not occur in a 32-bit operating system, which happens to be the recommendation for any sort of benchmarking activities with the Phenom II. 
  



Assuming you're not after over-clocking, do as darkod says - make it a new install - tell it to use the entire disk & give it 4gb swap - should run sweet.

If you think you are having an issue with the install disk, [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) is where to get it from  and [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  is how to chek the image and cd

Regards,

phill.

---

### Post by jarednielsen on 2009-11-28
Think I got it!  Many thanks!  It was the BIOS setting.  Had the HDD as the 1st boot.  Install is currently running.  I have to run out of the house for a job interview.  But you can see where my priorities lie.  Thanks again!

---

### Post by phillw on 2009-11-28
> **jarednielsen said:**
> Think I got it!  Many thanks!  It was the BIOS setting.  Had the HDD as the 1st boot.  Install is currently running.  I have to run out of the house for a job interview.  But you can see where my priorities lie.  Thanks again!

Good luck on the Job interview - we look forward to success in both your job interview and your Ubuntu install :D

Regards,

Phill.

---

