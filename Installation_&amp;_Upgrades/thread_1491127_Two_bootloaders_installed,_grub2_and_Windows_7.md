---
title: "Two bootloaders installed, grub2 and Windows 7"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by smgendler on 2010-05-23
All,

I recently installed Ubuntu 10.04 onto a drive that has the Win7 bootloader running on it.  I had hoped that grub2 would overwrite the Win7 bootloader, but it didn't work that way.  Instead the Win7 bootloader is a selection created on the grub menu, so grub comes up, I select the Win7 bootloader, and then have to select the Windows OS version I want to boot to.  Is there a way to get the 2 Win OSs on the grub menu and remove the Win7 bootloader?  There's lots of doc on making entries for /etc/grub.d/40_custom for linux partitions, but I can't figure out what the entries should be for Win XP and 7.

Thank you for your help.

---

### Post by dino99 on 2010-05-23
removing w7 bootloader might not be the good solution: if grub fail you still have it.
This problem has been discussed so many times here in the latest 30 days (google about)

---

### Post by darkod on 2010-05-23
> **smgendler said:**
> All,

I recently installed Ubuntu 10.04 onto a drive that has the Win7 bootloader running on it.  I had hoped that grub2 would overwrite the Win7 bootloader, but it didn't work that way.  Instead the Win7 bootloader is a selection created on the grub menu, so grub comes up, I select the Win7 bootloader, and then have to select the Windows OS version I want to boot to.  Is there a way to get the 2 Win OSs on the grub menu and remove the Win7 bootloader?  There's lots of doc on making entries for /etc/grub.d/40_custom for linux partitions, but I can't figure out what the entries should be for Win XP and 7.

Thank you for your help.

Grub2 is indeed on your MBR as you expected. The reason you are still getting a windows boot choice as second stage is because you have two windows versions. When installing more than one version, windows combines the boot files of both versions together. Ubuntu has nothing to do with it.

And since your boot files are already combined, grub2 can't split them up and make separate entries in the menu. It has to call the combined windows menu.

In theory, you could try splitting the files, or installing new boot files for windows to each partition of the two versions, and then grub2 should create separate entries.

But if thing go wrong with messing with the boot files, you will have to save your windows.

---

### Post by mikewhatever on 2010-05-23
Grub doesn't actually boot Windows, no matter what you put in the 40_custom, it simply redirects the process to the Windows bootloader, which, in turn, boots Windows.

---

### Post by smgendler on 2010-05-23
I see that's what Win7 did.  If I was willing to reinstall all 3 OSs (WinXP, Win7 and Ubu 10.04), is there a way to install Win7 where the merging together of XP and 7 under their bootloader doesn't happen?  The order of the current install was WinXP, Ubu 10.04, Win7.

It just seems nuts to me to have to go through 2 boot menus because Microsoft continues to not recognize Linux as a viable option.  It almost seems predatory (Microsoft?! Never! NOT!) to require users to use their boot software.

---

### Post by darkod on 2010-05-23
> **smgendler said:**
> I see that's what Win7 did.  If I was willing to reinstall all 3 OSs (WinXP, Win7 and Ubu 10.04), is there a way to install Win7 where the merging together of XP and 7 under their bootloader doesn't happen?  The order of the current install was WinXP, Ubu 10.04, Win7.

It just seems nuts to me to have to go through 2 boot menus because Microsoft continues to not recognize Linux as a viable option.  It almost seems predatory (Microsoft?! Never! NOT!) to require users to use their boot software.

I'm not sure how easy/difficult it is to do it right now. Otherwise, for a new install you will need to:

1. Install first win version.
2. Boot the ubuntu cd in live mode and use Gparted to create second ntfs partition with the size you want for the second win version. Then turn off the boot flag on the first partition, and turn it on on the second.
3. Install the second win version but because the boot flag will be on its own partition now, the boot files will remain on its own partition and will not be combined with ver1.

I agree, it makes no sense to go trough two stages for booting.

You could run the boot info script to see what is where, and depending on the results, if for example win7 has combined the boot files on its partition:

1. Set the boot flag on the XP partition. Use the XP cd to install boot files which should go on its own partition because it has the boot flag.
2. Once you can see XP booting directly from grub2, remove the reference for XP in the win7 bootloader.

However I've never tried this. It sounds logical to me, but I might be wrong. :)

---

### Post by oldfred on 2010-05-23
If you want to reinstall this is how. You may be able to move the boot flag and repair the second install if it is on a primary partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by smgendler on 2010-05-24
I took a look at the thread [http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

an exerpt:
> **mk4umha said:**
> OK, I got XP, Win7 and Ubuntu to show up on the Grub2 Menu.

First, I had to make Three Primary Paritions, one for XP one for Win7, One for storage so both XP and Win7. The rest of the drive is extended partition. Inside extended partition, I had for swap, "/" "/home" etc.

I install XP on to the first primary partition, after it's finished, boot into the Live CD and remove that parition Boot Flag.

Then i installed Win7, Then Ubuntu. After that Ubuntu picked up all 3 OS's and I can select which one I want to boot to with no issues.

I don't know how you guys find this stuff.  Honest I looked for hours trying to find a thread that helped me.  The one above is marked "solved."  I'm gonna give it a try.  If it works for me, I'll post back here and mark this thread solved, too.

Thank you all for your help.

---

