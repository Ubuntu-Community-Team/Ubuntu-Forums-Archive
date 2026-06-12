---
title: "Apparently good install, but major system 'lag'?"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Brad on 2005-02-02
Hi guys

I recently installed Ubuntu from the CD free with the Jan issue of Linux Format. Everything seemed to go absolutely fine.
I didn't have network access at the time so I skipped the update option during installation but have since checked for the most up to date versions of everything installed with Synaptic Package Manager without issue.


The one problem I do have (unfortunately making the system pretty much unusable) is that I seem to get serious lag during certain operations.

For example when booting up everything is fine until I log in and the 'splash screen' (with 'Ubuntu' and the logo in the centre of the screen) appears. That's all I get for the next 5-10 minutes.
Then I get the desktop. Checking activity monitor shows the CPU (XP1700+) has a low percentage of use but when I try and launch an application/utility there's about 30s - 1minutes lag. Then the app seems to run OK (eg I'm typing this in FireFox and have been browsing with no headaches) until I go to close it and again with the lag.

Same deal when I shut the system down, unbearable lag, as if the system is spinning it's wheels trying to catch up.

The gfx card is an old Riva TNT2 16MB and seems to be running a little hot.

I've been doing a little searching/reading but haven't found anyone who's experienced (and solved) this problem yet, so if someone could point me in the right direction that would be grand.
Forgive a newbie, but Ubuntu was to be my Linux learning experience. All I seem to have managed so far is to stove headlong into a steep learning curve.

---

### Post by trivialpackets on 2005-02-03
Probably unrelated, but I had similar experiences after updating the kernel.  I inserted a noapic command into my grub loader as I had needed to install properly prior to the upgrade to kernel, and it completely cleared up the lag that i was having.  the noapic from what I gather has somethign to do with the initiation of the system clock, but it cleared up my laggy system just fine.  Hope this helps.  I'd try installing the command during boot, just hit 'e' , then goto line 2, hit 'e' again and add the noapic.  It only will change for this running.  If it helps, it can be added into the grub loader, if not, no harm no foul.  Good luck.

---

### Post by Brad on 2005-02-03
[QUOTE=eric.proctor]Probably unrelated...[/QUOTE]

Not at all, that seems to have completely solved the problem!

In all honestly I don't really know what 'noapic' is, but seeing as this is my 'Linux learner' install I'll certainly be looking into this further now I have a solid lead.

Thanks Eric, great advice  =D> 



P.S. any other novices may want to know you'll need to press esc to bring up the menu, then follow Eric's instructions.

---

### Post by trivialpackets on 2005-02-03
No problem, it's nice to have helped someone.  In any case, the esc isn't needed for me.  But go gedit your /boot/grub/menu.lst and I'd change the settings to allow more than 5 seconds.  Esc probably isn't needed for me as I'm dual booting with XP?  I don't know if that's the difference.  In any case, you can allow for the noapic to be added without having to type it in each time as well as increasing the time.  Bear in mind the noapic will need to be adjusted if you upgrade the kernel.  Good luck, hope I can help again.

---

