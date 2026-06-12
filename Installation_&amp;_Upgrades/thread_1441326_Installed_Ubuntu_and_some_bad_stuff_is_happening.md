---
title: "Installed Ubuntu and some bad stuff is happening"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by bannana on 2010-03-28
I installed Ubuntu for the first time today. I thought it would nice to try using another operating system besides windows. I have in the past messed around with the Os BackTrack and i wanted to try Ubuntu. 

I have two hard drives in my computer, a Western Digital 320gb and a Seagate 500gb. On the SGhd I have Win7 installed and all my other crap. On the WDhd I have half of wndows 7 installed and my media files. I decided to try and install Ubuntu on the WDhd. I partitioned 20gb of space for it (I know not enough, I was going to hop on Win7 and fix that). Ubuntu installed alright, nothing bad happened. Although I did fool around with the disk Utility took and I might have changed the SGhd type from NTFS to (something/NTFS) I dont know if that could have done something and sorry about not being 100% specific there.

 I decided that I would use the terminal to shutdown the computer so that I could get aquainted with the OS. So i typed in something along the line of "sudo -shutdown now" and the computer turned off. *Also before I installed Ubuntu on the WDhd I unplugged the SGhd from my mobo so that I could correctly partition the WDhd when I was installing Ubuntu. 

I then plugged back in the SGhd into the mobo to boot up into Win7. I booted up my computer again and then got a a boot manager screen and clicked on Windows 7. 

Here is where the **** hit the fan :/. Win7 didn't want to load and then i tried Ubuntu, it too didnt want to load. So I reinstalled Ubuntu and a whole new slew of probmes are happening. 

When I boot off of the SGhd i get to a screen 
PCI device listing
(Table of devices)
Verifying DMI Pool Data
NLDR

THen when I boot off of the WDhd i get
PCI device listing
Verifying DMI Pool Data
Grub loading
error: unknown filesystem
grub rescue> _

I am lost as to what I have to do and I hope the answer isnt to reformat. :?

I am sorry for the long post :/. Please Help

---

### Post by 2hot6ft2 on 2010-03-28
When you installed BT (BackTrack) it installed grub.
When you deleted BT the grub is still pointing to where BT was and therefore can't load the info that was there like the menu.list file.
So if you install ubuntu 9.10 **"the same way you did BT"** it will install grub-pc (grub2) over grub, and you should be ok.

By the same way I mean **IF** both drives were in at the time they should both be in and in the same locations (same tapes (cables) and same positions on the tapes), if you made no changes to where the boot loader would be installed (step 7, actually BT skips a few steps but the last step before it starts installing) then don't make any this time either.

Note: BT uses grub and ubuntu 9.10 uses grub2 (now called grub-pc).

> **bannana said:**
> I have half of wndows 7 installed and my media files.
How you managed to do this part is beyond me. I've never installed 1/2 of an OS anywhere, and had it work that is.

---

### Post by bannana on 2010-03-28
Thank you for the reply. After I reinstalled Ubuntu on the WDhd it finaly worked. I then proceeded to poke and prod at the SGhd and now I have about 15 random partitions and one of them says that ive got a few trillion gb of information i can store on it o_0. Guess I have to just wipe that puppy clean and just convert back to NTFS if I want to install Win 7 on it :/. But Ubuntu works!! :D

---

