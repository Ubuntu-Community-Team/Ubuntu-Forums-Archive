---
title: "Windows vista will not boot"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Flavkupe on 2008-05-06
Hi all. 

I haven't dual-booted OSes on a laptop before so I'm running into some issues with this. 

I saw some similar posts about this issue but I think mine is a bit different. My Ubuntu installation was not successful (I think I have a hardware problem), but I can boot Ubuntu from the boot prompt; I get a desktop with 3 items: a folder called examples, an executable called install, and a DVD-rom icon. When I attempted to install, however, I got an error when attempting to partition. 

Now, when trying to run Vista again, I get this error: 

autochk program not found - skipping AUTOCHECK

Then I get a bluescreen and the system restarts, ad infinitum. I tried using the Vista repair CD and it doesn't work. Selecting the option to repair Vista rather than running it normally just sends me back to the boot prompt where it asks if I want to run Vista or Ubuntu. The only thing I can do is go into the limited (I think) Ubuntu I have. 

I did some searching online and it seems the Vista error is due to the windows partition being "hidden" or something. They offered several solutions that require using Partition Magic or other tools, but this laptop (not the one with the problems) can't burn CDs so I can't rely on that. I'm wondering if there is a way to solve this problem from Ubuntu, probably from the terminal or the Partition Editor. I tried going to the /boot directory from the terminal, running grub and typing "unhide (hd0,0)", which some post suggested, but that didn't work. 

Any help would be VERY well appreciated.

Sorry for the verbosity

Flav

---

### Post by Pumalite on 2008-05-06
Try to restore the Vista MBR with Super Grub:[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Next time use Vista partitioner. You cannot partition with Ubuntu CD.

---

### Post by Flavkupe on 2008-05-07
I solved this problem. It was not really a trivial solution (in which it wasn't obvious what I had to do). If someone needs details on how to solve it let me know - [email]flavkupe@umich.edu[/email]

Flav

---

