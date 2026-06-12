---
title: "Will not boot"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by shane3 on 2008-09-01
I'm new to ubuntu and have been trying to install Desktop on my machine all weekend.  The deal is I can run ubuntu from CD to test it out in Safe Graphics Mode only with the 'Live' installer.  I can then install it and when prompted to reboot it hangs with a black screen with 'Starting up ...'.  I ditched the Live installer and tried the alternate installation with the same results.  I've already posted once with no replies.  I've dug deep into the forums to no avail.  

At this point I have no other choice but to put Windows back on it unless someone out there can provided some insight. I believe it has something to do with my graphics card (S3), but without the proper support I have no more ways to troubleshoot.

---

### Post by xen-uno on 2008-09-01
Video has to be the #1 installation hassle with Ubuntu. Do you have an NVidia card you can stick in it? Throw up your computer specs ...

---

### Post by shane3 on 2008-09-01
Thanks for the quick response.  I've got a 1GHZ AMD with 256MB memory, and an S3 Trio64V+ video card.  I unfortunately don't have another card to test with.  Is the best thing to get a new NVidia?

---

### Post by xen-uno on 2008-09-01
I don't want to steer you wrong cuz it may not be video, but ... an NVidia card and the alternate install is the way to go IMO. What type of vid card bus? (PCIe, PCI, AGP, VESA, ISA)

---

### Post by shane3 on 2008-09-01
It's a PCI card.

---

### Post by xen-uno on 2008-09-01
Can you stay in Safe or low resolution mode (aka VGA) after the reboot? Are you ever prompted or is it an immediate lockup? I have a feeling that the install went OK but on reboot it wants to use the higher graphic modes which causes the lockup. I had that with 7.10 Live and my 8800 NVidia which I got around using the Alternative CD.

edit: when it hangs at starting up, is there any disk activity? How long do you wait before saying "up yours!" then aborting?

---

### Post by shane3 on 2008-09-01
I wish I knew how to stay in Safe Mode when rebooting. Is this possible?

The boot sequence is very limited.  It goes through the basic BIOS stuff, then says it's loading up grub, pauses a few seconds with a blank screen, then it hangs up after displaying 'Starting up'.  There is absolutely no disk activity at this point, and I've waited up to an hour for it to boot.    

You're on the $ that the reboot wants higher resolution than what it was installed with.  How did you get around this with the Alternate install?  I did the alternate and thought I would have some options to configure the graphics card.  Maybe this step timed out and I wasn't at my PC (the install took a while).  

I've also tried to edit some boot parameters in grub, for instance setting vga=771 (800x600).  However, the OS doesn't like the param and offers some other ones that don't look like resolution to me (ie 80x25).  

I know the dang card works at higher resolutions (1024) b\c it works with Windows.

---

