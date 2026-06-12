---
title: "Upgrade issues"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2007-04-20
Yesterday I completed the upgrade from 6.10 to 7.04  The upgrade went smoothly... just long waits for downloads for obvious reasons.  However, 2 minor issues, so far:

1.  On linux boot I get the following 'fail' messages:

   (from dmesg)

[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support

...

[   37.501024] PM: Checking swsusp image.
[   37.509105] PM: Resume from disk failed.

Both "fail" messages seem to be related.  I believe ACPI has to do with the computer sleeping, resuming, and the battery... I do have a battery backup device.  I read that ACPI is weak program to begin with... [http://www.advogato.org/article/913.html]("http://www.advogato.org/article/913.html")... what are my ubu-choices for this?

2.  I've got a dual boot system (w/ Win 2K) and use a vfat usb-attached disk to share some common files for Firefox/Thunderbird like bookmarks, mailboxes, etc.   The problem became apparent when I opened Thunderbird and found no mailboxes,,, the usb drive icon was on my desktop and on opening the drive icon everything looked correct.   So I went to the terminal and noticed that the drive mount point had changed... it used to be "/media/WDC USB2/"  and now it's "/media/WDC USB2_/".... of course that threw off all the references in F-fox/T-bird.   
   Looked in the fstab... the usb drive doesn't get mounted there, noticed that I can change the mount point from the "Properties" of the associated drive icon.. this wil most likely work, however, can someone tell me how to do this from the terminal.

Thnx
Rich

---

### Post by rgeddes on 2007-04-20
OK, I solved my #2 problem... /etc/fstab is where I specified how I wanted my external USB drive mounted.   The space in the mount point gave me some problems, which is specified as '\040' (from man fstab) then everything worked out...  a drive icon appeared on the desktop.... by the way, is there a way to force a drive icon to (not) appear on the desktop... as far as I know it just appears...  I'd like to get my home directory to appear on my desktop as well.

R

---

### Post by rgeddes on 2007-04-23
Another issue I noticed is that a few of my preferences are being over-written in the Feisty upgrade:

I've run azureus w/ java-6-sun vs java-gcj(gnu) and found a world of difference between the two... the gnu version still needs much work.. it crashes frequently, and when it runs, top reports ave loads of 5 - 10, about 30 - 50% cpu ... sun java runs much smoother... load ave < 1, 3 - 10 % CPU... of course since everything on computers is preformance related... other apps have more breathing room.

Before upgrading I removed the java-gcj... no problems.   It seems the Feisty upgrade reinstalled java-gcj and reworked the symbolic links in /etc/alternatives to get java-gcj back in the loop.  So I figured I could remove java-gcj and the system might be smart enough to point to the java-6-sun .... no can do... trying to remove java-gcj will force remove eclipse, which I'm using for java programming.   Fortunately, there were only 5 - 6 links in the /etc/alternatives that needed to be changed...  seems java-gcj is being promoted over other implementations in ubuntu... as I understand it, java-6-sun is open source now, so it should be user selectable.

Also, I prefer mplayer over totem.  Pre-upgrade to Feisty, I removed totem.  Feisty upgrade reinstalled totem, and changed my prefs in firefox to work totem back into the line-up ... 

R

---

