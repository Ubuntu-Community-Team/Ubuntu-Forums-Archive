---
title: "Boot loader installation failed on Mac Mini 1,1"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by xnera on 2012-10-12
Hello,

I have a Mac Mini 1,1.  I am trying to install Ubuntu on an external HD, an old Western Digital 80GB I had laying around. The installation went well, except that it failed when trying to install the boot loader.

I have yet to install rEFIt on my Mac, but I did try booting with a rEFIt CD - as I expected, the drive wasn't detected.

I followed the advice at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to scan the system.  Here's the results:

[http://paste.ubuntu.com/1275822/](http://paste.ubuntu.com/1275822/)

I have yet to try clicking recommended repair. I'm a bit leery of doing so without knowing exactly what it'd be doing during the repair.  Too scared of it messing up my Mac, since I don't have a full backup of it (my Mac is still running Tiger, so Time Machine is out of the question.  I have another external drive that I can back up documents to, but I'm unsure of how to backup the OS to it.)

Based on the pastebin, do you think it would be safe to try the recommended repair, or should I try re-installing, maybe with a different partition setup?

Thanks in advance for your advice and help!

---

### Post by xnera on 2012-10-14
Update: I decided to go ahead and re-install, this time letting Ubuntu partition the drive itself.  No errors with installation.  I rebooted using my burned rEFIt CD, and the Ubuntu drive showed up and booted no problem.  Works beautifully!

A tip for those trying to use Live CDs on a Mac mini: for some reason the 12.04 CDs didn't want to boot for me at first.  It's possible I just didn't wait long enough.... but, it seemed to work after I had completely **shutdown** the system and powered it back on, rather than just choosing Restart from within OSX.  Just thought I'd toss that out there in case others experience problems.

---

