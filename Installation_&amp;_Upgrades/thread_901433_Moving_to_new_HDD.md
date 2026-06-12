---
title: "Moving to new HDD"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Turrat on 2008-08-26
I've got a question about moving stuff to a new hard drive. A couple of years ago I got a WinXP Pro disk with a one-time use key free from the university I was at. I installed it and Ubuntu onto my machine, dual-booting from a single 20GB drive in three partitions (7.7 Ubuntu, 7.7 XP, the rest swap). I know from experience (college friends doing crazy overclocking tricks) that the Windows key is not valid for a repair install or anything; it was just for that one single installation use, and I can't get any more because I graduated and now have to pay my own money for Windows. 

Recently I purchased and installed a 500GB drive. I'm wanting to put my Ubuntu install on a partition of the new drive, and resize WinXP to fill up the rest of the old 20GB one. The question here is, is what I'm trying to do possible? And if so, what steps would I need to take to make sure my data is safe?

---

### Post by mellowd on 2008-08-26
In theory yes. First make a backup. (I'd image the entire 20GB disk onto the 500gb, plenty of space)

It then depends on how your disk is set up, is ubuntu on the first partition? You might be able to delete it completely, keeping the current MBR. You could then attempt to resize Windows.

This is why I said make a backup, you might need to try a few different things more than once

---

### Post by Turrat on 2008-08-26
I think Ubuntu is on the second partition - Nautilus says my Windows installation is on sda1 and my Ubuntu install is on sda2.

When I make a backup, if I mess up would I be able to restore it and have Windows still work? I really don't want to spend $100+ just for a key to do a repair install, so I'm a little on edge about it. And what's a good app to use for making a disk image?

---

### Post by mellowd on 2008-08-26
This is a free utility:

[http://selfimage.excelcia.org/](http://selfimage.excelcia.org/)


If you nuke it, you can use this utility to restore the image stored on your 500gb back to the 20gb and it'll be exactly the same as when you started.



Once the image has been made, delete the ubuntu partition and either extend your primary partition or just format the old partition to a new ntfs partition. You can then edit grub to remove any reference of ubuntu, or do a fdisk /mbr which will then point solely to your windows partition

---

### Post by mellowd on 2008-08-26
Here's another as well:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Turrat on 2008-08-26
And after that I reinstall Ubuntu onto a partition of my 500GB drive, yes? What about the apps and files I have - would I have to just install them again on the fresh Ubuntu partition or is there some way to keep them?

Also, I tried using SelfImage and it said that since the drive I'm copying the image to is Fat32 the image would cut off after 4GB? I have an HD movie on there right now so I know it supports files greater than 4GB. Yet SelfImage gives me the error still.

---

### Post by mellowd on 2008-08-26
> **Turrat said:**
> And after that I reinstall Ubuntu onto a partition of my 500GB drive, yes? What about the apps and files I have - would I have to just install them again on the fresh Ubuntu partition or is there some way to keep them?

Also, I tried using SelfImage and it said that since the drive I'm copying the image to is Fat32 the image would cut off after 4GB? I have an HD movie on there right now so I know it supports files greater than 4GB. Yet SelfImage gives me the error still.

Maximum size of a file on a fat32 partition is 4gb. convert it to NTFS until you're happy with your 20gb, as you'll format it for linux anyway. (the application might have an option to split the image, maybe not)

You can copy your /home partition to the new disk, but you'll need to install a few apps here and there

---

