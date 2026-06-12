---
title: "[SOLVED] Upgraded some hardware, now partition can't be found"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by subnet_rx on 2007-12-14
I just upgraded from 1GB of memory to 2GB (added 2 sticks) and upgraded my sound card.  When I started my computer back up, Grub now says that my drive cannot be found when I select Windows.  It will let me go into Linux, which is on a different partition, but the same hard drive.  Any ideas?

---

### Post by Herman on 2007-12-15
Installing more RAM and a sound card shouldn't hurt and should do a lot of good in your computer. 
Are you sure you didn't need to unplug some cables in order to reach in where you had to and maybe plugged them in again a little differently? Probably not, but just check again to make sure. 

What is the exact error message?
'Operating system not found' is not a GRUB error message, it might be from your BIOS instead, or even from Windows.
(Windows is famous for crazy error messages like 'keyboard not found, press any key to reboot', and the like ! :lolflag:)

Here's a thought, [Operating system not found]("http://www.pcguide.com/ts/x/sys/booterrGBER44-c.html") --> [Troubleshoot     this here]("http://www.pcguide.com/ts/x/comp/hdd/file_BadCorruption.htm")--> [Check for resource conflicts]("http://www.pcguide.com/ts/x/comp/mbsys/sys_ResourceConflict.htm"). "These can     cause problems with the hard disk."

Try going into your BIOS and taking a look around in there to see if everything looks normal. 

Were there any instructions with your new sound card about any BIOS settings you might need to make?

Try temporarily removing the sound card and test it to see if it will boot okay. and try putting the sound card back in but remove the new RAM and try again to see what happens. 

Quoted from the PC Guide:
> Watch out for conflicts between built-in IDE controllers and add-in controllers. If you are using an add-in controller, for example for enhanced BIOS translation support, then you need to make sure you disable the built-in controller so that there is no conflict. Watch out for sound cards that have IDE controllers built in to them--this is quite common. Make sure the controller is not enabled unless you are using it.

Regards, Herman :)

---

### Post by subnet_rx on 2007-12-17
It took me a while, but I finally figured out that I had unplugged the power from my primary drive.  It took me so long because I was sure that Linux was on my primary drive, when it looks like it is on my secondary storage drive.

---

