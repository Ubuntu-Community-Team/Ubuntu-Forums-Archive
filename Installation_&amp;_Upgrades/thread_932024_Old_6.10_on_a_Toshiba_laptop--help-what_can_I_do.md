---
title: "Old 6.10 on a Toshiba laptop--help-what can I do??"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by goodyear on 2008-09-27
I have a problem with my Ubuntu installation--I can't get rid of it!  I have 6.10 because I installed it a long time ago and then left the country to work. I got another computer when I returned, and long story short, I have 6.10 on my Toshiba Satellite 5205-S505 laptop and cannot upgrade, support, or remove it!  Toshiba has (had-it is not available w/Ubuntu that I know of) a Hardware Manager program in the control panel to change boot sequence and as I no longer have Windows, I cannot change my BIOS to put a different OS on.  Any ideas?  I am going NUTS!  My "new" computer is not what I want it to be--I want to be able to use my laptop!!  Thanks!!

Melissa](*,)](*,)

---

### Post by melojo on 2008-09-27
> **goodyear said:**
> I have a problem with my Ubuntu installation--I can't get rid of it!  I have 6.10 because I installed it a long time ago and then left the country to work. I got another computer when I returned, and long story short, I have 6.10 on my Toshiba Satellite 5205-S505 laptop and cannot upgrade, support, or remove it!  Toshiba has (had-it is not available w/Ubuntu that I know of) a Hardware Manager program in the control panel to change boot sequence and as I no longer have Windows, I cannot change my BIOS to put a different OS on.  Any ideas?  I am going NUTS!  My "new" computer is not what I want it to be--I want to be able to use my laptop!!  Thanks!!

Melissa](*,)](*,)

google search
Satellite 5205-S505 (2.2GHz Pentium 4-M, 512MB, 60GB, CDRW/DVD, Windows XP Home, 15" TFT)

If it is a satellite 5205-s505 it looks like it originally came with windows xp.

What os were you wanting to put on the laptop?

---

### Post by lemuriaX on 2008-09-27
can you boot from CD by changing the boot sequence in set up? Not sure which key it is with a Toshiba laptop but usually pressing the delete key when booting up will allow you to make changes to your bios such as boot sequence...

---

### Post by goodyear on 2008-09-27
Any at this point, I just need to start somewhere!  Any suggestions?  I still have XP oem cd I can use, but I'd like to think about trying to Ubuntu or something similar again.
M

---

### Post by goodyear on 2008-09-27
> **lemuriaX said:**
> can you boot from CD by changing the boot sequence in set up? Not sure which key it is with a Toshiba laptop but usually pressing the delete key when booting up will allow you to make changes to your bios such as boot sequence...

Toshiba has a hardware management program in Windows control panel that manages boot sequence.  I no longer have Windows (of course) and have tried *every single button* I can see to no avail.:confused:

---

### Post by goodyear on 2008-09-27
Any tricks to get to boot sequence?  If not I'd love to upgrade my 6.10 to a newer (supported) OS.

---

### Post by melojo on 2008-09-27
> **goodyear said:**
> Any tricks to get to boot sequence?  If not I'd love to upgrade my 6.10 to a newer (supported) OS.

I googled and found this give it a try

In order to boot the laptop from the recovery CD you have to change the boot order in the BIOS and make sure the DVD drive is listed first. Alternatively, you can press F12 key as soon as Toshiba logo appears on the screen. After that it will display the boot menu and you can select the DVD drive. Here’s one more trick. Press “C” key when Toshiba logo is displayed, it will boot the laptop directly from the CD-Rom without displaying the boot menu.

---

### Post by lemuriaX on 2008-09-27
should be able to change boot sequence by rebooting and holding the del key (most likely) down while it's booting up - which would take you to Set Up...

---

### Post by melojo on 2008-09-27
> **lemuriaX said:**
> should be able to change boot sequence by rebooting and holding the del key (most likely) down while it's booting up - which would take you to Set Up...

Support Bulletins

How to access the BIOS Settings on your legacy-free Toshiba Portable PC

Document ID:  98080112
Posted Date:  11/29/02
Last Updated:  11/29/02
Operating System:  BIOS, Windows 2000, Windows XP
Category  BIOS
Distribution  Public
Applicable Models:  Satellite 5205-S119, 5205-S705, 5205-S5151, 5205-S506, 5205-S505, 5205-S704, 5205-S504, 5205-S703, 5205-S503, 5105-S901, 5105-S702, 5105-S502, 5105-S701, 5105-S501, 5105-S608, 5105-S607, 5005-S508, 5005-S507, 5005-S504

just found this.  I won't be buying a toshiba.

Issue solution survey
This document provides information about how to access the BIOS settings on applicable models.

Procedure
These models are considered 'legacy-free', and offer only a Windows-based BIOS setting utility.
From the Windows Control Panel, launch the Toshiba HWSetup program. HWSetup provides a user-friendly graphical frontend for modifying BIOS settings. Please note that if you change some settings, you may be required to restart your computer. HWSetup comes preinstalled on your Toshiba portable PC, or it can be downloaded as part of the Toshiba Utilities package for your model.

in the same thread it said this also.

To Boot from CD/DVD on toshiba satellite 5005-S507:
1.power on
2. press F12
3. with the right arrow key choose cd
4.enter

---

### Post by lemuriaX on 2008-09-27
Oh cool - so it's the F12 key looks like for you or as Melojo also found sounds like you could use "c" to directly boot from CD. Maybe download the latest Hardy install CD image, burn it to CD and try a live CD session out. You could even keep your old Edgy install on it's own partition if you want.

---

### Post by goodyear on 2008-09-27
So after much stress and heavy drinking you do in 2 minutes what I couldn't in a week (and more) of Googling the S#*t out of this.  The F12 did nothing, but the "C" key did it!  I am going back to XP for now, but I'd loooove to hear input on something a little less.....windows!  I don't have a lot of time (or knowledge--I know mostly savvy Windows stuff) to build, and write, etc--I am a full time mom of 2 baby girls and a Medical student.  Ideas????  Thank you!!!!

---

### Post by melojo on 2008-09-27
> **goodyear said:**
> So after much stress and heavy drinking you do in 2 minutes what I couldn't in a week (and more) of Googling the S#*t out of this.  The F12 did nothing, but the "C" key did it!  I am going back to XP for now, but I'd loooove to hear input on something a little less.....windows!  I don't have a lot of time (or knowledge--I know mostly savvy Windows stuff) to build, and write, etc--I am a full time mom of 2 baby girls and a Medical student.  Ideas????  Thank you!!!!

You have a big enough hard drive that ubunu would look good on 1 partition=D>
glad we could help!!!

---

### Post by goodyear on 2008-09-27
> **melojo said:**
> You have a big enough hard drive that ubunu would look good on 1 partition=D>
glad we could help!!!
  Ummm... Love to---can you direct me to a "How to".  I'm very comfy w/computers, but new to OS tweaking, grubbing, scripting, etc:shock: and all that cool stuff ya'll can do so easily.  I sooo want to divorce Windows though!  A million thanks AGAIN!!

---

### Post by goodyear on 2008-09-27
BTW I'm at the setup part of XP install that deals w/partitions.  I have C: 55757 MB, and E: 1475 MB.  How can I install in a way that willleave space for a Linux based OS?

---

### Post by melojo on 2008-09-28
> **goodyear said:**
> Ummm... Love to---can you direct me to a "How to".  I'm very comfy w/computers, but new to OS tweaking, grubbing, scripting, etc:shock: and all that cool stuff ya'll can do so easily.  I sooo want to divorce Windows though!  A million thanks AGAIN!!

Probably the best thing for you to do is try a live ubuntu cd and you can run and test it out before you commit.  You have to understand that linux is not windows and windows is not linux.  You have to be willing to not think like a ms windows user, it is a different operating system.  I find linux to be my favorite os but not all think so because they are trained to be ms windows users.  If we were all brought up using linux and didn't think like ms windows users(not that anything is wrong with windows-playing both sides of the fence sorry to all you windows and linux fans.") It would be easier.

Link to live cd below.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by goodyear on 2008-09-28
Does live Ubuntu CD simulate the tweaks and programming types of things I'd need to use to get things running comfortably---file properties, media support, etc?  What would partitioning hurt if I decided not to use it after installing?

---

### Post by melojo on 2008-09-28
> **goodyear said:**
> Does live Ubuntu CD simulate the tweaks and programming types of things I'd need to use to get things running comfortably---file properties, media support, etc?  What would partitioning hurt if I decided not to use it after installing?

I would just try the live cd and see if it detects everything ok.  The same cd will also repartition and install ubuntu if you so desire.  Baby steps are sometimes the best way to approach new things.

---

### Post by goodyear on 2008-09-28
K...Thanks!  Got 8.04 burning!

---

