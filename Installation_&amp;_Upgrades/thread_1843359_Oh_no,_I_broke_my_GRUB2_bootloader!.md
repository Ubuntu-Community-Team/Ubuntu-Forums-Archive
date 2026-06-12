---
title: "Oh no, I broke my GRUB2 bootloader!"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by molotov256 on 2011-09-13
Hey all, I got to reconfiguring my hard disks in my main tower, and I've messed up GRUB in the process.

I originally had Win 7 and Ubuntu Studio  installed on a disk split into 3 partitions (Win 7 OS on one partition, Win 7 data stored on the second, and a 3rd little partition I'd set up to try Ubuntu) .  I wound up needing more space on the C: partition for Windows, so I threw in a new drive (H:) for data, deleted the D: partition and expanded C: over the space previously allocated to D. 

Now on reboot, i get:

```
error: no such partition.  grub rescue> _  
```

I've read that the easy fix is to delete the ubuntu partition and then use my Win 7 disk to run MBRFIX.  The issue is I can't seem to boot off any CD's now (Tried UBCD4WIN and my OEM Win7 disc).  I've triple checked BIOS and it's set to boot from CD before HDD.  I don't even get the option to press any key to boot from CD before I get the GRUB error.

I'm hoping I'm missing something simple here, and sorry if this sounds too much like a Windows thread - I just need to get past this GRUB issue before I can straighten out my Microsoft mess :)

---

### Post by dino99 on 2011-09-13
first you need to find why you cant boot on cd, grub have nothing to do at this step

see the grub2 guide link below

---

### Post by BeowulfNode on 2011-09-13
not being able to boot from cd from bios is not a grub problem.
when you put in the extra hdd you may of knocked out the cd data cable a bit, try re-plugging it an the power cable too.

try the cd in another pc to check it does actually boot. I've been caught out by a tool that was supposed to make a bootable cd and it didn't

is there an option like "removable media" before cd in bios? if so remove it or move it behnd cd.  if you have any usb disk or card readers plugged in remove them. they often mess up drive ordering.

as to the grub error i expect grub is looking for the 3rd partition on /dev/sda to boot ubuntu and now can't find it since there are only 2. but i could be very wrong about this one

---

### Post by molotov256 on 2011-09-13
Thanks for the  quick reply.  I agree, I've gotta get this thing to boot  off a CD, but I've never had a machine that wouldn't boot off a CD  after making the appropriate BIOS adjustments, so I'm a little perplexed  here.  I'll start looking into other non-GRUB related causes for that.

Of course, if anybody has any insight into why a PC might not boot from  CD's (other than boot device priority in BIOS), I'd appreciate it!

---

### Post by molotov256 on 2011-09-13
> As to the grub error i expect grub is looking for the 3rd partition on  /dev/sda to boot ubuntu and now can't find it since there are only 2.  but i could be very wrong about this one

I was thinking the same thing.  Can I just point GRUB at the second partition?

From another thread I'm reading:
[http://ubuntuforums.org/showthread.php?t=1359802&highlight=grub+error+boot+cd](http://ubuntuforums.org/showthread.php?t=1359802&highlight=grub+error+boot+cd)
> 
can you boot into windows by entering the following commands?

 	Code:
 	grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot 

 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by leef; December 20th, 2009 at 05:36 AM.. 					 					 				*


Those commands aren't working for me - the poster says later to change "rootnoverify (hd0,0)" to "set root=(hd0,0)" for GRUB2, and when I do that, it does not generate any response, so I assume it works.  However, "makeactive" doesn't work, so I assume all the commands have been updated?

If I can find the right commands for the GRUB 2 rescue console, can I in theory point it to hd(0,1) and see how that goes?

Granted, that won't solve the issue with booting from CD, but it might get me back into the computer.

Oh, and I did open the case and check the IDE cable to the CD drive.... I unplugged it and plugged it back in and am getting the same results.

---

### Post by Quackers on 2011-09-13
Your bios is set to boot from cd first, I believe. Which cd drive are you using? Is it an internal drive or a USB cd drive? Which is the bios set to boot first - internal or USB? Check that.
Once that's checked I would try powering off the pc and leave it for a minute.
Then put the cd in the drive and power up the pc. If it gets to a grub prompt of any kind the cd is not being recognised or the cd is not bootable. Has this cd been booted from in the past?

---

### Post by molotov256 on 2011-09-13
Ok, somebody shoot me or slap me or something.  :roll:

yeah, it was a BIOS issue.  I've only got one optical drive, and for some reason 2 different ones are listed in BIOS.  Turns out I had the mystery nonexistent optical drive at the top of the list.  Durhhh...

Very sorry, quite embarrassed, and hopefully I can extend my C drive and repair my win 7 MBR now.  

Thanks again for the replies, one can't help but love the Linux community (with exception for folks like me who can't diagnose the problem when it's right in my face!)

---

### Post by Quackers on 2011-09-13
It's easily done! Too many options in there :-)

---

### Post by molotov256 on 2011-09-13
Just to wrap up the thread on a positive note, the issue is solved.  The steps that wound up working for me (after my silly mistakes described above) were:

1) Set optical drive as first boot device in BIOS
2) Boot from UBCD4Win
3) Use partitioning utility to delete Ubuntu partition (nothing personal, still using Ubuntu on this laptop!)
4) Reboot from a Windows CD/DVD to repair MBR (plenty of good tutorials out there for that step)

Thanks everybody.

---

### Post by Quackers on 2011-09-13
Good to hear. Thanks for the update.

---

