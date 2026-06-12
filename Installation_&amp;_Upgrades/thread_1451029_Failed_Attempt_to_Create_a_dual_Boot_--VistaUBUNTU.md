---
title: "Failed Attempt to Create a dual Boot --Vista/UBUNTU"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by words on 2010-04-09
My buddy has a computer with a problem and he’s asked me to see if I can retrieve the data documents from the computer.  The subject computer is a COMPAQ PRESARIO SR5030NX  with a Pentium 4 cpu, 3.2 GHz, 1 GB RAM, running Windows Vista Home Basic.

His goal was to create a dual boot computer – UBUNTU and Vista.  What he did was to install UBUNTU, partitioning the computer in two partitions.  The computer is now giving an error code of 21 when GRUB Loader starts up.  Is there a restore disk or some kind of utility that can undo what was done to the computer.  He has no backup disk.  

I tried Recovery Commander Ver. 3 made by Avanquest but as their website indicates it’s for XP.  They never updated it for Vista and Windows 7.  Is there a utility that can undo some of the changes that were made to the machine when UBUNTU was installed, albeit, unsuccessfully.

(1) I have an HP PC running XP professional and I was wondering if I take the hard drive out from the COMPAQ and rig it to my HP via a SATA/IDE to USB 2.0 Adapter device would I be able to see the contents of that COMPAQ computer that had Vista and now UBUNTU.

(2)What about attaching the COMPAQ internal hard drive and attaching it to my HP as a slave drive.

(3)Can the UBUNTU disk going to help?

We’re just after the data files and not software programs.  Thanks for any links or advice.

Thanks, Words

---

### Post by presence1960 on 2010-04-09
Need more info on that rig! 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by PRC09 on 2010-04-10
See the attached link for Vista Recovery Disks. I dont know if they will help tho.If Ubuntu was used to partition the drive before you gave it space to do so in windows then it may have overwritten part of windows.


[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

