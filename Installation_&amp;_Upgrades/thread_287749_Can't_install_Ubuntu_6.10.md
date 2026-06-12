---
title: "Can't install Ubuntu 6.10"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by foof on 2006-10-29
First I tried to upgrade from Dapper... got some errors during upgrade, but it seemed to continue anyway. When rebooting X doesn't start. I have tried to reinstall the NVidia driver, but it still doesn't work.

So I decided to start from scratch, format the drive and make a clean install. I downloaded the 6.10 CD and started... all went fine until reboot, then it says remove CD and press enter... but nothing happens when I press enter! If I press ctrl+alt+del something happens, but I end up in the same position again... press enter and nothing happens! So I turn of the computer and tries to boot, but it doesn't boot... just a cursor in the left upper corner. What's wrong? I have a SATA drive... I did set the / (root drive) flag to boot, but it didn't help.

---

### Post by senior on 2006-10-29
Hi Foof,
Q1: Does your PC work properly with a live Ubuntu version x CD ?? 
    If yes: write down the information you need for your video and/or the screen.  

Q2: Can you reach the installed system by console (Ctr+Alt+F1 etc)??

Senior.

---

### Post by sparrowhawk on 2006-10-29
I have exactly the same problem ! Ubuntu installs then on reboot after removing cd............pc sits showing "verifying dmi pool data "
I have now tried re-installing several times and have come to the conclusion that it is a Grub/Sata problem.

Suse 10.1 installs and boots evry time !

Waiting and hoping for help.

---

### Post by mgolden on 2006-10-29
> **foof said:**
> First I tried to upgrade from Dapper... got some errors during upgrade, but it seemed to continue anyway. When rebooting X doesn't start. I have tried to reinstall the NVidia driver, but it still doesn't work.

Have you tried this stuff?

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

### Post by foof on 2006-10-29
I got it working, but I can't quit the Live CD correctly, but now my machine boots. Somehow it didn't like my RAID card anymore, I have unplugged it now. It's a later problem...

Now it works, have just installed the Nvidia driver and Beryl and it works great!

---

