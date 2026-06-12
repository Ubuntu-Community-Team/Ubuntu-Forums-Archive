---
title: "Window 8.1 and Ubuntu 14.04 dual boot issues- advanced- especially clock"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by aninkling on 2014-08-18
Some of the installation history and previous problems, see [previous post]("http://ubuntuforums.org/showthread.php?t=2232535&p=13064119#post13064119").  At this time I have Ubuntu 14.04 and the latest updated version of Windows 8.1 installed.  Ubuntu is installed on one hard drive and Windows 8.1 is installed on another hard drive.  It is necessary to point out that I have a twin screen (monitor) setup, with both operating systems set up to treat the two screens as one.  

When I cold start, the grub is displayed and I can select the usual grub entries, with Windows 8.1 at the top.  If I don't do anything, then Windows 8.1 will start.  If I want to start Ubuntu, then I use the down arrow key to highlight the standard Ubuntu start.  

**Issue 1**:  I have twin screens.  The grub selection list is displayed on both screens.  However, when I move the selection using the arrows keys, the left screen does not necessarily match the right screen selection.  Where the selection moves on the right screen seems random:  it can move one, move two, or not move at all, when I move the selection from the Windows 8 option to the **Ubuntu* option.  However, the left screen seems to be the master; I ignore where the right screen.  

**Can anyone describe why this is so?**

**Issue 2**:  If I have gone into Ubuntu and later cold start into Windows, it works fine.  Note that Windows first throws up an intermediate screen that seems to be Windows version of the grub, except it is graphical.  I am given the option of selecting Windows 8 or Ubuntu.  I can click on the Ubuntu and Ubuntu will start.  I can click on the Windows and Windows will start.  If I don't click on anything, then I get a black and white screen with a bunch of system messages and a message that says no operating system was selected.  I have to turn off the machine and start over.  

**What is going on here?**

**Issue 3**:  Once windows starts, it is fine _except_ the _time reported by Windows is set to Greenwich mean time_.  I have to manually change the time.  

**Why is this and how can I fix it?**

---

### Post by oldfred on 2014-08-18
I do not know about dual screens. But there are solutions to the time issue.

 [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
time, UEFI, windows 8  - several posts by sudodus  
[http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648](http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648)

---

