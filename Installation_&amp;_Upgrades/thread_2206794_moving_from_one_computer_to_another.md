---
title: "moving from one computer to another"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by mmcl26554 on 2014-02-20
Hp is giving me a new notebook computer to replace the lemon I now have.   The old one has win 7 (64) and the new one will have win 8.1.1.   This may have been addressed in this forum but I couldn't find it.   Anyway, I want to move the Ubuntu 12.04 install to the win 8.1 new computer.   What I thought I would do is using Acronis (which works with linux) make a backup of the 2 linux partitions (main and swap) and install them on the new computer.   I suppose I may need to setup the partitions, with G-Parted, on the new computer before I do the transfer.   After the transfer is complete I suppose I will have to run "Boot repair" to get the dual boot working.  I'm a beginner with Linux, but learning fast,  it has been a good stimulus for my elderly brain.   Is my thinking correct for this project or am I all wet?
Michael

---

### Post by stevephillipgreen on 2014-02-20
You might want to take a look at Timeshift.. 

> **Cross-Distribution Restore**
 You can also TimeShift across distributions. Let's say you are  currently using Xubuntu and decide to try out Linux Mint. You install  Linux Mint on your system and try it out for a week before deciding to  go back to Xubuntu. Using TimeShift you can simply restore the last  week's snapshot to get your Xubuntu system back. TimeShift will take  care of things like reinstalling the bootloader and other details. Since  installing a [[COLOR=#009900]_new_[/COLOR]]("http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html#")  linux distribution also formats your root partition you need to save  your snapshots on a separate linux partition for this to work.


[http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html](http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html)

---

### Post by mmcl26554 on 2014-02-20
I looked at timeshift, but it doesn't look as if it suitable to transfer the whole Ubuntu OS to another drive to dual boot with win 8.  Or did I miss something?
Michael

---

### Post by stevephillipgreen on 2014-02-20
What you do is perform a fresh install and then restore a timeshift backup you made on the old machine.

If you're using proprietary drivers for graphics or other things on your old computer, running the cloned install on another machine with different hardware would cause it not to boot into the desktop or present you with a blank screen (unless you removed them all 1st before creating the copy). That's why using something like Timeshift is a good option because you can start with a fresh install and just restore your backed up files.

---

### Post by Bucky Ball on 2014-02-20
Clonezilla, Partimage. Clonezilla will copy a whole disk, as is including MBR, directly to another disk, wiping out all on the target disk and leaving you with two identical images, one on each disk.

[http://clonezilla.org/](http://clonezilla.org/)

I used it recently to copy a full dual-boot to my new SSD, XP and Xubuntu. Worked a treat.

---

### Post by mmcl26554 on 2014-02-20
OH, I get it!   That would solve a lot of problems.   I'll study timeshift  and make the backup of Ubuntu, do a fresh install on the new computer and then run the backup.   This will work because the things timeshift won't transfer I don't have (User data such as documents, pictures and music)

---

### Post by Bucky Ball on 2014-02-20
Repeat: Clonezilla. Details in my previous post. ;)

---

### Post by mmcl26554 on 2014-02-20
I tried to install "Timeshift" into 12.04 but got the error message   ```
sudo: aptitude: command not found

```
So what do I do next?
Michael

---

### Post by mmcl26554 on 2014-02-20
The install instructions I was using were defective, I found good ones and it is installed, hooray!
Michael

---

### Post by stevephillipgreen on 2014-02-21
Glad you're making progress!

I thought i'd throw this into the pot, it's from the same author as timeshift and let's you quickly install all of your applications on another machine/fresh install.. Something to bookmark for future use perhaps?

[http://www.omgubuntu.co.uk/2014/01/reinstall-apps-on-ubuntu-fresh-install](http://www.omgubuntu.co.uk/2014/01/reinstall-apps-on-ubuntu-fresh-install)

The authors homepage for Timeshift in case you weren't able to locate it..

[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)[URL="http://ubuntuforums.org/member.php?u=504316"][B][COLOR=#C61919][B]
[/B][/COLOR][/B][COLOR=#C61919]****[/COLOR][/URL]
@bucky ball, what you're talking about will wipe out his Win 8 which I don't think is what he wants, if he clones his win 7 it probably won't even boot on the new machine and he won't be able to activate it because the code is already in use on another machine.

---

### Post by mmcl26554 on 2014-02-21
Thanks Steve, looks like just what I want.   I'll give it a shot.
Michael

---

### Post by oldfred on 2014-02-21
**Do not** use any tool that is an image copy. 
Old Windows 7 based computer probably was BIOS with MBR partitioning. New Windows 8 system will be UEFI with gpt partitioning. MBR and gpt are too different to do a partition copy. But if just copying data you should be ok, but a BIOS boot system will only boot in BIOS mode and require a lot of UUID, grub, fstab setting changes. Often as much work as a new install.

Actually best to just do a new install. 
You can export list of installed apps, export any special settings from /etc, but many may not apply in new install and export /home. I would copy all data in /home to a new /home partition (not image copy but cp -a or rsync) and then install new version also mounting the new (old copy) /home.

---

### Post by mmcl26554 on 2014-02-21
Hi Old Fred!
I checked and the Win7 notebook is indeed Bios.   So, I will do a fresh install.  I have been experimenting with Trusty on another computer (this is the one where all versions of Linux take 3 to 3-1/2 minutes to boot, never did find an answer to that), anyway once up it works fine.   I like the desktop on 12.04 better (Unity?) so maybe I'll wait until that is added to the release of Trusty and install it and then transfer the data and programs I did with whatever program I chose to do it with.
Michael

---

### Post by oldfred on 2014-02-21
Trusty should have Unity as default.
I do not use Unity as my old desktop has a 4:3 monitor and using the old menus (fallback or flashback) work beter as they are at top & bottom of screen. Plus oldfred does not change easily. :)
And my laptop which is wider, is just too old to run Unity well. It barely runs with Unity and with fallback it runs reasonably well. Plus then I have same desktop on both systems.

Now older but shows different desktops.
 Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)

---

### Post by mmcl26554 on 2014-02-21
The release I am using is the "Alpha" and doesn't come with Unity but it is supposed to be added the end of March.   It has Gnome, and I added KDE for me each has it's good points and bad but I guess I'm just used to Unity.
Michael

---

### Post by stevephillipgreen on 2014-02-21
> **mmcl26554 said:**
> The release I am using is the "Alpha" and doesn't come with Unity but it is supposed to be added the end of March.   It has Gnome, and I added KDE for me each has it's good points and bad but I guess I'm just used to Unity. Michael  I actually did a video about making cairo dock/cairo dock session look like Unity (not exactly like it but it gets the job done) plus there's all the added goodies that come with cairo dock.  [http://www.youtube.com/watch?v=sBLWinUMB_k](http://www.youtube.com/watch?v=sBLWinUMB_k)

---

### Post by mmcl26554 on 2014-02-21
I did download it and install it, interesting!   I haven't seen your video yet but I will.   And, then play with it.
Michael
P.S.: keep the suggestions coming!

---

