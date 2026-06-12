---
title: "Want to reformat drives after failing 9.10 installation, and then reinstall"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by WhiteHorse007 on 2009-11-14
Hi all!

I have upgraded to 9.10 lately, and a couple of days later I could not start up, got file system errors... 

I must say that after the upgrade and getting the file system errors, I downloaded and used USB CD to reinstall the whole 9.10. But I could not really boot from the new installation: I get "GRUB loading" error: no such disk, then get the prompt "grub rescue>"... 

If I use the Live CD, then I can get to have a look at my drives. I see even my stuff that I had created under 9.04. Was able to copy that onto a flash drive.

I spent already a few hours unsuccessfully, so I just want to wipe out both drives, format them, and reinstall ubuntu 9.10.

How can I do this?

---

### Post by darkod on 2009-11-14
Live CD is best option. It doesn't mount hard drives and it has Gparted tool so you can use it on the drives. No need to reformat right now, just delete all partitions, if that's what you want.
Then create partitions for your new installation and format them at that point. Since you obviously know how to install you shouldn't have any problems.
If you really want to reformat I think Gparted offers the option too, but haven't used it without creating partitions myself.

---

### Post by WhiteHorse007 on 2009-11-14
Do you mean just starting up with the Live CD, then "Try Ubuntu..."; or "Install ubuntu..." and do some operation in the installation process?

Thanks!

---

### Post by darkod on 2009-11-14
Starting with live CD Try Ubuntu option. Usually called short just live cd. Because ubuntu is running from the cd it allows gparted to make changes to the drives. Do the changs you want/plan.
Then boot with the cd again, select Install Ubuntu and off you go. :)

---

### Post by WhiteHorse007 on 2009-11-14
Thanks for the clarification Darkod. Tell me, do you know if the normal installation will format both drives with best file extensions and partitioning or do I have to make them up? I'm asking because I'm null in that area ! 

Thanks.

---

### Post by darkod on 2009-11-14
It will offer to do everything itself but I prefer manual control. And I have never tried with two drives so not sure about the second one.

Basically, you need:
1. / (root), main partition, like C: in windows, filesystem ext4, size as much as you want since you have 2 drives, minimum 15GB if you have the space
2. swap, just called swap area, filesystem swap, does not have mount point, mine is 2GB size, it can be up to 4-5GB if you have spare space but no need more than that

Only those are essential. I also have:
3. /home, filesystem ext4, mounted as /home obviously, this keeps your documents, personal settings, etc. People prefer to have it separate because you can install again in the same / and just mount (use) the old /home which keeps your files and settings.
If you don't create it then a folder called home will just be created in / (root), so /home will also exist. But formating / destroys it too.

There are other additional options but you really only need these for a start. If you have 2 drives and plenty of space it is only up to you what you want to do.

Basically mine are:
/ 15GB
swap 2GB
/home 10GB

But I also have 141GB data partition formatted as ntfs which ubuntu can share with my win7 because I have dual boot with one drive. Linux can read ntfs but windows can not linux files (not by default) so if you want accessible by both, make it ntfs.

---

### Post by WhiteHorse007 on 2009-11-14
Sorry Darkod! I launched the installer before your last reply and let the installer erase all my sda drive and partition automatically. That is ok Ubuntu is now launching properly. Thanks to your help for cleaning up my mess!!!  :D

---

