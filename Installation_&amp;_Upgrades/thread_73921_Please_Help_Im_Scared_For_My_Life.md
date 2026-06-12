---
title: "Please Help Im Scared For My Life"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by asonjay99 on 2005-10-10
yeah has windows installed on my computer and i decided that i would repartion my hard drive and do a dule boot of windows ans linux and i got another computer that i wanted to put linux on...that went swiminly. i decided i wanted the other computer for windows so i downloaded partition magic 8.0 and i deleted the linux partition and restarted my computer and when i restarted it it comes up to where it would normaly com up to asking me if i want to load linux or windows but instead it says there is an error (error 17) and i cant load from a d or anything and if my dad fins out what i did i am dead 

please someone help me

---

### Post by Raj on 2005-10-10
Hi asonjay99,

First thing, dont panic and calm down. In situations like this, I usually find that panicing leads to mistakes, which by the sounds of things, is not what you need.

I'm fairly new to linux, but a reasonably old hand with windows, so please breakdown the problem a little more clearly.

Are you saying you had Ubuntu and Windows (what version please?) dual booting on the same machine? Do you have information about the partitioning and also how were you booting the machine?

I've re-read your post, did you move the drive? exactly what have you done, im just having a little difficulty understanding. do you have a windows disk incase you need to use that to fix the mbr [which may or may not help]. sorry for all of the questions, but as i am new also, more info might mean that i can help [hope so]

cheers

raj

---

### Post by Lord Illidan on 2005-10-10
So you have a harddisk which you deleted Linux from, because you want it Windows only.

Easy, if you have the XP cdrom..

To start the computer and use the Recovery Console to replace the MBR

   1. Insert the Windows XP Professional Setup CD-ROM into the CD-ROM drive.
   2. Restart the computer. If prompted to press a key to start the computer from the CD-ROM, press the appropriate key.
   3. When the text-based part of Setup begins, follow the prompts. Press the R key to repair a Windows XP Professional installation.
   4. If you are repairing a system that has more than one operating system installed, from the Recovery Console choose the Windows XP Professional installation that you need to repair.

      Note
          * If you press ENTER without typing a number, the Recovery Console quits and restarts the computer.
          * The Recovery Console might also show valid installations of Windows NT 4.0. However, the results of attempting to access a Windows NT 4.0 installation can be unpredictable.

   5. When prompted, type the Administrator password. If you do not have the correct password, or if the security database for the installation of Windows XP Professional you are attempting to access is corrupted, Recovery Console does not allow access to the local disks and you cannot repair the MBR.
   6. To replace the MBR, at the Recovery Console command prompt, type:

fixmbr

---

### Post by jrib on 2005-10-10
I might have misunderstood you, but it sounded like you want to put windows on the other computer by itself.  Have you tried putting in the windows cd and booting from it?  With Windows XP you can edit the partition table.  So you could delete  all of the existing partitions and create a new one for Windows. ([edit] lord Illidan's reply above is more detailed if you are looking to repair an existing window XP install.)

Listen to Raj and calm down, its not the end of the world.  Try to give us some more details, it's not totally clear what you are trying to do.

---

### Post by asonjay99 on 2005-10-11
nevermins i got it to work...for some reason teh cdrom drive asnt pluged into the motheboard and yeah it was causeing problems and i coulnt start from the cd but now everyting is cool...thanks anyway

---

