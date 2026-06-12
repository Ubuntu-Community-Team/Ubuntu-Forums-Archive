---
title: "How to make an 'In place upgrade' like MS xp"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by nodnolse1 on 2013-07-12
I often try new settings, environments etc and often I get out from 'GUI', no ways to repair the damage. I used 'apt-get', 'dpkg' and reseted configurations files, 'kernel' and more but even when I get back the 'GUI', the system is compromised. Then, in this cases when repairing MS OS's like 98/2k/xp, using the ['In place upgrade' ]("http://support.microsoft.com/kb/978788/en-us")function in the 95% of the cases all system returns stable by deleting and reinstalling fresh system files/services. I think that an expert/s can make a sort of batch script that remove and install fresh system from Ubuntu repositories. Unfortunately I'm not able to understand what and how remove, reinstall, reconfigure in manner that a specific OS, for instance Ubuntu 12.04, become default as if it was just fresh installed but keeping user files and applications config/data. I dream a script that maybe natively (in the future) lets the user to reset and fix the system from terminal or maybe a choice in the gui menu that appears in 'recovery mode' from boot. Probably a 'reset to default sys/de/X/GUI files' as part of recovery tools should help many users, specially the new ones and alpha-tester like I. If you or someone that you know are able to produce a similar thing, please, join/merge yours knowhow to make Ubuntu users experience more confident and relaxed. Thanks for reading even if I think that these arguments are not interesting for exert users since that know exactly what to do when the system is faulty, then beginners users get always the same answer: '''fresh/clean install''. Best regards, Paolo


P.S. another missing and very important function is ['System Restore']("http://windows.microsoft.com/en-us/windows7/products/features/system-restore") like MS, even if MS is not my favorite OS, this function is really great. Please create it

---

### Post by Mark Phelps on 2013-07-12
MS's System Restore is NOT what many people think it is -- it is NOT a time-machine that rolls back the clock.  When Windows updates are performed, and when apps are installed, Windows creates a Restore Point.  This is NOT an image copy of the current state of MS Windows; instead, it saves off the system files that are being updated.

The MS tool should really be called Operating System Restore -- because that is what it really does.  When you select a Restore Point, that is a associated with a copy of system files and settings that were made at a point in time.  When you run System Restore, it overwrites the current system files (including the Registry) with those saved copies.

I personally have found System Restore to be useless and prefer, instead, to do my own image backups with Macrium Reflect (in Windows).

In Linux, I use Clonezilla to image off my current distros.  IT only takes a few minutes, and it is very easy to run a restore, should I need to get back the working system.

There are other backup/restore solutions, as well, including DejaDup and RemasterSys.  You should read about these and how they can be used to backup/restore your Linux system.

---

### Post by oldfred on 2013-07-12
If you are having Boot issues you can run this gui.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

For just about anything else you can chroot from a liveCD (or Boot-Repair) and run every update or repair you might need to fix just about anything. But sometimes a reinstall is just easier if you have backed up /home, any other data you might need and a list of installed apps.

---

