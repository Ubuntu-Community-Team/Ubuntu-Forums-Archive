---
title: "Ubuntu parition got deleted..."
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by vghaisas on 2010-08-25
Dear All,

I originally had a Desktop PC running Windows XP with two drives - C:\ and D:\ , each around 75GB so total around 150Gig.

Anyway, I was suddenly interested in Ubuntu so I downloaded it, put it on a USB, booted from the USB and installed Ubuntu giving it around 25GB of space. (Which it took from D:\)

Then I felt I wanted to give Ubuntu some more space. So, using GParted, I did some nonsense that almost destroyed D:\. At the time, C:\ was unaffected, D:\ was reduced by 20GB, Ubuntu was unaffected and there was 20GB unallocated space. Then, using Windows disk management, I decided to create a &GB Logical Drive in the Unallocated space that could be shared by Ubuntu and XP. (bcoz it would be formatted in FAT32)

Anyway, after I started the creation, some error ocurred and now C:\ is same. D:\ is same, Ubuntu has dissapeared and I have 43GB unallocated (free) space.

Ubuntu has caused more bad than good (for me at least). So, I'm going to install it much, much later. But my main question is, will Windows XP still boot? And is my hard disk intact??

Help please... :( ?

---

### Post by Rubi1200 on 2010-08-25
Hi,
let's just be clear about something. 
> Ubuntu has caused more bad than good
Not true!
You are the one who has done something wrong here:
> I did some nonsense

On to the problem:

Do you have an Ubuntu CD?

If yes, boot the computer with it, making sure BIOS is set to boot from the CD drive.

Choose to try Ubuntu NOT install.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results of the bootscript so we can see what your setup is and offer solutions.

> will Windows XP still boot?
You need to tell us that.

> is my hard disk intact??
Probably, but it sounds as if you have messed the partitions up.

Post the bootscript please.

---

### Post by vghaisas on 2010-08-25
Ok, ok, maybe I messed up. Then again, all I did was to resize the D:\ partition using GParted. I don't think that qualifies as me doing something wrong...

Anyway, forgetting that. At least in my case, Ubuntu has troubled me. And though it did give me the enjoyment of speed and other worthwhile things, I feel Windows is necessary in my life.. :P

So, I have an Ubuntu USB from which I originally installed Ubuntu. Also, I am currently using the Windows XP in question. It works fine though I haven't booted the system even once since 'THE MISHAP'. Also, since Windows boots from the C:\ (I think...) and nothing is wrong with it (yet!..) shouldn't Windows XP be able to boot? P.S. I don't have the XP installation CD... :(

I don't want to risk rebooting my system because Windows is working fine right now. Im just not sure what will happen after rebooting.

Ill make my question simple. If I had a dual boot system - Ubuntu and Windows XP and I boot into XP, go to disk management and delete the Ubuntu partitions, will XP still boot? 

Thanks in advance...

---

### Post by Rubi1200 on 2010-08-25
> **newbie.who.needs.help said:**
> Ok, ok, maybe I messed up. Then again, all I did was to resize the D:\ partition using GParted. I don't think that qualifies as me doing something wrong...

Anyway, forgetting that. At least in my case, Ubuntu has troubled me. And though it did give me the enjoyment of speed and other worthwhile things, I feel Windows is necessary in my life.. :P

So, I have an Ubuntu USB from which I originally installed Ubuntu. Also, I am currently using the Windows XP in question. It works fine though I haven't booted the system even once since 'THE MISHAP'. Also, since Windows boots from the C:\ (I think...) and nothing is wrong with it (yet!..) shouldn't Windows XP be able to boot? P.S. I don't have the XP installation CD... :(

I don't want to risk rebooting my system because Windows is working fine right now. Im just not sure what will happen after rebooting.

Ill make my question simple. If I had a dual boot system - Ubuntu and Windows XP and I boot into XP, go to disk management and delete the Ubuntu partitions, will XP still boot? 

Thanks in advance...

> If I had a dual boot system - Ubuntu and Windows XP and I boot into XP, go to disk management and delete the Ubuntu partitions, will XP still boot? 
To answer the question: in theory, yes. But, there are always risks involved when doing things with drives/partitions.

The best thing to do is make a backup of all important files etc. before attempting stuff like this.

You can also use the Ubuntu CD (or USB) to change partitions as well as install the system.

Dual-booting, in my opinion, is the best option for you.

Here are some guides that will help:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have any questions, feel free to ask.

EDIT: a friendly word of caution; since you don't have a Windows installation CD, you should be very careful whatever you do. If things get really messed up, there is usually almost no chance of getting things "back to normal."

---

### Post by vghaisas on 2010-08-25
This is how my hard disk looks under disk management right now.
[IMG]http://iota-org.webs.com/Disk.bmp[/IMG]

Also, sorry to put it this way, but now I have lost any wish to reinstall Ubuntu. I don't care if any files on it are lost or if I can't use Ubuntu any more.

The only question is... If I leave my C:\ like it is and also my D:\ like it is, will XP boot? I'm actually just worried about grub. In a dual-boot system, you have to choose which OS to boot into with grub right? But now that it's no longer there, will the computer automatically boot into windows? 

P.S. The default OS was XP before..

---

### Post by Fableflame on 2010-08-25
It's quite simple to boot the Ubuntu LiveCD and use Gparted to resize your D: drive to normal size, I don't know what "nonsense" you done to mess up your partitions. After you resize D: you can boot back into XP if you want and make sure the partitions are as they should be, then you can boot the Ubuntu LiveCD again and Install Ubuntu on the remaining space on your harddrive.

---

### Post by vghaisas on 2010-08-25
Dear All,

I am not exactly worried about the size of my D:\\ . I will create a new partition using Disk Management in the free space. The only thing I am worried about is - "WILL WINDOWS XP BOOT" ? Because I think when Ubuntu installs, it also installs GRUB and when booting the system, the chioce of which OS you want to boot into is given by GRUB. So all I'm worried about is now that GRUB is deleted, will Windows boot as normal?

P.S. The main reason that I am not going into resizing is because that was what got me into all this mess in the first place!...

P.P.S Would all of you like to know precise what I did with Disk Management and GParted? Though I am hoping that you will be able to help me without it.....

---

### Post by ks07 on 2010-08-25
Hi,

First things first, backup all of your important/needed/wanted files on the C: and D: drives to something removable (e.g. a USB drive). As you've already found out, it's very easy to delete everything on a drive when partitioning. 

Now, before you start changing the partitions, we need to know how your PC is booting into XP. When you boot the computer, does it show the Grub menu? (Menu with options to boot Ubuntu, XP or memtest etc.) If it does, then you'll need to restore the windows xp mbr or you wont be able to boot at all once you have grown the D: partition to fill the entire disk. 

If it doesn't, and the computer goes straight to the XP loading screen, you should be set to grow the D: partition to include the leftover free space. Just be careful this time round ;)

---

### Post by vghaisas on 2010-08-25
Dear All,

Before, when the system was running on a dual-boot system (XP and Ubuntu), on booting, I got a Grub screen that allowed me to choose which OS I want to boot - Ubuntu, XP, memtest and so on. But now that Ubuntu partitions have gotten deleted, GRUB has gone, right? So, I don't know what's going to happen at startup.

Things to Remember:
- I am NOT going to resize any partitions now.
- I have no wish to make a dual-boot system in the near future.
- I just want to know if Windows XP will boot if I restart.
- if it is not going to boot, please tell me what I should do to       ... make it boot...

---

### Post by Grenage on 2010-08-25
Will it boot?  Probably.  Restart and find out; it's not like your data will disappear.

Worst case scenario, you boot from an XP disc and run fixboot, or boot from you Ubuntu CD and reinstall grub.

---

### Post by ks07 on 2010-08-25
> **newbie.who.needs.help said:**
> Dear All,

Before, when the system was running on a dual-boot system (XP and Ubuntu), on booting, I got a Grub screen that allowed me to choose which OS I want to boot - Ubuntu, XP, memtest and so on. But now that Ubuntu partitions have gotten deleted, GRUB has gone, right? So, I don't know what's going to happen at startup.

Things to Remember:
- I am NOT going to resize any partitions now.
- I have no wish to make a dual-boot system in the near future.
- I just want to know if Windows XP will boot if I restart.
- if it is not going to boot, please tell me what I should do to       ... make it boot...
I assume you are booted into XP on the computer now, right? If so, like mentioned previously, when you restart you will most likely be given a Grub not found error, due to the Ubuntu partition being deleted.

In any case, not being able to boot does not mean your data is gone. You can restore the boot information on the hard disk and the PC should boot straight into XP from then on.

The easiest way to fix it is to use a Windows installation CD and use the recovery console. In your case, you're going to have to fix it using the Ubuntu Live CD and using the tools as described here: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

EDIT: The only problem you'll have is installing ms-sys. It is no longer in the repos, so to install it you will have to download and compile it from source. [Download here.]("http://sourceforge.net/projects/ms-sys/files/ms-sys%20stable/2.2.0/ms-sys-2.2.0.tar.gz/download")

---

### Post by vghaisas on 2010-08-25
> **Grenage said:**
> Will it boot?  Probably.  Restart and find out; it's not like your data will disappear.


Worst case scenario, you boot from an XP disc and run fixboot, or boot from you Ubuntu CD and reinstall grub.

The worst case scenario is what I want to avoid!

Mainly because--

1) I don't have an XP installation disc!
2) I don't like worst case scenarios!

I do not wish to damage my system. I want to do whatever is possible while it is running. Which is why I don't want to take the risk of rebooting...

---

### Post by ks07 on 2010-08-25
> **newbie.who.needs.help said:**
> The worst case scenario is what I want to avoid!

Mainly because--

1) I don't have an XP installation disc!
2) I don't like worst case scenarios!

I do not wish to damage my system. I want to do whatever is possible while it is running. Which is why I don't want to take the risk of rebooting...
Check the post above yours - was a bit slow at replying so I think you missed it! :D

Anyway, I don't believe it is possible to restore the MBR while booted into XP. You're going to have to restart. This will almost certainly not let you boot into windows until you fix the problem, which you're going to have to do using the Ubuntu Live CD and ms-sys as above.

The other, possibly easier way is to actually re-install Ubuntu. If you are careful, when installing pick to install to the free space on the drive. Then, once it is installed, Grub will be able to boot you into windows without any problems, so you can leave Ubuntu installed and ignore it indefinately, if you wished. :p

---

### Post by vghaisas on 2010-08-25
Yes, sorry, I was a little late in replying so I missed your post.

Actually, I quite liked the idea of reinstalling Ubuntu and then ignoring it... but that doesn't seem complete...any other ways?

.Actually, now that the Ubuntu partition is deleted, won't the GRUB bootloader get deleted too? (I'm hoping it will!...)

---

### Post by ks07 on 2010-08-25
> **newbie.who.needs.help said:**
> Yes, sorry, I was a little late in replying so I missed your post.

Actually, I quite liked the idea of reinstalling Ubuntu and then ignoring it... but that doesn't seem complete...any other ways?

.Actually, now that the Ubuntu partition is deleted, won't the GRUB bootloader get deleted too? (I'm hoping it will!...)
Yes, deleting Ubuntu will delete GRUB. However, **it will not delete the 'pointer' to it at the start of the drive**, which tells your computer to boot using GRUB. Of course, if it tries this it will fail because it has been deleted. This is why you need to fix the mbr, either with an installation CD (which you dont have) or a tool such as ms-sys that will need to be used from a Live CD/USB.

EDIT: There's also[ this]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php"), which you may be able to use while still booted (i doubt it though, so you'll need a bootable disc anyway... :sigh:)

---

### Post by vghaisas on 2010-08-25
> **ks07 said:**
> Yes, deleting Ubuntu will delete GRUB. However, **it will not delete the 'pointer' to it at the start of the drive**, which tells your computer to boot using GRUB.

Oh!...Thats not good. Quite discouraging actually!..... :(

I really regret that I don't have an installation CD... are you SURE ms-sys will work? And are there any tutorials for using it?

Is there REALLY no other way? Will using someone else's installation CD work? What about using a Vista or Win 7 CD? Will that work?

---

### Post by ks07 on 2010-08-25
> **newbie.who.needs.help said:**
> Oh!...Thats not good. Quite discouraging actually!..... :(

I really regret that I don't have an installation CD... are you SURE ms-sys will work? And are there any tutorials for using it?

Is there REALLY no other way? Will using someone else's installation CD work? What about using a Vista or Win 7 CD? Will that work?
ms-sys should work, although it's probably too much work considering I've just found this article concerning the tool I mentioned in the edit. Read this: [http://schivmeister.wordpress.com/2009/02/07/uninstall-linux-fix-mbr-from-within-windows-xp/](http://schivmeister.wordpress.com/2009/02/07/uninstall-linux-fix-mbr-from-within-windows-xp/)

Scroll down to the section titles "_**OK OK Now Let’s Just Fix It!"**_

---

### Post by Rubi1200 on 2010-08-25
> **newbie.who.needs.help said:**
> I really regret that I don't have an installation CD... are you SURE ms-sys will work? And are there any tutorials for using it?

Is there REALLY no other way? Will using someone else's installation CD work? What about using a Vista or Win 7 CD? Will that work?
> are you SURE ms-sys will work? And are there any tutorials for using it?From what I have read it will work and the article was already linked to earlier on.
> Will using someone else's installation CD work?Yes; see here for instructions: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
> What about using a Vista or Win 7 CD? Will that work?Probably not because, from what I have read, the way the bootloader is handled is done differently on later versions.
> Is there REALLY no other way? YES, in the absolute worst case scenario you can use an Ubuntu CD to restore the MBR.

Listen, newbie.who.needs.help, I understand why you are reluctant to restart the computer, but the only way to find out if everything is ok is to restart. You have an Ubuntu CD and we are here to help **if** something is wrong. I stress if, because from what you have posted so far, it seems more than likely that everything *should* be fine.

---

### Post by vghaisas on 2010-08-25
> **Rubi1200 said:**
> 
Listen, newbie.who.needs.help, I understand why you are reluctant to restart the computer, but the only way to find out if everything is ok is to restart. You have an Ubuntu CD and we are here to help **if** something is wrong. I stress if, because from what you have posted so far, it seems more than likely that everything *should* be fine.

Finally, someone who understands! Yes, I am **really** reluctant to restart my computer because everything works now and everything might stop working after a restart!

In any case, I cannot restart the computer for another 4 hours or so, and so, inevitably, this thread will resume only 16 hours after the time of this post.

If anybody has any more suggestions, I request them to please post them. Thanks for all your help and see you in 15:59:59!

---

### Post by Rubi1200 on 2010-08-25
> **newbie.who.needs.help said:**
> Finally, someone who understands! Yes, I am **really** reluctant to restart my computer because everything works now and everything might stop working after a restart!

In any case, I cannot restart the computer for another 4 hours or so, and so, inevitably, this thread will resume only 16 hours after the time of this post.

If anybody has any more suggestions, I request them to please post them. Thanks for all your help and see you in 15:59:59!
I will keep an eye on this thread and be back to check if everything went well or to help if it doesn't.
:)

---

### Post by ks07 on 2010-08-25
> **newbie.who.needs.help said:**
> Finally, someone who understands! Yes, I am **really** reluctant to restart my computer because everything works now and everything might stop working after a restart!

In any case, I cannot restart the computer for another 4 hours or so, and so, inevitably, this thread will resume only 16 hours after the time of this post.

If anybody has any more suggestions, I request them to please post them. Thanks for all your help and see you in 15:59:59!
If you don't want to restart your PC without having attempted a fix, follow this:

> **http://schivmeister.wordpress.com/2009/02/07/uninstall-linux-fix-mbr-from-within-windows-xp/]
First, get the utility[ here (http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php).]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php")
 Double-click on it and your browser will probaby pop up with a new  tab, window, or it will just pop up itself. All you would need to do to  be able to boot Windows again without having to deal with gibberish like  &#8220 said:**
> 
[*]Move that downloaded thing to  C:\WINDOWS
[*]Go to ***Start > Run***
[*]Type in  cmd
[*]Now you have a black box (and you are afraid)
[*]Type in  mbrfix /drive 0 fixmbr /yes
[/LIST]
 The above assumes that you are trying to restore the MBR on your  first Hard Disk. Subsequent ones will be numbered from 1 onwards.

---

### Post by vghaisas on 2010-08-26
Dear All,

Even though I was reluctant to restart my PC, it was shut down by somebody else yesterday. Forget that... anyway, now on booting it sayd -

grub: no such partition                                   or something like that...

I am going to wait for a windows CD to fix the MBR rather than use ms-sys.

P.S. When I get the Windows CD, can someone give me instructions for what to do? Also, do I have to run only 'fixmbr' or fixmbr AND fixboot (whatever that is...) ?

---

### Post by Rubi1200 on 2010-08-26
Here is the link describing how to repair the Windows XP bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section. The instructions are clear, but if you have any questions, feel free to ask.

Good luck! :)

---

### Post by vghaisas on 2010-08-26
:D :D :D PROBLEM SOLVED!!!! :D :D :D

I borrowed an XP installation disk off one of my friends and then used the repair option and fixmbr and fixboot to fix everything! It was pretty difficult though... XP made everything very hard to understand. But anyway, things are back to normal And everything is finally working! :D :D

---

### Post by Rubi1200 on 2010-08-26
> **newbie.who.needs.help said:**
> :D :D :D PROBLEM SOLVED!!!! :D :D :D

I borrowed an XP installation disk off one of my friends and then used the repair option and fixmbr and fixboot to fix everything! It was pretty difficult though... XP made everything very hard to understand. But anyway, things are back to normal And everything is finally working! :D :D

Excellent! I am really pleased things worked out.

Please mark the thread Solved using the Thread Tools near the top of the page.

Feel free to drop by and ask questions.

I hope you also reconsider installing Ubuntu; you will find people are more than willing to help walk you through things.

---

