---
title: "Ubuntu 7.10 won't shutdown"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2007-11-27
Ever since I upgraded to 7.10 I am having a problem shutting down.  If I click on the shutdown applet in the panel the computer does a reboot.  The same thing happens if I use the terminal and type 'shutdown -h 1'.  Someone suggested that Compiz was the problem so I removed Compiz from my system, but that hasn't helped.  At the moment I have to let the reboot happen and then I am able to do a proper shutdown by clicking the options menu on the login screen and shut down from there.

This is an annoying problem.  Does anyone have a solution?

---

### Post by aathomas on 2007-11-30
I am having same problem, IBM Thinkpad R32, Someone please help us.

---

### Post by Baasha on 2007-12-01
I have posted this problem a couple of times in this forum and also on the Linux Questions forum, but got no response.  After looking through all the related (but not exactly the same) problems, and trying a number of things posted there, I have found a solution.  This may or may not work on your machine, but it did on mine.

In the terminal type in 'sudu gedit /boot/grub/menu.lst  (where the "l" in .lst is a small L.  Then scan down the list until you find the lines that begin with kernel.  On my machine the line looked like:

kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=d1506f7b-b5d3-4eec-bef0-226f8233f27f ro quiet splash 

Then add to the end of that line: acpi=force pci=noacpi

so the line will look like this:

kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=d1506f7b-b5d3-4eec-bef0-226f8233f27f ro quiet splash acpi=force pci=noacpi

After I did that, my machine now shuts down normally.  I hope it works for you too.

---

### Post by Baasha on 2007-12-01
Well, I take the previous post back, it doesn't work.  i had a couple of successful shutdowns and now the problem is back.  Aren't there any Ubuntu gurus out there who have at least a clue what might be happening?

---

### Post by Baasha on 2007-12-02
I think I may have found another answer.  My Gutsy came with the Network Manager applet installed and Network Manager enabled.  When I disabled nm the system shutdown normally, at least the first time I tried it.  I will report back if I continue to have problems.

---

