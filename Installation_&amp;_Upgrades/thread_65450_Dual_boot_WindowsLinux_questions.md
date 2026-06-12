---
title: "Dual boot Windows/Linux questions"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by 68Firebird on 2005-09-14
I am currently downloading Ubuntu 5.04 (Hoary Hedgehog) Install/live DVD.

I am currently running windows xp pro. I know nothing about linux but am going to give it a shot. I would like to dual-boot into either windows or Ubuntu. I am told I can keep my existing install of window xp and make a partition for the linux installation.

I am a noob to dual-booting. Any pointers on what to use to make a partition for Ubuntu? I have only 1 80gig hard drive. Any tips on how to go about this would be a great help.

---

### Post by Herman on 2005-09-14
Hi, I'm just another newbie who's done it a few times; (make sure you back-up first).Defrag first too (recommended). Check available disk space. I always just use the partitioner that's already on the install CD, I just put in the CD, restart, press 'ENTER' for the default install, then answer a few simple questions.
 Soon you will be offered the choice of 'erase entire hard disk' or 'manually edit partition table'. Choose 'manually edit partition table', for the disk partitioner. I then shrink my fat32 or ntfs partition to 70GB (the amount to shrink is up to you), and this leaves 10GB FREE SPACE to do something with, (install Ubuntu). Next I select 'automatically partition the FREE SPACE'. After that you can expect a few more simple questions and then the GRUB boot loader will be offered to you, (for loading either Windows or Ubuntu each time your computer starts) . After that it will ask you to remove the CD. It will reboot, and sit there with white type scrolling on a black screen for a while, then give you a login screen to log in to your new system. (Remember the NumLock if you had numbers in your password.)
  Well, that's what works for me, anyway, Good luck!

---

### Post by 68Firebird on 2005-09-14
I seem to be having a problem shrinking the existing partion I have.

When I get to this part,

"Select Partition to modify its Settings

SCSI1 (0,0,0) (sda)-80.0GB ATASt380013A5
#1 Primary 80.0GB ntfs
Pri/log         8.2MB  free space"

I then select the 80.0GB to modify its settings. Then after a 10min wait I get a screen to resize the partition. 1st time I entered 30%, because there was a tip that it would partition 30% of the free space. Well that did not work because after a long wait I ended up back at the screen "Select Partition to modify is Settings".

So I tried it again. After about 15 or 20 minutes I get to the screen to resize the 80.0GB partition. This time I enter 10GB for a new partition. Well that did not work either. After a long wait I ended back at the beginning again to "Select Partition to modify its Settings".

Any Ideas what I am doing wrong?? I would like to get this thing going but I keep hitting a brick wall trying to get this to work.

---

### Post by elky10 on 2005-09-14
Try what I did: In Windows, go to Control Panel -> Administrative Tools -> Computer Management -> Disk Management, and change your partition there.  I had the same problem as you, and it worked for me.  After you do that, when you go to install linux again, there will be an extra option, something along the lines of "Use largest continuous free space;" select that.

---

### Post by 68Firebird on 2005-09-14
Boy this is getting frustrating. I tried  your suggestion. In Disk Management I can find no options to add a partition. I read all the help topics I could find. There was one help topic that said to right click on the drive you want to add a partition and click on "add partition to allocated free space". But I saw no such option when right clicking on the only partition listed, by 80gig partition. I am running windows XP pro with sp2.
This is getting very frustrating. About to give up. I put aside an entire day to get this going and I have gotten nowhere and the day is almost over.

Any step by step instructions for shrinking my existing partition and then adding another?? So I can get this Ubuntu installed??

---

### Post by wjp.reg on 2005-09-14
Once you've shrunk the winxp partition and created free space you are ready to proceed with a linux install.

Ubuntu will give you the option of rewriting the entire disk or just using the free space.

Grub boot loader will be installed and set up with WinXP and Ubuntu as boot options.

Good Luck!

---

### Post by 68Firebird on 2005-09-14
[QUOTE=wjp.reg]Once you've shrunk the winxp partition and created free space you are ready to proceed with a linux install.

Ubuntu will give you the option of rewriting the entire disk or just using the free space.

Grub boot loader will be installed and set up with WinXP and Ubuntu as boot options.

Good Luck![/QUOTE]


Thats my problem I am hitting a brick wall trying to shrink the winxp partition and create free space. The HD is 48 free. But HOW do I shrink it???

---

### Post by wjp.reg on 2005-09-14
The easiest and safest way I have found to change partition sizes is to use **Acronis Disk Manager** for windows.

Get the free trial version here [http://www.acronis.com/homecomputing/](http://www.acronis.com/homecomputing/)

Once you've shrunk windows (but don't create another partition out of it), boot from your linux CD and install to the free space.

I have found acronis very reliable  :smile:

---

### Post by 68Firebird on 2005-09-14
I was able to borrow a copy of partition magic from a friend. I was able then to resize my windows partition and then install Ubuntu. Success, yay,  :) .

Now I have to learn how to find my way around this new os. I feel like a fish out of water at the moment. But at least I got it installed and the dual boot thing working.

---

### Post by Herman on 2005-09-15
Sorry I had to leave for a while and missed the chance to help. I'm glad you got your install done in the end. 
 
   Well here's a link I didn't get a chance to send in time, for an excellent presentation someone made illustrating the use of the Ubuntu disk partitioner. [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
It might be helpful to others in the future who might read this.

---

