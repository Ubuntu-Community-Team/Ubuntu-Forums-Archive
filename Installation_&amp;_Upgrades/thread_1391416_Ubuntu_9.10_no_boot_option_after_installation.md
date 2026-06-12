---
title: "Ubuntu 9.10 no boot option after installation"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by petatkinson on 2010-01-26
I have installed Ubuntu 9.10 on a system that already had XP on it.Up to 9.04 I always updated but with all the difficulties users have been experiencing I decided to do a fresh install.Well on re-boot it went straight to XP with no boot options.I then find out about this new wonderful GRUB2 boot loader.I have a bit of experience with Linux and its filesystems but there is no way I am messing about with the MBR as when installing Ubuntu the installer didn't even recognise that I had an operating system installed.Disk 0 is a 500gb IDE drive, disk 1 is a 500gb sata drive.Help needed here.

My point on the above is if I have a bit of experience on Linux and hit a problem like this how am I going to convince the standard user to install and use Ubuntu.Why was the original GRUB changed.The saying "if it aint broke don't fix it" comes to mind.We all saw where messing with a tried and tested operating system got Microsoft ie Vista.I am a long time around computers but I would not expect to have to go around messing with an MBR in order to get an operating system running.There are bigger and better challenges to be taken on by Linux in general and Ubuntu in particular and designing a new bootloader is not one of them.

---

### Post by kansasnoob on 2010-01-27
Is your grub OK now?

Quite honestly grub2 is better than legacy grub, it's just new.

New things always present a learning curve.

---

### Post by petatkinson on 2010-01-27
In a word no.I shouldn't have to worry wheather mt GRUB is right or not.Thats my point.I did the installation, answered all the right questions, re-booted and straight into XP.No choice of OS.Whats happening.I've used Ubuntu since 7.xx and no installation problems like this.Is this GRUB setup the same for all variants of Linux theses days.I can feel people walking away from it as I speak.Surprised I only had one comment on this issue although all I can see is posts with GRUB problems.I have no problem tweaking systems when they are operational but life is too short to be messing MBRs.

---

### Post by mr clark25 on 2010-01-27
when you hold SHIFT down when you startup, it should bring up the grub menu.

check and see if all of your bot options are there.

if they are, i can guide you through on how to make the menu come up without holding down shift.

---

### Post by kansasnoob on 2010-01-27
If you really just want to revert to legacy grub that's why I wrote this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by presence1960 on 2010-01-27
> **petatkinson said:**
> I have installed Ubuntu 9.10 on a system that already had XP on it.Up to 9.04 I always updated but with all the difficulties users have been experiencing I decided to do a fresh install.Well on re-boot it went straight to XP with no boot options.I then find out about this new wonderful GRUB2 boot loader.I have a bit of experience with Linux and its filesystems but there is no way I am messing about with the MBR as when installing Ubuntu the installer didn't even recognise that I had an operating system installed.Disk 0 is a 500gb IDE drive, disk 1 is a 500gb sata drive.Help needed here.

My point on the above is if I have a bit of experience on Linux and hit a problem like this how am I going to convince the standard user to install and use Ubuntu.Why was the original GRUB changed.The saying "if it aint broke don't fix it" comes to mind.We all saw where messing with a tried and tested operating system got Microsoft ie Vista.I am a long time around computers but I would not expect to have to go around messing with an MBR in order to get an operating system running.There are bigger and better challenges to be taken on by Linux in general and Ubuntu in particular and designing a new bootloader is not one of them.

GRUB 0.97 will soon be obsolete. It hasn't been updated in quite some time. GRUB2 is not hard, it is just different than GRUB 0.97. Just as you had to learn GRUB 0.97 you will learn GRUB2. To lament about "the good ole days" will not help you in the least.

Now to your problem. I need to see exactly how your machine is set up and the boot process before making any suggestions. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by petatkinson on 2010-01-28
Thank you for your help and I certainly will try what you suggest but the point I am making is it is supposed to be getting easier to deal with Linux and its installation and not harder.Prior to this I loaded the live cd, chose the install option, answered the questions and away it went.At the end it formulated the boot menu taking into account I was running another OS (XP in this case) rebooted and the boot option screen appeared.I chose what OS to load and that was it.The question I am asking is it that simple now.

I am not lamenting the passing of old believe you me.I used to load mag tapes on to an IBM mainframe, load punch cards on an old Cobol based DB system so I for one appreciate progress but change for the sake of change.Linux is not a gaming based system so why all the development on 3D graphics and effects.Courses for horses and I know what Linux does best.After all it is a Unix derivitive and we all know what Unix does best.

I will post back my results based on your suggestions

---

### Post by presence1960 on 2010-01-28
> **petatkinson said:**
> Thank you for your help and I certainly will try what you suggest but the point I am making is it is supposed to be getting easier to deal with Linux and its installation and not harder.Prior to this I loaded the live cd, chose the install option, answered the questions and away it went.At the end it formulated the boot menu taking into account I was running another OS (XP in this case) rebooted and the boot option screen appeared.I chose what OS to load and that was it.The question I am asking is it that simple now.

I am not lamenting the passing of old believe you me.I used to load mag tapes on to an IBM mainframe, load punch cards on an old Cobol based DB system so I for one appreciate progress but change for the sake of change.Linux is not a gaming based system so why all the development on 3D graphics and effects.Courses for horses and I know what Linux does best.After all it is a Unix derivitive and we all know what Unix does best.

I will post back my results based on your suggestions

It is not harder, but more that it is "new" or "different". Whatever you knew about GRUB 0.97 will not help you with GRUB2. GRUB 0.97 will soon be unable to boot hard disk of the sizes that are coming out. I beleieve that is one of the reasons for the change. I know GRUB 0.97 pretty good, but I find GRUB2 way more reliable. Once I studied and learned about it that is.

---

