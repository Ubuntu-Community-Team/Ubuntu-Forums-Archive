---
title: "Toshiba hard drive password lost because of ATA Secure Erase/hdparm"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by amirrocat2 on 2017-03-04
Hello, there. 

I'll tell you what happened: trying to completely erase/empty/format the hard disk to reinstall Ubuntu on my laptop, a Toshiba L755, I followed the instructions, as Ubuntu's 'Disks' application suggested ([https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)). I introduced the commands within the terminal and I stayed in step 4 of this previous link. However, the same application 'Disks' said that there was an error in the formatting of the hard disk because it was being used. So I decided to turn off the laptop to format the disk and reinstall Ubuntu from a pen drive where there is an ISO of our OS. But when the computer started again it's been blocked and only asks me for my password HDD/SSD, which theoretically should be the 'Eins' that the instructions at the same ATA page I've linked made me make state via terminal. But it doesn't work! Nor does any other password I have ever consciously used with my computer. 

I'm frightened because I've read and read on the Internet what can I do about it but I don't manage to succeed, mainly because the computer does not let me do anything else unless I'm able to find out the hard disk password. 

Any ideas? Many thanks in advance!

---

### Post by ajgreeny on 2017-03-04
Did you manage to boot from your pendrive to a live OS and actually attempt to reinstall your Ubuntu OS from there?

I can not fully understand what you mean by the statement
> But when the computer started again it's been blocked and only asks me for my password HDD/SSD, which theoretically should be the 'Eins' that the instructions at the same ATA page I've linked made me make state via terminal. But it doesn't work! Nor does any other password I have ever consciously used with my computer.

Can you explain where in the procedure this problem appears as if you are booting from the pendrive your hard disk should not be involved.  If, however, this is happening when you are trying to partition the hard disk ready for installation, that would make more sense, as it is at that point that the hard disk must be interrogated

From the live system you could also go to gparted and see what that shows for the hard disk.  If there is nothing on it that you must save it may be possible to format it using the live system gparted, but if you do need to keep any files on it you will have to try again to mount the partitions of the internal hard disk of your computer (if you can) and copy those needed files to another disk.

---

### Post by amirrocat2 on 2017-03-05
> **ajgreeny said:**
> Did you manage to boot from your pendrive to a live OS and actually attempt to reinstall your Ubuntu OS from there?

I wish! By now all the computer let's me do is try and write the HDD/SSD password which I don't really know. 

> **ajgreeny said:**
> Can you explain where in the procedure this problem appears as if you are booting from the pendrive your hard disk should not be involved.  If, however, this is happening when you are trying to partition the hard disk ready for installation, that would make more sense, as it is at that point that the hard disk must be interrogated

What I intended to do was to fully wipe out my hard disk, not partition it. But I think that actually none of that happened when I entered the hdparm commands on the terminal. So that's why I tried to format my hard disk booting the ISO from a USB stick. But for now I'm not able to access it as, as I said, the only think my computer let's me do, no matter how fast or how continuously I press the F8 and F12 buttons to access the BIOS or the USB stick, is to be stuck in that 'Enter the HDD/SSD password' screen. 

> **ajgreeny said:**
> From the live system you could also go to gparted and see what that shows for the hard disk.  If there is nothing on it that you must save it may be possible to format it using the live system gparted, but if you do need to keep any files on it you will have to try again to mount the partitions of the internal hard disk of your computer (if you can) and copy those needed files to another disk. 

My personal files are already copied in another disk, so that wouldn't be a problem. The question is how can I possibly access the live system gparted or format the disk with my actual situation, anyways. Maybe there is a way to find out what can possibly be the password I set for my hard disk taking a look at the commands at the link on my original message. It's absolutely certain that I messed something up while using them.

Many thanks for your answer, by the way.

---

### Post by Geoffrey_Arndt on 2017-03-05
F2 to enter BIOS and update Boot Order or Boot Sequence.     Then, after the proper setting is saved, F12 should bring up the one-time boot menu.    This should all happen prior to the system addressing the internal drives.

---

### Post by amirrocat2 on 2017-03-07
No, no, guys. It's just not possible to access any other screen but the one that asks me for my HDD/SSD password. The F2 button nor any other 'F' would work. Could you tell me, please, as you're certainly far more experienced than I am with programmation and so, how did I mess it up introducing the commands on the terminal? The hdparm ones in this [link]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase"), that is. And what's crucial here: could you give me some options on what you guess my current hard disk password would be?
Thanks.

---

