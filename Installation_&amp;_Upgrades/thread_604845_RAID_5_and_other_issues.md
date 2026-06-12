---
title: "RAID 5 and other issues"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by c00kie1000 on 2007-11-06
So after I physically installed 4 500GB hard drives to make a RAID 5 on windows XP, upon boot up I got a "could not read operating system" error.  After some time trouble shooting windows and getting fed up, I decided to go with Ubuntu (what I have on my laptop).  Upon reformatting the Hard drive and installing Ubuntu, I tried rebooting and it gave me a grub error.  Unfortunately, the error message only says "grub read error" and there is no error number or anything.  I thought that maybe the problem was that I didnt have my raid set up, so I did that using these instructions: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)   while working off of the liveCD.  Upon rebooting, I still got the "grub read error".  Does anyone know how I can fix this?

oh also, I tried going into the liveCD again and it wouldn't recognize the raid, so I rebuilt it using mdadm and tried reinstalling grub, but it still gave me the error when I rebooted.


optimally, I'd like to have my 160GB hard drive be dual boot with Ubuntu and Windows XP, and then have my RAID be read as its own disk.  But I know I can make my hard drive dual boot later, the important thing is getting Linux to play along with my RAID

---

### Post by Fire_Chief on 2007-11-06
If you are installing Ubuntu on the 160GB drive and not directly on the RAID array, then it should not have a problem booting from the 160 GB drive (assuming you configured Grub to handle booting Ubuntu and Windows). If the system is trying to boot from the RAID array instead of the 160GB drive, then you would see the errors you are reporting. Check the BIOS and see what the "boot order" is set to. It may also be called the startup sequence or startup order. Make sure that the 160GB drive is in the boot order and that it is a higher priority than the RAID controller.
The RAID setup could be done after the Ubuntu installation is complete and running on the 160GB disk.

---

### Post by diggity on 2007-11-06
I had to disconnect my raid disks to install Gutsy otherwise I received a grub error on rebooting. I don't exactly remember the error. Once I had Gutsy installed on the single disk, I re-connected the raid disks and it booted fine. However, I've had a very difficult time with mdadm under Gutsy. I am having to use the old kernel from feisty (2.6.16 I think). The raid refuses to start under 2.6.22 kernel.

---

### Post by c00kie1000 on 2007-11-06
the 160gb hard drive is first on the list of hard drives in the bootlist.  Also, I disabled the raid controller in bios because I had read on other posts that the software raid from a motherboard can mess up software raid on linux.  Should I have it switched on or off?  I really dont want to have to disconnect my 4 sata drives to install Ubuntu on my other disk only to have to plug them in again and get the same error, but I guess I'll try it since I have no other real options at the momment.  Anymore input is greatly appreciated.

---

### Post by Fire_Chief on 2007-11-07
Since your motherboard can do hardware RAID across the 4 SATA drives, is there a particular reason you want to do software RAID instead?

---

### Post by c00kie1000 on 2007-11-07
I was thinking to do software raid so that Linux would recognize it.  Oh, ans since I've disconnected the SATA drives and reinstalled Ubuntu, I still get the grub read error.  What can I do to fix this?

---

### Post by Fire_Chief on 2007-11-07
Look and see what the error number is from Grub and check for solutions to that problem [here]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors")

*Edit*: Oops, I missed the part earlier where you said no number was showing with the error. Does the error line start with GRUB: ? How far does it get in the boot up process? (see the Grub menu?)

---

### Post by c00kie1000 on 2007-11-07
I get the error right after verifying the datapool, before I get the Stage1 or Stage1.5 screens

---

### Post by c00kie1000 on 2007-11-08
i think the problem may now be with the BIOS and possibly the partition table on my hard drive.  When I try booting off of the liveCD and select boot off of first hard drive I get: "Isolinux: Disk error 01, AX=0201, drive 80".  If I set my BIOS to just book from the hard drive, it still tries to boot off of CD twice and then gives me: "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".

---

### Post by Fire_Chief on 2007-11-08
Might want to check the mode for the hard drive in the BIOS settings. Usually has several options like LBA and CHS. Try changing the mode and rebooting to see if the drive is recognized or not.

---

### Post by c00kie1000 on 2007-11-08
Ive tried it on Auto, LBA and Large
I've also tried clearing the CMOS by resetting the jumpers on my motherboard to reset the BIOS, and that didn't work either.  I tried using Powermax from Maxtor on the hard drive (it's that brand) and it passed the quick tests but when trying to run the full ones it hangs and says "error reading log file".  Do you know of any tools that will let me erase and rewrite the partition table on the drive?  I think that might be the source of the problems... 

also, in my BIOS, I tried setting ALL of the boot devices to HARD DISK and took the ubuntu livecd out of the optical drive and when I rebooted it still did:
boot from cd:
boot from cd:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

so flashing my BIOS is an option, but I'd really like to leave that as a last resort

---

### Post by Fire_Chief on 2007-11-08
Any chance that drive is bad?

---

### Post by c00kie1000 on 2007-11-08
Well it's worked alright for 3 years now, and was working great until I tried installing the RAID.  If I can be certain that my BIOS is ok, then I might just give up on the drive and install Ubuntu on the RAID and just worry about the other drive later.  My 4 500GB drives in a raid 5 would give me 1.3TB or so, so 160GB is pennies compared to that.  But before I do anything like that, I need to be sure my BIOS is ok.

---

### Post by diggity on 2007-11-08
Are you trying to dual boot winxp and ubuntu? I see you had xp installed on the hard-drive initially. The error you are receiving is one I have encountered with a corrupted Windows MBR (master boot record). Which install method did you choose from ubuntu? entire disk or re-size partition?

---

### Post by c00kie1000 on 2007-11-12
I decided to check the IDE cables to see if that was the problem, so I switched it out and tried it with only one device instead of two on the cable, and it worked.  So I figure it was a faulty cable.  It was kinda old (4 years or so).  Now I installed XP and Ubuntu, and I've set up the raid in XP... Im going to set them up in ubuntu, but I'm worried that when I build the arrays there I might lose data?  I need to look at mdadm to see if I can just create a md0 and mount that.  Meh, I'll figure it out.  Thank you for all the help, everyone who posted

---

