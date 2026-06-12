---
title: "Reinstallation on a new Hard Drive"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by sigma2805 on 2005-07-04
Hello Everyone,
I started using Ubuntu about a week ago and i am loving it. I recently bought a new hard drive to install ubuntu on. Basically what i want to do is delete my current installation of Ubuntu and Re-install it on my new hard drive. i figure its best to do it now before i go ahead and customize it and install all the apps i need. Basically for the installation of ubuntu i partitioned my hard drive with qtparted(great program) and went ahead with the installation. Here is my plan to re-install it. can someone look this over and make sure i'm doing this right

1. Use QTparted to delete the current ubuntu partition and resize the NTFS partition back to the size it was before the installation of ubuntu. 
2. Use QTparted to partition the new hard drive(i want to add a couple other linux distros for testing)
3. Install Ubuntu

The only thing i'm scared about is grub getting messed up somehow doing this. I need my windows partition because this is a family computer. does anyone have any tips or insight they can share with me?

---

### Post by t2kburl on 2005-07-05
looks like it will work

just take care during ubuntu installation to make sure you are putting it into the partitions you want it in (likely to be hdb1)

rewrite grub during the new install and all should be well.

also ... I would recommend booting to W$ before you install so it can adjust to the resized partition ..... it may want to take the new HD also, but just cancel the new hw wizard for it if it starts.

---

### Post by C.B. on 2005-07-05
Why not just stick the Ubuntu CD in and let install do it. You can direct it to put the OS on the new drive (presumably hdb) and have it partition, and put GRUB where it is now (presumably hda) so it will take over at boot-up. The new install will change the GRUB parameters to work with the new drive. Simple.

---

### Post by sigma2805 on 2005-07-05
Yeah, thats what i was thinking just now. I think i will install Ubuntu on the new drive and let the installation configure grub then i will go ahead and delete the installation off of hda. i'm assuming  i can delete the grub entry for the first installation right?

---

### Post by t2kburl on 2005-07-05
the new grub will replace the old automaticly

---

### Post by sigma2805 on 2005-07-05
cool thanks. i'm going to do it tonight.

---

### Post by mingus on 2005-07-05
There are a couple potential gotchas to be aware of . . .

First, double-check that the BIOS permits you to boot from the second drive.

Second, remember that grub's (hd0) is now /dev/hdb, not hda as it is now.

Third, to dual-boot XP you may need to modify the /boot/grub/menu.lst file in the XP stanza.  You stanza will probably need to look like:
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)

Finally, when overwriting the MBR it's always a good idea to have XP repair media should something go awry.  A W2K/XP install CD, or a W98/ME/DOS bootable diskette.

---

### Post by sigma2805 on 2005-07-05
just so  i can be sure, i need to check to make sure that the bios can boot from the second drive because grub will be installed on the second drive and that grub will point to the XP installation on the first drive correct?

---

### Post by mingus on 2005-07-05
[QUOTE=sigma2805]just so  i can be sure, i need to check to make sure that the bios can boot from the second drive because grub will be installed on the second drive and that grub will point to the XP installation on the first drive correct?[/QUOTE]

Yes.  It is very likely the BIOS can do this, but since you didn't mention what rig you've got, thought it should be mentioned just in case.  And some BIOS's come with an easy-to-use menu to choose the boot device (without going into setup); these users often use this menu to control the boot instead of dual-booting.  When you dual-boot (whether from grub to W$ on the other drive, or the other way around) it's important to keep the boot drive first in the BIOS sequence, whichever it may be.

---

### Post by sigma2805 on 2005-07-05
i'm pretty sure my bios doesn't allow choosing which drive to boot from. unfortunatly i am at work right now so i can't check it out. i bought the computer in i believe 2001 or 2002.

---

